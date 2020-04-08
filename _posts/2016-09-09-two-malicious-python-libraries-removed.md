---
title: 'Two malicious Python libraries removed from PyPI'
date: 2019-12-04T02:11:00+01:00
draft: false
---

![olgired2017.png](https://zdnet4.cbsistatic.com/hub/i/2019/12/04/9d6de096-5c14-4888-976b-6bb4a36a5c61/3b8da917af66d7d01f9849156e6d6e04/olgired2017.png)

Image: ZDNet

The Python security team removed two trojanized Python libraries from PyPI (Python Package Index), its official package repository.

The two libraries were created by the same developer and mimicked other more popular libraries -- using a technique called [typosquatting](https://en.wikipedia.org/wiki/Typosquatting) to register similarly-looking names.

The first is "[python3-dateutil](https://pypi.org/project/python3-dateutil/)," which imitated the popular "[dateutil](https://pypi.org/project/python-dateutil/)" library. The second is "[jeIlyfish](https://pypi.org/project/jeIlyfish/)" (the first L is an I), which mimicked the "[jellyfish](https://pypi.org/project/jellyfish/)" library.

The two malicious clones were [discovered](https://github.com/dateutil/dateutil/issues/984) on Sunday, December 1, by German software developer Lukas Martini. Both libraries were removed on the same day after Martini notified dateutil developers and the PyPI security team.

While the python3-dateutil was created and uploaded on PyPI two days before, on November 29, the jeIlyfish library had been available for nearly a year, since December 11, 2018.

### Mysterious malicious code

According to Martini, the malicious code was present only in the jeIlyfish library. The code downloaded and read [a list of hashes](https://gitlab.com/olgired2017/aeg_wandoo_dag_m3/raw/master/hashsum) stored in a GitLab repository.

The nature and purpose of these hashes are currently unknown, as neither Martini or the PyPI team detailed the behavior in great depth before the library was promptly removed from PyPI.

The python3-dateutil package didn't contain malicious code of its own, but it did import the jeIlyfish library, meaning it was malicious by association.

Both libraries were uploaded on PyPI by the same developer, who used the username of olgired2017 -- also used for the GitLab account.

It is believed that olgired2017 created the dateutil clone in an attempt to capitalize on the original's library popularity and increase the reach of the malicious code; however, this also brought more attention from more developers and eventually ended up in exposing his entire operation.

### Developers advised to review projects

Excluding the malicious code, both typosquatted packages were identical copies of the original libraries, meaning they would have worked as the originals.

Developers who didn't pay attention to the libraries they downloaded or imported into their projects should check to see if they've used the correct package names and did not accidentally use the typo-squatted versions.

This is the third time the PyPI team intervenes to remove typo-squatted malicious Python libraries from the official repository. Similar incidents have happened in [September 2017](http://www.nbu.gov.sk/skcsirt-sa-20170909-pypi/) (ten libraries), [October 2018](https://www.zdnet.com/article/twelve-malicious-python-libraries-found-and-removed-from-pypi/) (12 libraries), and [July 2019](https://www.zdnet.com/article/malicious-python-libraries-targeting-linux-servers-removed-from-pypi/) (three libraries).

  
  
from Latest Topic for ZDNet in... https://ift.tt/34YGRog