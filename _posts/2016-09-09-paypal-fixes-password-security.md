---
title: 'PayPal Fixes ''High-Severity'' Password Security Vulnerability'
date: 2020-01-10T13:47:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-81UDQIQtkgE/XhhpWS6FKFI/AAAAAAAAB5A/jJn6lYKXezUlz849KtpvaMtbgvhskug4gCLcBGAsYHQ/s640/paypal-784404_960_720.webp)](https://1.bp.blogspot.com/-81UDQIQtkgE/XhhpWS6FKFI/AAAAAAAAB5A/jJn6lYKXezUlz849KtpvaMtbgvhskug4gCLcBGAsYHQ/s1600/paypal-784404_960_720.webp)

  

Researcher Alex Birsan, while examining PayPal's main authentication flow– discovered a critical security flaw that hackers could have exploited to access passwords and email addresses of users. He responsibly reported the vulnerability to PayPal on November 18, 2019, via the HackerOne bug bounty platform and received a bug bounty over $15,000 for the issue which was acknowledged by HackerOne after 18 days of its submission and later patched by the company on 11th December 2019. 

  

The aforementioned bug affected one of the primary and most visited pages amongst all of PayPal's, which is its 'login form' as mentioned by Birsan in the public disclosure of the flaw. 

  

As Birsan was exploring the main authentication flaw at PayPal, his attention got directed to a javascript file that seemingly contained a cross-site request forgery (CSRF) token along with a session ID. "providing any kind of session data inside a valid javascript file," the expert told in his blog post, "usually allows it to be retrieved by attackers." 

  

"In what is known as a cross-site script inclusion (XSSI) attack, a malicious web page can use an HTML tag to import a script cross-origin, enabling it to gain access to any data contained within the file." </div><div dir="auto" style="background-color: white; color: #222222; font-family: Arial, Helvetica, sans-serif; font-size: small;"><br /></div><div dir="auto" style="background-color: white; color: #222222; font-family: Arial, Helvetica, sans-serif; font-size: small;">While giving their confirmation, PayPal put forth that sensitive, unique tokens were leaked in a JS file employed by the Recaptcha implementation. Sometimes users find themselves in situations where they have to go through a captcha quiz after authentication and according to the inference drawn by PayPal, "the exposed tokens were used in the post request to solve the captcha challenge." The captcha quiz comes into play after multiple failed login attempts, that is normal until you come to terms with the fact that " “the response to the next authentication attempt is a page containing nothing but a Google captcha. If the captcha is solved by the user, an HTTP POST request to /auth/validate captcha is initiated.” Although, in order to successfully obtain the credentials, the hacker would be required to find a way of making targeted users visit an infected website prior to logging into their PayPal account. </div><div dir="auto" style="background-color: white; color: #222222; font-family: Arial, Helvetica, sans-serif; font-size: small;"><br /></div><div dir="auto" style="background-color: white; color: #222222; font-family: Arial, Helvetica, sans-serif; font-size: small;">While assuring its users, PayPal said that it “implemented additional controls on the security challenge request to prevent token reuse, which resolved the issue, and no evidence of abuse was found.”</div></div></div><br /><br />from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2NcXypm<br /></x-turndown>