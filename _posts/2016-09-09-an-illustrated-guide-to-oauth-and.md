---
title: 'An Illustrated Guide to OAuth and OpenID Connect'
date: 2019-10-25T07:32:00+01:00
draft: false
---

In the “stone age” days of the Internet, sharing information between services was easy. You simply gave your username and password for one service to another so they could login to your account and grab whatever information they wanted!

![Shady Budget Planner](https://d33wubrfki0l68.cloudfront.net/89c462a5d1fa7c53524902a682463f920c694767/5eba9/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/shady-budget-planner-3fc7da122783122e86b1c2bd7ba6a026ecc3ac9ab1b4c5d725d0a91614cd93e0.jpg)

Yikes! You should never be required to share your username and password, your _credentials_, to another service. There’s no guarantee that an organization will keep your credentials safe, or guarantee their service won’t access more of your personal information than necessary. It might sound crazy, but some applications still try to get away with this!

Today we have an agreed-upon standard to securely allow one service to access data from another. Unfortunately, these standards use a lot of jargon and terminology that make them more difficult to understand. The goal of this post is to explain how these standards work using simplified illustrations.

You can think of this post as the worst children’s book ever. You’re welcome.

![The Illustrated Guide to OAuth and OpenID Connect](https://d33wubrfki0l68.cloudfront.net/ea2c82aee671b0a77c1c78f9d758fa7eea34bbfa/0eac3/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/illustrated-guide-to-oauth-and-oidc-post-04e626d73bcd02dd03b1c7624a6076683f66694414293aab0803ea07aa1a63e9.jpg)

Ladies and Gentlemen, Introducing OAuth 2.0
-------------------------------------------

[OAuth 2.0](https://oauth.net/2/) is a security standard where you give one application permission to access _your data_ in another application. The steps to grant permission, or _consent_, are often referred to as _authorization_ or even _delegated authorization_. You authorize one application to access your data, or use features in another application on your behalf, without giving them your password. Sweet!

As an example, let’s say you’ve discovered a web site named “Terrible Pun of the Day” and create an account to have it send an awful pun joke as a text message every day to your phone. You love it so much, you want to share this site with everyone you’ve ever met online. Who wouldn’t want to read a bad pun every day, am I right?

![Terrible Pun of the Day](https://d33wubrfki0l68.cloudfront.net/1f86db70aeac98806dcb35748e968696d5414a46/61ef4/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/terrible-pun-of-the-day-8a4b14ffbdf205d9441a63fb6584ae99bf4bb96c3bb4f05fc5fbc48da6ff545d.jpg)

However, writing an email to every person in your contacts list sounds like a lot of work. And, if you’re like me, you’ll go to great lengths to avoid anything that smells like work. Good thing “Terrible Pun of the Day” has a feature to invite your friends! You can grant “Terrible Pun of the Day” access to your email contacts and send out emails for you! OAuth for the win!

![Authorize Terrible Pun of the Day to Access Your Contacts](https://d33wubrfki0l68.cloudfront.net/7c805b557bdb9df3231e07943315517e044a012a/5cdbc/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/authorize-tpotd-contacts-9f4dca35e4c91b5d808f65f64bb14cc40e7c701742f4b764c5baa8acfeb59020.jpg)

1.  Pick your email provider
2.  Redirect to your email provider and login if needed
3.  Give “Terrible Pun of the Day” permission to access to your contacts
4.  Redirect back to “Terrible Pun of the Day”

> In case you change your mind, applications that use OAuth to grant access also provide a way to revoke access. Should you decide later you no longer want your contacts shared, you can go to your email provider and remove “Terrible Pun of the Day” as an authorized application.

### Let the OAuth Flow

You’ve just stepped through what is commonly referred to as an OAuth _flow_. The OAuth flow in this example is made of visible steps to _grant consent_, as well as some invisible steps where the two services agree on a secure way of exchanging information. The previous “Terrible Pun of the Day” example uses the most common OAuth 2.0 flow, known as the “authorization code” flow.

Before we dive into more details on what OAuth is doing, let’s map some of the OAuth terminologies.

![Resource Owner](https://d33wubrfki0l68.cloudfront.net/d7b82a2e5f24d6837cf1615bff0d2f95cf1bfe8c/a7459/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/resource-owner-dda19a504066d1902cfa07584c30b8eea9ed3016240f8081c6373dd6102a32f6.jpg)

**Resource Owner**: You! You are the owner of your identity, your data, and any actions that can be performed with your accounts.

![Client](https://d33wubrfki0l68.cloudfront.net/2c476ff82bde89d4ca82255343265d53821582df/5ad58/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/client-b2de9ec0448544254cc48d0900916297c49ed72bb4cf5757c096250da9440d98.jpg)

**Client**: The application (e.g. “Terrible Pun of the Day”) that wants to access data or perform actions on behalf of the **Resource Owner**.

![Authorization Server](https://d33wubrfki0l68.cloudfront.net/e05eae8baa4a0c3b4cf995c90e439913a2f35d14/f8f6b/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/authorization-server-53d3a31f16de5a829e9dee950484c2028698b345aaeffc6c354ea4f6e556ce30.jpg)

**Authorization Server**: The application that knows the **Resource Owner**, where the **Resource Owner** already has an account.

![Resource Server](https://d33wubrfki0l68.cloudfront.net/253b628c3113744ccdcdd59776249c2920fcef24/0a6ca/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/resource-server-a18f62d1b3e8a105c27523a9c95a292eef90029953d2d8c561b8d7604e9b11a6.jpg)

**Resource Server**: The Application Programming Interface (API) or service the **Client** wants to use on behalf of the **Resource Owner**.

![Redirect URI](https://d33wubrfki0l68.cloudfront.net/a5baf1c81248cac7f2f717d8a713386dfbe1cc4e/0df72/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/redirect-uri-a51f4cf691cc2f03a8c2c99ac207d8bc7fd190ce8ae6d3245dcef49396672c7f.jpg)

**Redirect URI**: The URL the **Authorization Server** will redirect the **Resource Owner** back to after granting permission to the **Client**. This is sometimes referred to as the “Callback URL.”

![Response Type](https://d33wubrfki0l68.cloudfront.net/4aaee74784e1dfaa259690eb4b10f6fee00cc78a/a210f/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/response-type-0d590f738af30ba6a0b25e945c476d59eb9928e4dfc92a9ad21f1eba959742ad.jpg)

**Response Type**: The type of information the **Client** expects to receive. The most common Response Type is `code`, where the **Client** expects an **Authorization Code**.

![Scope](https://d33wubrfki0l68.cloudfront.net/ef43b2659081995bee0f1976b9649e9891987c89/67052/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/scope-152d928d9e47e9ea93e54479e320bcbb98da352a8d070502a314df9c6e9fbf92.jpg)

**Scope**: These are the granular permissions the **Client** wants, such as access to data or to perform actions.

![Consent](https://d33wubrfki0l68.cloudfront.net/591b93dbab089cc04f25c13394faadc316da06d4/79524/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/consent-f5e59161add3500fd008f180ee6704b6880d67a39dc545e1696b9408ba364087.jpg)

**Consent**: The **Authorization Server** takes the **Scopes** the **Client** is requesting, and verifies with the **Resource Owner** whether or not they want to give the **Client** permission.

![Client ID](https://d33wubrfki0l68.cloudfront.net/13301a91be542e9c54fc20d9d3e0aa1c58aba2e8/fc891/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/client-id-81159792607654ac7210a08960ba2679c7af89260f96fa4ca650d8c63757fdaa.jpg)

**Client ID**: This ID is used to identify the **Client** with the **Authorization Server**.

![Client Secret](https://d33wubrfki0l68.cloudfront.net/98c855ff458ad9bde36f4e1200d4b053ee146747/5e38f/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/client-secret-2c1b4829a91671414eef5f8fce5ea9636b40150197d2deb1695df314a49f5bea.jpg)

**Client Secret**: This is a secret password that only the **Client** and **Authorization Server** know. This allows them to securely share information privately behind the scenes.

![Authorization Code](https://d33wubrfki0l68.cloudfront.net/56815776b50b08e97b2ec253bf6ccc54f55d1fe7/f2968/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/authorization-code-2c15e268333e4fd5e1f68db54a8a43b890b2e2c958cd1fedf7ec070ebb9eba0e.jpg)

**Authorization Code**: A short-lived temporary code the **Client** gives the **Authorization Server** in exchange for an **Access Token**.

![Access Token](https://d33wubrfki0l68.cloudfront.net/eb70ecaee2b9bb8df7702afdeaf218309344b970/3be7c/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/access-token-b5edc0a7db64a6a01db4e3d0b0207c924938453bab1bed526708425d57df9c2b.jpg)

**Access Token**: The key the client will use to communicate with the **Resource Server**. This is like a badge or key card that gives the **Client** permission to request data or perform actions with the **Resource Server** on your behalf.

> Note: Sometimes the “Authorization Server” and the “Resource Server” are the same server. However, there are cases where they will _not_ be the same server or even part of the same organization. For example, the “Authorization Server” might be a third-party service the “Resource Server” trusts.

Now that we have some of the OAuth 2.0 vocabulary handy, let’s revisit the example with a closer look at what’s going on throughout the OAuth flow.

![Terrible Pun of the Day Authorization Code Flow](https://d33wubrfki0l68.cloudfront.net/e65239bdbd8b982d8eda9f1da9f486efdb11af1d/1cc5c/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/tpotd-authorization-code-flow-f959373be5520c3f3a78fbd0a340c5ea67e75cf27979476cf66670914de5e6ba.jpg)

1.  You, the **Resource Owner**, want to allow “Terrible Pun of the Day,” the **Client**, to access your contacts so they can send invitations to all your friends.
2.  The **Client** redirects your browser to the **Authorization Server** and includes with the request the **Client ID**, **Redirect URI**, **Response Type**, and one or more **Scopes** it needs.
3.  The **Authorization Server** verifies who you are, and if necessary prompts for a login.
4.  The **Authorization Server** presents you with a **Consent** form based on the **Scopes** requested by the **Client**. You grant (or deny) permission.
5.  The **Authorization Server** redirects back to **Client** using the **Redirect URI** along with an **Authorization Code**.
6.  The **Client** contacts the **Authorization Server** directly (does not use the **Resource Owner**’s browser) and securely sends its **Client ID**, **Client Secret**, and the **Authorization Code**.
7.  The **Authorization Server** verifies the data and responds with an **Access Token**.
8.  The **Client** can now use the **Access Token** to send requests to the **Resource Server** for your contacts.

### Client ID and Secret

Long before you gave “Terrible Pun of the Day” permission to access your contacts, the Client and the Authorization Server established a working relationship. The Authorization Server generated a Client ID and Client Secret, sometimes called the App ID and App Secret, and gave them to the Client to use for all future OAuth exchanges.

![Client receives the Client ID and Client Secret from the Authorization Server](https://d33wubrfki0l68.cloudfront.net/b48af32086ee9d8822d22d2737a38573f48bc9c7/8bc08/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/client-auth-server-id-secret-40d6636c858938befc6bd10a948b82b1118b9956b5ccaa56e6323ed78107b71e.jpg)

As the name implies, the Client Secret must be kept secret so that only the Client and Authorization Server know what it is. This is how the Authorization Server can verify the Client.

That’s Not All Folks… Please Welcome OpenID Connect
---------------------------------------------------

OAuth 2.0 is designed only for _authorization_, for granting access to data and features from one application to another. [OpenID Connect](https://openid.net/connect/) (OIDC) is a thin layer that sits on top of OAuth 2.0 that adds login and profile information about the person who is logged in. Establishing a login session is often referred to as _authentication_, and information about the person logged in (i.e. the **Resource Owner**) is called _identity_. When an Authorization Server supports OIDC, it is sometimes called an _identity provider_, since it _provides_ information about the **Resource Owner** back to the **Client**.

OpenID Connect enables scenarios where one login can be used across multiple applications, also known as _single sign-on_ (SSO). For example, an application could support SSO with social networking services such as Facebook or Twitter so that users can choose to leverage a login they already have and are comfortable using.

![FleaMail SSO](https://d33wubrfki0l68.cloudfront.net/dd0211670c1e1d7553dd8fe40d9130d79586ef5d/bdf38/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/fleamail-sso-141794170f7e28141b0cf65e8a174b7c036bcf9b9aa1e80bc1f1a72496daf082.jpg)

The OpenID Connect flow looks the same as OAuth. The only differences are, in the initial request, a specific scope of `openid` is used, and in the final exchange the **Client** receives both an **Access Token** and an **ID Token**.

![Terrible Pun of the Day OIDC Example](https://d33wubrfki0l68.cloudfront.net/5e16fd7ccb2302d02db4a34a648ee4a58dbef364/3d4ed/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/tpotd-oidc-example-191accef3b901cec19fcbfa3eba7d4a175e3545e60efd656e3aea959a3df4deb.jpg)

As with the OAuth flow, the OpenID Connect **Access Token** is a value the **Client** doesn’t understand. As far as the **Client** is concerned, the **Access Token** is just a string of gibberish to pass with any request to the **Resource Server**, and the **Resource Server** knows if the token is valid. The **ID Token**, however, is very different.

### Jot This Down: An ID Token is a JWT

An **ID Token** is a specifically formatted string of characters known as a JSON Web Token, or JWT. JWTs are sometimes pronounced “jots.” A JWT may look like gibberish to you and me, but the **Client** can extract information embedded in the JWT such as your ID, name, when you logged in, the **ID Token** expiration, and if anything has tried to tamper with the JWT. The data inside the **ID Token** are called _claims_.

![Terrible Pun of the Day Examines an ID Token](https://d33wubrfki0l68.cloudfront.net/d7271a547f8b4e5535c266bccd89470581602b66/ea674/assets-jekyll/blog/illustrated-guide-to-oauth-and-oidc/tpotd-examining-id-token-8d047e404d0d789cd2996d4d7d7601bccd9741905e80b3720b3565208eebd453.jpg)

With OIDC, there’s also a standard way the **Client** can request additional _identity_ information from the **Authorization Server**, such as their email address, using the **Access Token**.

Learn More About OAuth and OIDC
-------------------------------

That’s OAuth and OIDC in a nutshell! Ready to dig deeper? Here are some additional resources to help you learn more about OAuth 2.0 and OpenID Connect!

As always, feel free to leave comments below. To make sure you stay up to date with our latest developer guides and tips follow us on [Twitter](https://twitter.com/oktadev) and subscribe to our [YouTube Channel](https://www.youtube.com/c/oktadev)!

  
  
from Hacker News https://ift.tt/2JbmgnU