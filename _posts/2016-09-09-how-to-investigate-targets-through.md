---
title: 'How To Investigate Targets through Sn0int OSINT Framework'
date: 2019-12-27T23:27:00+01:00
draft: false
---

  

===

  

Sn0int is a semi-automatic open-source intelligence _(osint) _project. The framework collects publically available information followed by data processing and mapping. The framework has a lot of interesting _osint_ features. Some of these features include:

*   Human profiling across the internet
*   Phone numbers information collection
*   Image scanning
*   Instagram data and images collection
*   Discovering compromised logins in breaches
*   Bypassing Cloudflare via shodan
*   Email collection from PGP servers and WHOIS record
*   Domains IP and GEOIP address collection
*   Harvesting subdomains through Passive DNS and certificate transparency logs
*   Local networks enumeration

Sn0int has a default set of modules to perform the aforementioned tasks. The framework gives the freedom of writing and integrating our own modules. Penetration testers can even publish their modules to make them available for other Sn0int users.

Sn0int Installation

Sn0int depends on Rust (programming) and few other packages.  Rust can be installed by typing the following command in the terminal.

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

![rust-installation](https://www.hackingloops.com/wp-content/uploads/2019/11/rust-installation.png)

The above command automatically installs cargo –the package manager for Rust. Cargo is responsible for downloading Rust package’s dependencies, package compiling and making distributable packages. After installing Rust, restart your system. Otherwise, you might get command errors while running the cargo commands.

![cargo command error](https://www.hackingloops.com/wp-content/uploads/2019/11/cargo-command-error.png)

Install the following dependencies if they are not already installed on your system.

```
apt install build-essential libsqlite3-dev libseccomp-dev publicsuffix
```

![sn0int requirements installation](https://www.hackingloops.com/wp-content/uploads/2019/11/sn0int-requirements-installation.png)

After installing the dependencies, clone Sn0int from Github using the following command.

```
git clone https://github.com/kpcyrd/sn0int.git
```

![sn0int cloning](https://www.hackingloops.com/wp-content/uploads/2019/11/sn0int-cloning.png)

Navigate to the _sn0int_ directory and run the following _cargo path_ command to complete the installation.

```
cd sn0int  
cargo install -f --path .
```

![sn0int installation](https://www.hackingloops.com/wp-content/uploads/2019/11/sn0int-installation.png)

First Interaction with Sn0int

Sn0int installs the default modules during the first run of the framework. The following command executes Sn0int in the terminal.

```
sn0int
```

![sn0int initial state](https://www.hackingloops.com/wp-content/uploads/2019/11/sn0int-initial-state.png)

As we can see in the screenshot, Sn0int comes with no pre-installed modules. Running the _quickstart_ command installs all the default modules of the framework.

```
quickstart
```

![modules installation](https://www.hackingloops.com/wp-content/uploads/2019/11/40-modules-installation.png)

The _–help_ command shows different types of command arguments we can use to perform the intelligence tasks.

–help

![sn0int commands](https://www.hackingloops.com/wp-content/uploads/2019/11/help-commands-1.png)

There is a subcommand help section showing different arguments that can be used while running specific modules.

![sn0int subcommands](https://www.hackingloops.com/wp-content/uploads/2019/11/subcommands.png)

Creating Workspace

We can create different workspaces in Sn0int for different intelligence projects. Let’s create an example workspace called _domains_ using the following command.

```
workspace domains
```

We can add the target domain to the workspace as follows.

```
add domain  
Domain: webscantest.com
```

![workspace and domain selection](https://www.hackingloops.com/wp-content/uploads/2019/11/workspace-and-domain-selection.png)

Running Modules

The _mod list_ command lists all the installed modules. Currently, there are 40 default modules available in Sn0int.

```
mod list
```

![mod list](https://www.hackingloops.com/wp-content/uploads/2019/11/mod-list-command.png)

We can call any module through _the use _command. Let’s call the certificate transparency logs _(ctlogs) _module to find the subdomains associated with the target domain _(webscantest.com)._

```
use ctlogs  
run
```

![subdomain finding](https://www.hackingloops.com/wp-content/uploads/2019/11/subdomain-finding.png)

As we can see the framework has found few subdomains associated with the target domain. The _dns-resolve_ module can find out which subdomains (hosts) are resolvable and their IP addresses.

```
use dns-resolve  
run
```

![resolveable addresses](https://www.hackingloops.com/wp-content/uploads/2019/11/resolve-able-addresses.png)

The next module we can try is _url-scan_ that identifies the webpages on each host.

```
use url-scan  
run
```

![status 200 ok](https://www.hackingloops.com/wp-content/uploads/2019/11/status-200-ok.png)

The above results not only validate the existence of web pages for each subdomain but also confirm the _open_ status of port 80 and 443 for each target host. The results also show the _http_ and _https_ responses by the target hosts.  We can apply more modules to further investigate the target as per the requirements.

Conclusion

Sn0int can perform open-source intelligence tasks in sequential orders. We can generate a hierarchy of information and store results in a database.