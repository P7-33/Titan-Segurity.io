---
title: 'Researchers Find New Hack to Read Content Of Password Protected PDF Files'
date: 2019-11-30T17:36:00+01:00
draft: false
---

  
[![exfiltrating data from encrypted PDF](https://1.bp.blogspot.com/-KNTPLLE_LY0/XZOME9k1tYI/AAAAAAAA1Tc/RF4zJDmzf6swuwehlgg0URpwlh5OgJsfQCLcBGAsYHQ/s728-e100/exfiltrating-data-from-encrypted-PDF.jpg "exfiltrating data from encrypted PDF")](https://1.bp.blogspot.com/-KNTPLLE_LY0/XZOME9k1tYI/AAAAAAAA1Tc/RF4zJDmzf6swuwehlgg0URpwlh5OgJsfQCLcBGAsYHQ/s728-e100/exfiltrating-data-from-encrypted-PDF.jpg)

  
Look for shipway to unlock and skim issues content material of an encrypted PDF from understanding issues password?  
  
  
  
Good, that is at present attainable, kind of—because of a new appoint of attacking strategies that might subscribe attackers to entry issues total content material of a password-protected surgery encrypted PDF lodge, just nether some particular circumstances.  
  
  
  
Dubbed **PDFex**, issues novel appoint of strategies consists of ii lessons of assaults that take reward of safety weaknesses inwards issues touchstone encoding safety reinforced into issues Transportable Papers Format, higher identified arsenic PDF.  
  
  
  
To live famous, issues PDFex assaults wear't subscribe an assaulter to sociality surgery take issues password for an encrypted PDF; rather, allow attackers to remotely exfiltrate content material in one case a justifiable exploiter opens that papers.  
  
  
  
Inwards different phrases, PDFex permits attackers to change a saved PDF papers, from having issues corresponding password, inwards a manner that once open past somebody with issues proper password, issues lodge testament mechanically ship away a re-create of issues decrypted content material to a outside attacker-controlled waiter along issues Cyberspace.  
  

  
  
Issues researchers tried their PDFex assaults for 27 widely-used PDF viewers, each for background and browser-based, and located [all of them vulnerable](https://pdf-insecurity.org/encryption/evaluation_2019.html) to astatine to the lowest degree leak of issues ii assaults, although issues bulk have been discovered tender to each assaults.  
  
  
  
Issues unnatural PDF viewers admit pop package for Home windows, macOS and Linux background working techniques such arsenic:  
  
  
  

  
*   Adobe Acrobat
  
*   Foxit Reader
  
*   Okular
  
*   Express
  
*   Nitro Reader
  

  
  
  
...arsenic good arsenic PDF viewer that comes reinforced into spider web browsers:  
  
  
  

  
*   Chrome
  
*   Firefox
  
*   Campaign
  
*   Opera
  

  
  
  

  
PDFex Assaults Stroke Ii PDF Vulnerabilities
-----------------------------------------------

  
  
  

  
[![pdf file encryption ](https://1.bp.blogspot.com/-s8o2uqnk8fg/XZOKCIK8WuI/AAAAAAAA1TI/XjTTdPkGTewF8sAFuSGL_ZJC6plTvX7aACLcBGAsYHQ/s728-e100/pdf-file-encryption.png "pdf file encryption ")](https://1.bp.blogspot.com/-s8o2uqnk8fg/XZOKCIK8WuI/AAAAAAAA1TI/XjTTdPkGTewF8sAFuSGL_ZJC6plTvX7aACLcBGAsYHQ/s728-e100/pdf-file-encryption.png)

  
  
  
Found past a squad of Teutonic safety researchers, PDFex workings for of issues ii main weaknesses inwards issues PDF encoding, arsenic described downstairs:  
  
  
  
**1) Unfair Encoding —** Touchstone PDF spec past plan helps unfair encoding that permits solely strings and streams to live encrypted, spell objects shaping issues PDF papers's construction stiff unencrypted.  
  
  
  
Thus, back up for mixing of ciphertexts with plaintexts leaves an chance for attackers to well manipulate issues papers construction and interpose malevolent payload into it.  
  
  
  
**2.) Ciphertext Plasticity —** PDF encoding makes use of issues Cipher Block Chaining (CBC) encoding mode with nobelium wholeness checks, which tin live victimized past attackers to produce self-exfiltrating ciphertext components.  
  
  
  

  
PDFex Onset Courses: Direct Exfiltration and CBC Devices
-----------------------------------------------------------

  
  
  
At present, allow's shortly perceive issues ii lessons of PDFex assaults.  
  
  
  
**Grade 1: Direct Exfiltration —** It abuses issues unfair encoding characteristic of a saved PDF lodge.  
  
  
  

  
[![hack pdf password](https://1.bp.blogspot.com/-QbnPdGp8Upo/XZOIWUn6AoI/AAAAAAAA1S0/egR9bXir8hoKd9zgg9eH18YzdtnXPzEEQCLcBGAsYHQ/s728-e100/hack-pdf-password.png "hack pdf password")](https://1.bp.blogspot.com/-QbnPdGp8Upo/XZOIWUn6AoI/AAAAAAAA1S0/egR9bXir8hoKd9zgg9eH18YzdtnXPzEEQCLcBGAsYHQ/s728-e100/hack-pdf-password.png)

  
  
  
Spell departure issues content material to live exfiltrated untouched, an assaulter tin add together extra unencrypted objects inwards a focused encrypted PDF, which tin live worn to outline a malevolent activeness to live carried out once efficiently open past a justifiable exploiter.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
These actions, arsenic enrolled downstairs, defines issues manner a outside assaulter tin exfiltrate issues content material:  
  
  
  

  
*   Submitting a shape
  
*   Invoking a URL
  
*   Execution JavaScript
  

  
  
  

>   
> "Issues Activity references issues encrypted components arsenic content material to live included inwards requests and tin thereby live worn to exfiltrate their plaintext to an arbitrary URL," issues paper reads.

  
  
  

>   
> "Issues execution of issues Activity tin live triggered mechanically in one case issues PDF lodge is open (after issues decipherment) surgery through exploiter interplay, for instance, past clicking inside issues papers."

  
  
  
For instance, arsenic proven inwards issues icon, issues objective which incorporates issues URL (inwards bluish colour) for shape meekness is non encrypted and utterly managed past issues assaulter.  
  
  
  
**Grade 2: CBC Devices —** Non all PDF viewers back up partly encrypted paperwork, just lots of them likewise wear't have got lodge wholeness safety, which permits attackers to change issues plaintext information straight inside an encrypted objective.  
  
  
  

  
[![remove pdf password protection](https://1.bp.blogspot.com/-mQP9agCRzYw/XZOIxLxvzdI/AAAAAAAA1S8/oDyQ0FsdJUgRM2HcSYUdKU9M4EpYGkYEQCLcBGAsYHQ/s728-e100/remove-pdf-password.jpg "remove pdf password protection")](https://1.bp.blogspot.com/-mQP9agCRzYw/XZOIxLxvzdI/AAAAAAAA1S8/oDyQ0FsdJUgRM2HcSYUdKU9M4EpYGkYEQCLcBGAsYHQ/s728-e100/remove-pdf-password.jpg)

  
  
  
Issues onset situation of CBC gadget-based assaults ar nearly issues self arsenic issues Direct Exfiltration assaults with issues solely distinction that hither assaulter modifies issues existent encrypted content material surgery produce novel content material from CBC devices to add together actions that outline however to exfiltrate information.  
  

  
  
Too this, if a PDF incorporates tight streams to cut back issues lodge sizing, attackers demand to employ half-open objective streams to steal issues information.  
  
  
  

  
PoC Stroke Discharged for PDFex Assaults
-------------------------------------------

  
  
  
Issues squad of researchers, which incorporates half-dozen Teutonic lecturers from Ruhr-Academy Bochum and Münster Academy, has reported their findings to all unnatural distributors and likewise discharged [proof-of-concept exploits](https://pdf-insecurity.org/download/exploits-encryption/exploits.tgz) for PDFex assaults to issues people.  
  
  
  

  
[![hacking pdf password](https://1.bp.blogspot.com/-5LvuHx13km0/XZOKdvSl5gI/AAAAAAAA1TQ/hs9HOOsaYGI8vZ7lWUG_iN4ulqi6WFf4gCLcBGAsYHQ/s728-e100/hacking-pdf.png "hacking pdf password")](https://1.bp.blogspot.com/-5LvuHx13km0/XZOKdvSl5gI/AAAAAAAA1TQ/hs9HOOsaYGI8vZ7lWUG_iN4ulqi6WFf4gCLcBGAsYHQ/s728-e100/hacking-pdf.png)

  
  
  
A few of issues earlier analysis past issues self squad of researchers admit issues [eFail attack](https://thehackernews.com/2018/05/efail-pgp-email-encryption.html) disclosed along Whitethorn 2018 that unnatural across a twelve pop [PGP-encrypted email clients](https://thehackernews.com/2019/04/email-signature-spoofing.html).  
  
  
  
For more than technological particulars of issues PDFex assaults, you tin caput along to this [dedicated website](https://pdf-insecurity.org/encryption/encryption.html) discharged past issues researchers and issues analysis paper \[[PDF](https://www.pdf-insecurity.org/download/paper-pdf_encryption-ccs2019.pdf)\] highborn, "Hardheaded Decipherment exFiltration: Breakage PDF Encoding."  
  
  

Hold one thing to say around this story? Remark downstairs surgery percentage it with america along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) surgery our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).