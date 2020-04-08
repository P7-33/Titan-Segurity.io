---
title: 'Gosec - Golang Security Checker'
date: 2019-11-11T00:28:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-QeJn3Uml4_E/XbS1AIhK9wI/AAAAAAAAQto/6PnMWrj6GJoPNHcE20JSJV3jX6T92TREQCNcBGAsYHQ/s400/gosec_1.png)](https://1.bp.blogspot.com/-QeJn3Uml4_E/XbS1AIhK9wI/AAAAAAAAQto/6PnMWrj6GJoPNHcE20JSJV3jX6T92TREQCNcBGAsYHQ/s1600/gosec_1.png)

**Gosec - Golang Security Checker**

  

  
Inspects source code for security problems by scanning the Go AST.  
  
**Install**  
  
**CI Installation**

```
# binary will be $GOPATH/bin/gosec  
curl -sfL [https://raw.githubusercontent.com/securego/gosec/master/install.sh](https://raw.githubusercontent.com/securego/gosec/master/install.sh) | sh -s -- -b $GOPATH/bin vX.Y.Z  
  
# or install it into ./bin/  
curl -sfL [https://raw.githubusercontent.com/securego/gosec/master/install.sh](https://raw.githubusercontent.com/securego/gosec/master/install.sh) | sh -s vX.Y.Z  
  
# In alpine linux (as it does not come with curl by default)  
wget -O - -q [https://raw.githubusercontent.com/securego/gosec/master/install.sh](https://raw.githubusercontent.com/securego/gosec/master/install.sh) | sh -s vX.Y.Z  
  
# If you want to use the checksums provided on the "Releases" page  
# then you will have to download a tar.gz file for your operating system instead of a binary file  
wget [https://github.com/securego/gosec/releases/download/vX.Y.Z/gosec_vX.Y.Z_OS.tar.gz](https://github.com/securego/gosec/releases/download/vX.Y.Z/gosec_vX.Y.Z_OS.tar.gz)  
  
# The file will be in the current folder where you run the command   
# and you can check the checksum like this  
echo " gosec_vX.Y.Z_OS.tar.gz" | sha256sum -c -  
  
gosec --help
```

  
**Local Installation**

```
go get [github.com/securego/gosec/cmd/gosec](http://github.com/securego/gosec/cmd/gosec)
```

  
**Usage**  
Gosec can be configured to only run a subset of rules, to exclude certain file paths, and produce reports in different formats. By default all rules will be run against the supplied input files. To recursively scan from the current directory you can supply './...' as the input argument.

[](https://www.blogger.com/u/1/null)  
**Available rules**

*   G101: Look for hard coded credentials
*   G102: Bind to all interfaces
*   G103: Audit the use of unsafe block
*   G104: Audit errors not checked
*   G106: Audit the use of ssh.InsecureIgnoreHostKey
*   G107: Url provided to HTTP request as taint input
*   G108: Profiling endpoint automatically exposed on /debug/pprof
*   G201: SQL query construction using format string
*   G202: SQL query construction using string concatenation
*   G203: Use of unescaped data in HTML templates
*   G204: Audit use of command execution
*   G301: Poor file permissions used when creating a directory
*   G302: Poor file permissions used with chmod
*   G303: Creating tempfile using a predictable path
*   G304: File path provided as taint input
*   G305: File traversal when extracting zip archive
*   G401: Detect the usage of DES, RC4, MD5 or SHA1
*   G402: Look for bad TLS connection settings
*   G403: Ensure minimum RSA key length of 2048 bits
*   G404: Insecure random number source (rand)
*   G501: Import blacklist: crypto/md5
*   G502: Import blacklist: crypto/des
*   G503: Import blacklist: crypto/rc4
*   G504: Import blacklist: net/http/cgi
*   G505: Import blacklist: crypto/sha1

  
**Retired rules**

*   G105: Audit the use of math/big.Int.Exp - [CVE is fixed](https://github.com/golang/go/issues/15184 "CVE is fixed")

  
**Selecting rules**  
By default gosec will run all rules against the supplied file paths. It is however possible to select a subset of rules to run via the '-include=' flag, or to specify a set of rules to explicitly exclude using the '-exclude=' flag.

```
# Run a specific set of rules  
$ gosec -include=G101,G203,G401 ./...  
  
# Run everything except for rule G303  
$ gosec -exclude=G303 ./...
```

  
**Configuration**  
A number of global settings can be provided in a configuration file as follows:

```
{  
    "global": {  
        "nosec": "enabled",  
        "audit": "enabled"  
    }  
}
```

*   `nosec`: this setting will overwrite all `#nosec` directives defined throughout the code base
*   `audit`: runs in audit mode which enables addition checks that for normal [code analysis](https://www.kitploit.com/search/label/Code%20Analysis "code analysis") might be too nosy

```
# Run with a global configuration file  
$ gosec -conf config.json .
```

Also some rules accept configuration. For instance on rule `G104`, it is possible to define packages along with a list of functions which will be skipped when auditing the not checked errors:

```
{  
    "G104": {  
        "io/ioutil": ["WriteFile"]  
    }  
}
```

  
**Dependencies**  
gosec will fetch automatically the dependencies of the code which is being analyzed when go modules are turned on (e.g.`GO111MODULE=on`). If this is not the case, the dependencies need to be explicitly downloaded by running the `go get -d` command before the scan.  
  
**Excluding test files and folders**  
gosec will ignore test files across all packages and any dependencies in your vendor directory.  
The scanning of test files can be enabled with the following flag:

```
gosec -tests ./...
```

Also additional folders can be excluded as follows:

```
 gosec -exclude-dir=rules -exclude-dir=cmd ./...
```

  
**Annotating code**  
As with all automated detection tools there will be cases of false positives. In cases where gosec reports a failure that has been manually verified as being safe it is possible to annotate the code with a '#nosec' comment.  
The annotation causes gosec to stop processing any further nodes within the AST so can apply to a whole block or more granularly to a single expression.

  

```
import "md5" // #nosec  
  
  
func main(){  
  
    /* #nosec */  
    if x > y {  
        h := md5.New() // this will also be ignored  
    }  
  
}
```

When a specific false positive has been identified and verified as safe, you may wish to suppress only that single rule (or a specific set of rules) within a section of code, while continuing to scan for other problems. To do this, you can list the rule(s) to be suppressed within the `#nosec` annotation, e.g: `/* #nosec G401 */` or `// #nosec G201 G202 G203 `  
In some cases you may also want to revisit places where #nosec annotations have been used. To run the scanner and ignore any #nosec annotations you can do the following:

```
gosec -nosec=true ./...
```

  
**Build tags**  
gosec is able to pass your [Go build tags](https://golang.org/pkg/go/build/ "Go build tags") to the analyzer. They can be provided as a comma separated list as follows:

```
gosec -tag debug,ignore ./...
```

  
**Output formats**  
gosec currently supports text, json, yaml, csv, [sonarqube](https://www.kitploit.com/search/label/SonarQube "sonarqube") and JUnit XML output formats. By default results will be reported to stdout, but can also be written to an output file. The output format is controlled by the '-fmt' flag, and the output file is controlled by the '-out' flag as follows:

```
# Write output in json format to results.json  
$ gosec -fmt=json -out=results.json *.go
```

  
**Development**  
  
**Build**

```
make
```

  
**Tests**

```
make test
```

  
**Release Build**  
Make sure you have installed the [goreleaser](https://github.com/goreleaser/goreleaser "goreleaser") tool and then you can release gosec as follows:

```
git tag v1.0.0  
export GITHUB_TOKEN=  
make release
```

The released version of the tool is available in the `dist` folder. The build information should be displayed in the usage text.

```
./dist/darwin_amd64/gosec -h  
gosec  - Golang security checker  
  
gosec analyzes Go source code to look for common programming mistakes that  
can lead to security problems.  
  
VERSION: 1.0.0  
GIT TAG: v1.0.0  
BUILD DATE: 2018-04-27T12:41:38Z
```

Note that all released archives are also uploaded to GitHub.  
  
**Docker image**  
You can build the docker image as follows:

```
make image
```

You can run the `gosec` tool in a [container](https://www.kitploit.com/search/label/Container "container") against your local Go project. You just have to mount the project into a volume as follow:

```
docker run -it -v /:/ securego/gosec //...
```

  
**Generate TLS rule**  
The configuration of TLS rule can be generated from [Mozilla's TLS ciphers recommendation](https://statics.tls.security.mozilla.org/server-side-tls-conf.json "Mozilla's TLS ciphers recommendation").  
First you need to install the [generator](https://www.kitploit.com/search/label/Generator "generator") tool:

```
go get [github.com/securego/gosec/cmd/tlsconfig/](http://github.com/securego/gosec/cmd/tlsconfig/)...
```

You can invoke now the `go generate` in the root of the project:

```
go generate ./...
```

This will generate the `rules/tls_config.go` file with will contain the current ciphers recommendation from Mozilla.  
  

**[Download Gosec](http://eunsetee.com/idfi "Download Gosec")**

**  
Regards**

**Kang Asu**