---
title: 'Improving Go code: An introduction to the static analysis tool Staticcheck'
date: 2019-11-11T06:11:00+01:00
draft: false
---

![](https://superhighway.dev/images/w_1280,e_sharpen:60/odl8suayxjlxh8xngmc3.jpg "Staticcheck in Action")  

Too often we discover subtle bugs only after deploying to production. Even in a language like Go it's possible to write ineffectual code and not catch bugs until it's too late.

[Staticcheck](https://staticcheck.io/) is a static analysis tool for Go code. It has various checks, such as a check for unused variables, a check for deferring the Lock method on a mutex right after locking (the user probably meant to defer Unlock instead), a check for unreachable code, and more.

In this post we'll show sample code for which staticcheck returns errors, and how to fix the affected code.

Value is never used (SA4006)
----------------------------

I always double check these errors as they can cause some serious bugs. Here's one example:

```
package main import ( "errors" "fmt" "log" ) type Result struct { Entries []string } func Query() (Result, error) { return Result{ Entries: []string{}, }, nil } func ResultEntries() (Result, error) { err := errors.New("no entries found") result, err := Query() if err != nil { return Result{}, err } if len(result.Entries) == 0 { return Result{}, err } return result, nil } func main() { result, err := ResultEntries() if err != nil { log.Fatal(err) } fmt.Printf("result=%v, err=%v", result, err) }
```

When running staticcheck on this code, we see the following errors:

```
$ staticcheck main.go main.go:20:2: this value of err is never used (SA4006) main.go:20:19: New is a pure function but its return value is ignored (SA4017)
```

We're going to ignore the second error as it's a side effect of the first.

If we run the code, we see:

```
$ go run main.go result={[]}, err=
```

Let's investigate:

We have two functions, `Query()` and `ResultEntries()`. The `Query` function returns an empty set of entries for the purpose of this example. The `ResultEntries()` function declares an error at the top, `err := errors.New("no entries found")`, and then calls `Query()` right below that to get the result.

This call to `Query`, however, overwrites the `err` variable to when the error returned is nil. So when we check the length of `result.Entries` and find that it's `0`, we return `Result{}, err` but the `err` we're returning is not the `err` we declared at the top of the function, but rather the error which was returned by `Query()`.

This example is quite harmless but one can imagine how similar code might lead to a more serious bug.

So how do we fix it?

The method you choose to fix this will depend on your preferred style. Here is one way:

```
func ResultEntries() (Result, error) { result, err := Query() if err != nil { return Result{}, err } err = errors.New("no entries found") if len(result.Entries) == 0 { return Result{}, err } return result, nil }
```

Here we reassign the `err` variable before checking the length of `result.Entries`. This will now return the correct error:

```
$ go run main.go 2019/09/18 19:03:40 no entries found exit status 1
```

and staticcheck no longer complains:

```
$ staticcheck main.go $
```

Another way would be:

```
func ResultEntries() (Result, error) { result, err := Query() if err != nil { return Result{}, err } if len(result.Entries) == 0 { return Result{}, errors.New("no entries found") } return result, nil }
```

Calling `regexp.MatchString` in a loop has poor performance (SA6000)
--------------------------------------------------------------------

If staticcheck finds this issue in your code, you can fix it for better performance. Here's an example (note: this is not an extensive regular expression for matching emails):

```
package main import ( "fmt" "log" "regexp" ) func ValidateEmails(addrs []string) (bool, error) { for _, email := range addrs { matched, err := regexp.MatchString("^[a-zA-Z0-9.]+@[a-zA-Z0-9]+\\.[a-zA-Z0-9]*$", email) if err != nil { return false, err } if !matched { return false, nil } } return true, nil } func main() { emails := []string{"testuser@gmail.com", "anotheruser@yahoo.com", "onemoreuser@hotmail.com"} matched, err := ValidateEmails(emails) if err != nil { log.Fatal(err) } fmt.Println(matched) }
```

In this example we pass a slice of email addresses to a validation function that matches them with a regular expression. Staticcheck finds the following issue:

```
$ staticcheck main.go main.go:11:37: calling regexp.MatchString in a loop has poor performance, consider using regexp.Compile (SA6000)
```

Let's fix it and then look at some benchmarks.

To fix the issue we'll compile the regular expression at the beginning of the function instead of recreating it in the loop every iteration:

```
func ValidateEmails(addrs []string) (bool, error) { re := regexp.MustCompile(`^[a-zA-Z0-9.]+@[a-zA-Z0-9]+\.[a-zA-Z0-9]*$`) for _, email := range addrs { matched := re.MatchString(email) if !matched { return false, nil } } return true, nil }
```

The method `regexp.MustCompile` creates a reusable regular expression struct and panics if it can't be compiled. You may have noticed that the string changed slightly, but we'll ignore that for the purposes of this post it's not relevant to the overall fix. If we run staticcheck on this new code, we see no errors:

```
$ staticcheck main.go $
```

The code runs and returns `true`:

```
$ go run main.go true
```

Now let's write a benchmark to compare these two methods. We'll call the original method `ValidateEmailsRegexpLoop`, and keep the current implementation called `ValidateEmails`:

```
package main import "testing" func BenchmarkValidateEmailsRegexpLoop(b *testing.B) { emails := []string{"testuser@gmail.com", "anotheruser@yahoo.com", "onemoreuser@hotmail.com"} for i := 0; i < b.N; i++ { _, err := ValidateEmailsRegexpLoop(emails) if err != nil { b.Fatal(err) } } } func BenchmarkValidateEmails(b *testing.B) { emails := []string{"testuser@gmail.com", "anotheruser@yahoo.com", "onemoreuser@hotmail.com"} for i := 0; i < b.N; i++ { _, err := ValidateEmails(emails) if err != nil { b.Fatal(err) } } }
```

Let's run this benchmark:

```
$ go test -bench=. goos: darwin goarch: amd64 BenchmarkValidateEmailsRegexpLoop-4 100000 21150 ns/op BenchmarkValidateEmails-4 200000 8108 ns/op PASS ok _/Users/gopher 4.045s
```

There is a significant performance improvement by declaring the regular expression once outside of the loop. Thanks staticcheck!

Running Staticcheck on popular open source codebases
----------------------------------------------------

As the co-creator of [Go Report Card](https://goreportcard.com), I'm passionate about open source code quality. Let's take a look at staticcheck results for some popular open source repositories.

### aws/aws-sdk-go

[github.com/aws/aws-sdk-go](https://github.com/aws/aws-sdk-go) is the official AWS SDK for Go. To install it, run:

```
$ go get github.com/aws/aws-sdk-go
```

and then:

```
$ cd $GOPATH/src/github.com/aws/aws-sdk-go
```

Staticcheck takes a long time to run on the entire codebase, so let's run it on a single directory and its sub-directories:

```
$ aws-sdk-go git:(master) staticcheck ./aws/...
```

There are many results. The one in particular we'll take a look at is:

```
aws/request/request_retry_test.go:133:2: unreachable case clause: github.com/aws/aws-sdk-go/aws/request.temporary will always match before *net/url.Error (SA4020)
```

Here is the function:

```
func debugerr(t *testing.T, err error) { t.Logf("Error, %v", err) switch err := err.(type) { case temporary: t.Logf("%s is a temporary error: %t", err, err.Temporary()) return case *url.Error: t.Logf("err: %s, nested err: %#v", err, err.Err) if operr, ok := err.Err.(*net.OpError); ok { t.Logf("operr: %#v", operr) } debugerr(t, err.Err) return default: return } }
```

We need to take a look at the `temporary` type definition as well as `url.Error` to see what's going on. The `temporary` type is located in `aws/request/retryer.go`:

```
type temporary interface { Temporary() bool }
```

and in the stdlib `net/url` package we'll find a concrete type `Error` that implements a `Temporary()` method (along with some others). In other words, `url.Error` implements the `temporary` interface.

To break it down, let's imagine that we do pass a `url.Error` to the `debugerr` function. We go into the type switch and ask, "is this value's type `temporary`?" The answer is "yes" because `url.Error` implements the `Temporary()` method, the only method in the `temporary` interface. Thus we enter that case and return -- and we never get to `case *url.Error`.

This can be fixed by swapping the case statements:

```
func debugerr(t *testing.T, err error) { t.Logf("Error, %v", err) switch err := err.(type) { case *url.Error: t.Logf("err: %s, nested err: %#v", err, err.Err) if operr, ok := err.Err.(*net.OpError); ok { t.Logf("operr: %#v", operr) } debugerr(t, err.Err) return case temporary: t.Logf("%s is a temporary error: %t", err, err.Temporary()) return default: return } }
```

Now, if we pass a `url.Error` to this function, it will match in the first case statement.

Staticcheck also finds other issues that could be fixed in small PRs. Here are a few that stood out to me:

```
service/s3/host_style_bucket.go:70:2: var accelElem is unused (U1000) service/glacier/treehash.go:58:5: should omit nil check; len() for nil slices is defined as zero (S1009) service/s3/s3manager/upload.go:366:2: field bufferUploadPool is unused (U1000)
```

### Kubernetes

Staticcheck found many issues in Kubernetes. Let's take a look at some of them:

First, we'll get the source:

```
go get k8s.io/kubernetes
```

Kubernetes is quite a large codebase, so this time we'll just focus on one package, `pkg/volume`:

```
staticcheck ./pkg/volume/...
```

There are many results, but we'll focus on one of them for now:

```
pkg/volume/azure_file/azure_file.go:122:31: this value of err is never used (SA4006)
```

If we take a look at that code, we see the following function:

```
func (plugin *azureFilePlugin) newMounterInternal(spec *volume.Spec, pod *v1.Pod, util azureUtil, mounter mount.Interface) (volume.Mounter, error) { share, readOnly, err := getVolumeSource(spec) if err != nil { return nil, err } secretName, secretNamespace, err := getSecretNameAndNamespace(spec, pod.Namespace) return &azureFileMounter{ azureFile: &azureFile{ volName: spec.Name(), mounter: mounter, pod: pod, plugin: plugin, MetricsProvider: volume.NewMetricsStatFS(getPath(pod.UID, spec.Name(), plugin.host)), }, util: util, secretNamespace: secretNamespace, secretName: secretName, shareName: share, readOnly: readOnly, mountOptions: volutil.MountOptionFromSpec(spec), }, nil }
```

We can see that the error returned by the `getSecretNameAndNamespace` function is ignored. We should add an error check:

```
func (plugin *azureFilePlugin) newMounterInternal(spec *volume.Spec, pod *v1.Pod, util azureUtil, mounter mount.Interface) (volume.Mounter, error) { share, readOnly, err := getVolumeSource(spec) if err != nil { return nil, err } secretName, secretNamespace, err := getSecretNameAndNamespace(spec, pod.Namespace) if err != nil { return nil, err } return &azureFileMounter{ azureFile: &azureFile{ volName: spec.Name(), mounter: mounter, pod: pod, plugin: plugin, MetricsProvider: volume.NewMetricsStatFS(getPath(pod.UID, spec.Name(), plugin.host)), }, util: util, secretNamespace: secretNamespace, secretName: secretName, shareName: share, readOnly: readOnly, mountOptions: volutil.MountOptionFromSpec(spec), }, nil }
```

### The Go source tree

That's right, staticcheck even found some bugs in the Go source itself!

To be fair, it didn't find anything egregious, but I didn't run it on every package so it's possible there are some more bugs hiding elsewhere.

We'll take a look at another unused error variable in a file called `database/sql/sql_test.go`. The test is `TestTxEndBadConn`:

```
dbQuery := func(endTx func(tx *Tx) error) func() error { return func() error { tx, err := db.Begin() if err != nil { return err } rows, err := tx.Query("SELECT|t1|age,name|") if err == nil { err = rows.Close() } else { return err } return endTx(tx) } }
```

Staticcheck tells us the following:

```
database/sql/sql_test.go:2888:5: this value of err is never used (SA4006)
```

This refers to the line `err = rows.Close()`. We can fix it by checking the error:

```
dbQuery := func(endTx func(tx *Tx) error) func() error { return func() error { tx, err := db.Begin() if err != nil { return err } rows, err := tx.Query("SELECT|t1|age,name|") if err == nil { err = rows.Close() if err != nil { return err } } else { return err } return endTx(tx) } }
```

Or perhaps this is more idiomatic:

```
dbQuery := func(endTx func(tx *Tx) error) func() error { return func() error { tx, err := db.Begin() if err != nil { return err } rows, err := tx.Query("SELECT|t1|age,name|") if err != nil { return err } err = rows.Close() if err != nil { return err } return endTx(tx) } }
```

There are other functions in the same test file that call `rows.Close()` without checking the error, so maybe that is fine too.

If you've been wanting to make a contribution to the Go source code, this could be your chance.

Conclusion
----------

Hopefully you've found this introduction to one of my favorite tools, [staticcheck](https://staticcheck.io/), useful. Please try it out on your own code and see what it finds!

* * *

* * *

  
  
from Hacker News https://ift.tt/36OqlIQ