---
title: 'Self_update: In-place updates for Rust executables'
date: 2020-01-30T01:34:00+01:00
draft: false
---

[](https://github.com/jaemk/self_update#self_update)self\_update
================================================================

[![Build status](https://camo.githubusercontent.com/321424b559876103d7df0ef0284cb0e567fc5957/68747470733a2f2f63692e6170707665796f722e636f6d2f6170692f70726f6a656374732f7374617475732f786c6b713872643733636c61346978772f6272616e63682f6d61737465723f7376673d74727565)](https://ci.appveyor.com/project/jaemk/self-update/branch/master) [![Build Status](https://camo.githubusercontent.com/41365f5b8e40f45eb3602e94fd03a4cc86e8377e/68747470733a2f2f7472617669732d63692e6f72672f6a61656d6b2f73656c665f7570646174652e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/jaemk/self_update) [![crates.io:clin](https://camo.githubusercontent.com/179cc5a2d5fda5a9847aeae98a26f10d8f04f83d/68747470733a2f2f696d672e736869656c64732e696f2f6372617465732f762f73656c665f7570646174652e7376673f6c6162656c3d73656c665f757064617465)](https://crates.io/crates/self_update) [![docs](https://camo.githubusercontent.com/665f305ecf212a32ce22228ee06f7f5a4ecbe83b/68747470733a2f2f646f63732e72732f73656c665f7570646174652f62616467652e737667)](https://docs.rs/self_update)

`self_update` provides updaters for updating rust executables in-place from various release distribution backends.

[](https://github.com/jaemk/self_update#usage)Usage
---------------------------------------------------

Update (replace) the current executable with the latest release downloaded from `https://api.github.com/repos/jaemk/self_update/releases/latest`. Note, the [`trust`](https://github.com/japaric/trust) project provides a nice setup for producing release-builds via CI (travis/appveyor).

```
#\[macro\_use\] extern crate self\_update; fn update() -> Result<(), Box<::std::error::Error>> { let status \= self\_update::backends::github::Update::configure() .repo\_owner("jaemk") .repo\_name("self\_update") .bin\_name("self\_update\_example") .show\_download\_progress(true) .current\_version(cargo\_crate\_version!()) .build()? .update()?; println!("Update status: \`{}\`!", status.version()); Ok(()) }
```

Run the above example to see `self_update` in action: `cargo run --example github`

Amazon S3 is also supported as the backend to check for new releases. Provided a `bucket_name` and `asset_prefix` string, `self_update` will look up all matching files using the following format as a convention for the filenames: `--.`. Any file not matching the format, or not matching the provided prefix string, is be ignored.

```
fn update() -> Result<(), Box<::std::error::Error>> { let status = self_update::backends::s3::Update::configure() .bucket_owner("self_update_releases") .asset_prefix("self_update") .region("eu-west-2") .bin_name("self_update_example") .show_download_progress(true) .current_version(cargo_crate_version!()) .build()? .update()?; println!("S3 Update status: `{}`!", status.version()); Ok(()) } # fn main() { } 
```

Separate utilities are also exposed:

```
extern crate self\_update; fn update() -> Result<(), Box<::std::error::Error>> { let releases \= self\_update::backends::github::ReleaseList::configure() .repo\_owner("jaemk") .repo\_name("self\_update") .build()? .fetch()?; println!("found releases:"); println!("{:#?}\\n", releases); // get the first available release let asset \= releases\[0\] .asset\_for(&self\_update::get\_target()).unwrap(); let tmp\_dir \= self\_update::TempDir::new\_in(::std::env::current\_dir()?, "self\_update")?; let tmp\_tarball\_path \= tmp\_dir.path().join(&asset.name); let tmp\_tarball \= ::std::fs::File::open(&tmp\_tarball\_path)?; self\_update::Download::from\_url(&asset.download\_url) .download\_to(&tmp\_tarball)?; let bin\_name \= std::path::PathBuf::from("self\_update\_bin"); self\_update::Extract::from\_source(&tmp\_tarball\_path) .archive(self\_update::ArchiveKind::Tar(Some(self\_update::Compression::Gz))) .extract\_file(&tmp\_dir.path(), &bin\_name)?; let tmp\_file \= tmp\_dir.path().join("replacement\_tmp"); let bin\_path \= tmp\_dir.path().join(bin\_name); self\_update::Move::from\_source(&bin\_path) .replace\_using\_temp(&tmp\_file) .to\_dest(&::std::env::current\_exe()?)?; Ok(()) }
```

License: MIT

  
  
from Hacker News https://ift.tt/2RDO88M