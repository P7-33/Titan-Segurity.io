---
title: 'Easy Social Share Buttons for WordPress v6.2.9 nulled'
date: 2019-10-31T08:06:00+01:00
draft: false
---

In this post, you will learn how to test security loopholes in Drupal CMS for any critical vulnerability which can cause great damage to any website if found on any webserver.  In this article, you will learn how a misconfigured web application can be easily exploited.

**Remote Code Execution:** Remote Code Evaluation is a vulnerability that occurs because of the unsafe handling of inputs by the server application or that can be exploited if user input is injected into a File or a String and executed by the programming language’s parser or the user input is not sanitised properly in POST request and also when accepting query string param during GET requests.

Therefore a Remote Code Evaluation can lead to a full compromise of the vulnerable web application and also a web server.

**Let’s Begin!!**

So the drupal is accessible through a web browser by exploring the following URL:

```
http://192.168.10.117/drupal
```

And this opens the default home page, to access the dashboard you must-have credential for login.

![](https://i0.wp.com/1.bp.blogspot.com/-p5WuniFLZ98/Xbp6GlLhnSI/AAAAAAAAhJw/NeO8IxfR7WUy7IXwW8kw0o5g0ZufIaAqgCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

So, to access the user console, I used following creds.

```
Username:raj  
Password:123
```

![](https://i2.wp.com/1.bp.blogspot.com/-p9XU3rDXnQc/Xbp6GrGQ0BI/AAAAAAAAhJo/40MclehkX40DVqesGckZZkLbVOv2XidZgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

After accessing the admin console, it was time to exploit web application by injecting malicious content inside it. Directly writing malicious scripts as web content will not give us the reverse shell of the application but after spending some time, we concluded that it requires PHP module. We, therefore, move to install new module through **_Manage>Extend>List>Install new module_**.

You can download the PHP package for Drupal from the URL below and upload the tar file to install the new module.

https://ift.tt/2ec4Oze

![](https://i0.wp.com/1.bp.blogspot.com/-hHb-Sia2f8w/Xbp6Gg_vY8I/AAAAAAAAhJs/GIyZiNhdna4Ip5wzDdfGuqacLzeBMfTtQCLcBGAsYHQ/s1600/13.5.png?w=687&ssl=1)

To install php module upload the tar file that was downloaded.

![](https://i1.wp.com/1.bp.blogspot.com/-Z_JMFIlSLAE/Xbp6HvdEViI/AAAAAAAAhJ0/Nl1GPB4TfRwin3QU91jyJnnNarOFfD2rgCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

So, when the installation is completed, we need to enable to the added module.

![](https://i1.wp.com/1.bp.blogspot.com/-Nu5Pg87KRg4/Xbp6HwQOjaI/AAAAAAAAhJ8/EZr9I0DFVQYfgB3Iq-kuMuUAGcfk8kRtwCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Again, move to **Manage > Extend >filters** and enable the checkbox for PHP filters.

![](https://i1.wp.com/1.bp.blogspot.com/-hBglmPhyUOM/Xbp6H3oM2PI/AAAAAAAAhJ4/GzbJ3DhZNHMCEys-vRL1WVnByRXPytYcgCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Now use the Pentest monkey PHP script, i.e. “reverse shell backdoor.php” to be injected as basic content. Don’t forget to add a “listening IP & port” to get a reversed connection. Continue to change the “text format to PHP” and enable the publishing checkbox. Keep the netcat listener ON in order to receive the incoming shell.

When everything is set accordingly, click the preview button and you’ll get the reverse connection over the netcat.

![](https://i1.wp.com/1.bp.blogspot.com/-0mJStJQMszg/Xbp6IlNJFHI/AAAAAAAAhKE/BgbfiPgrgOsTmkY5vu77DBp7Mc6RKWceQCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Hence, we got the reverse connection of the host machine.

![](https://i1.wp.com/1.bp.blogspot.com/-f_JQLIcho5w/Xbp6IXXR7dI/AAAAAAAAhKA/FiKGZXSZVesIjz3vvA5spHuWxVVVYiD9ACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

**Author**: Komal Singh is a Cyber Security Researcher and Technical Content Writer, she is completely enthusiastic pentester and Security Analyst at Ignite Technologies. Contact [**Here**](https://www.linkedin.com/in/komal-rajput-26b783131/)

The post [Drupal: Reverseshell](https://www.hackingarticles.in/drupal-reverseshell/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2JDx12F