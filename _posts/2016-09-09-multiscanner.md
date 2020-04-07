---
title: 'Multiscanner'
date: 2020-01-16T17:14:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-Ybnf4hArkGM/XgqpXMqDDdI/AAAAAAAARVc/YynBi4qPSvcnjvZHsEsV3HF_bqld2xvWwCNcBGAsYHQ/s640/multiscanner.png)](https://1.bp.blogspot.com/-Ybnf4hArkGM/XgqpXMqDDdI/AAAAAAAARVc/YynBi4qPSvcnjvZHsEsV3HF_bqld2xvWwCNcBGAsYHQ/s1600/multiscanner.png)

**Multiscanner - Modular File Scanning/Analysis Framework**

  

  
MultiScanner is a file [analysis framework](https://www.kitploit.com/search/label/Analysis%20Framework "analysis framework") that assists the user in evaluating a set of files by automatically running a suite of tools for the user and aggregating the output. Tools can be custom built Python scripts, web APIs, software running on another machine, etc. Tools are incorporated by creating modules that run in the [MultiScanner](https://www.kitploit.com/search/label/MultiScanner "MultiScanner") framework.  
Modules are designed to be quickly written and easily incorporated into the framework. Currently written and maintained modules are related to malware analytics, but the framework is not limited to that scope. For a list of modules you can look in [modules/](https://github.com/mitre/multiscanner/blob/master/modules "modules/"). Descriptions and config options can be found on the [Analysis Modules](https://multiscanner.readthedocs.io/en/latest/use/use-analysis-mods.html "Analysis Modules") page.  
MultiScanner also supports a [distributed](https://www.kitploit.com/search/label/Distributed "distributed") workflow for sample storage, analysis, and report viewing. This functionality includes a web interface, a REST API, a distributed file system (GlusterFS), distributed report storage / searching (Elasticsearch), and distributed task [management](https://www.kitploit.com/search/label/Management "management") (Celery / RabbitMQ). Please see [Architecture](https://multiscanner.readthedocs.io/en/latest/arch.html "Architecture") for more details.  
[](https://www.blogger.com/u/7/null)

[  
](https://www.blogger.com/u/7/null)

  

  
**Usage**  
MultiScanner can be used as a command-line interface, a Python API, or a distributed system with a web interface. See the documentation for more detailed information on [installation](https://multiscanner.readthedocs.io/en/latest/install.html "installation") and [usage](https://multiscanner.readthedocs.io/en/latest/use/index.html "usage").  
  
**Command-Line**  
Install Python (2.7 or 3.4+) if you haven't already.  
Then run the following (substituting the actual file you want to scan for ):

```
$ git clone [https://github.com/mitre/multiscanner.git](https://github.com/mitre/multiscanner.git)  
$ cd multiscanner  
$ sudo -HE ./install.sh  
$ multiscanner init
```

This will generate a default configuration for you. Check `config.ini` to see what modules are enabled. See [Configuration](https://multiscanner.readthedocs.io/en/latest/install.html#configuration "Configuration") for more information.  
Now you can scan a file (substituting the actual file you want to scan for ):

```
$ multiscanner 
```

You can run the following to get a list of all of MultiScanner's command-line options:

```
$ multiscanner --help
```

**Note**: If you are not on a RedHat or Debian based Linux distribution, instead of running the `install.sh` script, install pip (if you haven't already) and run the following:

```
$ pip install -r requirements.txt
```

  
**Python API**

```
import multiscanner  
multiscanner.config_init(filepath)  
output = multiscanner.multiscan(file_list)  
results = multiscanner.parse_reports(output, python=True)
```

  
**Web Interface**  
Install the latest versions of [Docker](https://docs.docker.com/engine/installation/ "Docker") and [Docker Compose](https://docs.docker.com/compose/install/ "Docker Compose") if you haven't already.

```
$ git clone [https://github.com/mitre/multiscanner.git](https://github.com/mitre/multiscanner.git)  
$ cd multiscanner  
$ docker-compose up
```

You may have to wait a while until all the services are up and running, but then you can use the web interface by going to `[http://localhost:8000](http://localhost:8000/)` in your web browser.  
_Note_: this should not be used in production; it is simply an introduction to what a full installation would look like. See [here](https://multiscanner.readthedocs.io/en/latest/install.html#standalone-docker-installation "here") for more details.  
  
**Documentation**  
For more information, see the [full documentation](https://multiscanner.readthedocs.io/ "full documentation") on ReadTheDocs.  
  

**[Download Multiscanner](http://ellevolaw.com/3jOF "Download Multiscanner")**

**Regards**

**Kang Asu**