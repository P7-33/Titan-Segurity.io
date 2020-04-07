---
title: 'Ako Ransomware usa spam para infectar a sus víctimas'
date: 2020-01-16T22:33:00+01:00
draft: false
---

[![Ako Ransomware Uses Spam to Infect Its Victims](https://www.bleepstatic.com/content/hl-images/2018/07/10/ransomware-header.jpg)](https://www.bleepstatic.com/content/hl-images/2018/07/10/ransomware-header.jpg)
===================================================================================================================================================================================================================

Se ha descubierto que el ransomware Ako se distribuye a través de archivos adjuntos de spam malintencionados que pretenden ser un acuerdo solicitado.

La semana pasada informamos sobre el [ransomware Ako](https://www.bleepingcomputer.com/news/security/ako-ransomware-another-day-another-infection-attacking-businesses/) y cómo se dirigía a las empresas con la intención de cifrar toda su red. En ese momento, no se sabía cómo se distribuía y cuando le preguntamos a los operadores de ransomware nos dijeron que era un "secreto".  
  
Desde entonces, el sitio de identificación de ransomware ID-Ransomware ha visto una cantidad cada vez mayor de víctimas.

  
  
  
  
  

![ID Ransomware Submissions](https://www.bleepstatic.com/images/news/ransomware/a/a/ako/spam-distribution/idr-submissions.jpg)

ID Ransomware Submissions

  

David Pickett, analista sénior de ciberseguridad en AppRiver, se comunicó ayer con BleepingComputer para decirnos que su compañía vio que el ransomware Ako se distribuía por correo electrónico.  
  
Estos correos electrónicos pretenden contener un acuerdo solicitado por el destinatario y utilizan asuntos de correo tales como "Acuerdo 2020 # 1775505".

  
  
  
  

![Spam email distributing the Ako Ransomware](https://www.bleepstatic.com/images/news/ransomware/a/a/ako/spam-distribution/spam-email.jpg)

Spam email distributing the Ako Ransomware

Se adjunta a estos correos electrónicos un archivo zip protegido por contraseña llamado Agreement.zip con la contraseña '2020' que se proporciona en el correo electrónico.  
  
El archivo extraído contendrá un ejecutable renombrado como Agreement.scr que cuando se ejecute instalará el ransomware.

  
  
  

![Agreement.zip Archive](https://www.bleepstatic.com/images/news/ransomware/a/a/ako/spam-distribution/archive.jpg)

Agreement.zip Archive

Como se muestra en este [informe de JoeSandbox](https://www.joesandbox.com/analysis/200688/0/html), cuando se ejecuta Ako, cifrará los archivos de la víctima y los dejará con una nota de rescate llamada ako-readme.txt.

  
  
  
  

![Ako Ransom Note](https://www.bleepstatic.com/images/news/ransomware/a/a/ako/ransom-note.jpg)

Ako Ransom Note

Como el spam se está utilizando para difundir el ransomware Ako, todos deben recibir capacitación sobre cómo identificar correctamente el correo electrónico malicioso y no abrir ningún archivo adjunto sin confirmar primero a quién y por qué se enviaron.  
  
Esto es especialmente cierto para los archivos adjuntos de correo electrónico que están en archivos protegidos con contraseña, ya que se usan comúnmente para evitar ser detectados por pasarelas de correo electrónico seguras y software antivirus.

  

Fuente: [https://www.bleepingcomputer.com/](https://www.bleepingcomputer.com/news/security/ako-ransomware-uses-spam-to-infect-its-victims/)

No olvides Compartir... 

  

Siguenos en twitter: [@disoftin](http://twitter.com/disoftin) - [@fredyavila](http://twitter.com/fredyavila)