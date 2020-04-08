---
title: 'Catalonia protestors use distributed network to securely organize protests'
date: 2019-10-20T09:33:00+01:00
draft: false
---

![](https://wi-images.condecdn.net/image/Gqj5q6aQ6qo/crop/1440/0.5235602094240838/f/gettyimages-1181890950.jpg "Catalonia has created a new kind of online activism. Everyone should pay attention | WIRED UK")  

Getty Images / Sandra Montanez / Staff

Trouble is brewing in Catalonia. On October 14, Spain’s supreme court in Madrid sentenced nine pro-independence Catalan politicians to long prison terms – from nine to 13 years – for their roles in the Catalan referendum on independence in 2017.

Following the verdict, furious protests have ripped through the streets of Catalonia. What at first began as peaceful mass demonstrations has sparked sporadic violence, with protestors setting fire to buildings and damaging property, and police spraying crowds with rubber bullets and water cannons.

To an outsider, the protests can look like a homogenous mass of angry citizens revolting against the Spanish state. But the movement encompasses different factions, from long-standing separatist groups ANC (Assemblea Nacional Catalana) and Òmnium, to absolute newcomers. Among the latter is a mysterious digital network called Tsunami Democràtic.

What is Tsunami Democràtic?
---------------------------

It is one faction of the multifaceted pro-independence protest movement in Catalonia, formed shortly before October 14. But despite its young age, it is relevant: according to Spanish daily newspaper _[El Pais](https://elpais.com/elpais/2019/10/15/inenglish/1571123222_635456.html)_, the group instigated what is arguably the most disruptive protest action undertaken so far – the mass occupation of Barcelona’s El Prat airport by an estimated 10,000 protesters. It is especially how they did it that caught many people’s attention: everything Tsunami Democràtic does is orchestrated completely online – and it isn’t clear who exactly is behind it.

#### Read next

The organisation broadcasts both on Twitter, where it currently counts more than 188,000 followers, and on Telegram, where it has as amassed more than 330,000 subscribers. It’s also launched an ambitious protest-organisation app – but more on that later. Its [webpage](https://tsunamidemocratic.github.io/), featuring a video of a wave engulfing the screen, appears more like a glossy travel site. (There are reports from within Catalonia that the website has been taken down in Spain; it remains accessible from the UK as of the evening of October 18.) The tsunami moniker might be inspired by the Bruce Lee ‘Be water’ quote that has been co-opted by the Hong Kong protestors to describe the movement as fluid, fast moving and adaptable.

“I didn't have a lot of faith in Tsunami Democràtic at first because there's been a lot of groups who sold themselves like they were going to be the revolution and then came to nothing,” says Alba Medrano, a 28-year-old activist based in Barcelona who has been involved in the pro-independence movement for the past 11 years. However, since the successful staging of the airport, confidence in the group has grown. She says right now activists are just waiting for the group’s next protest action to be called.

Medrano says that it’s still primarily other channels that she and fellow activists consult for updates. In particular, the Anonymous Catalonia group’s Telegram channel. “There, there’s a retransmission of everything that's happening. They keep posting every minute what's happening everywhere, so that's how we get information.”

However, where Tsunami Democràtic has managed to gain greater traction than established groups is online attention. For example, the Catalonia Anonymous faction counts just over 100,000 subscribers on Telegram, while CDR (Los Comités de Defensa de la República) has around 50,000.

But the group has another point of difference from others: a new app for coordinating protest activity in the region. Tsunami Democràtic has billed this as an organising tool that promises innovative ways of evading police detection and coordinating actions. Around 270,000 people have reportedly downloaded the app, which was only announced on Monday, October 14. It’s not yet been used to orchestrate activity, but the group has strongly encouraged people to download it ahead of more planned actions.

#### Read next

What does Tsunami Democràtic’s app do?
--------------------------------------

The app is a communication platform that's been designed to organise and mobilise protestors in a secure and efficient way – employing geolocation and friend-to-friend technologies to ensure only trusted members have access.

Getting access to the app isn't the most straight forward. It isn’t available through Android’s Play Store or on Apple’s App Store. Instead, you have to download an APK file (an Android Package file used to distribute applications on Google's Android operating system) from the website, and manually install it on your phone. The software doesn’t work on iPhones because Apple’s iOS has stricter safeguards in place.

The installation process may be used to avoid the chance that big tech firms remove it from app stores following pressure from the government, the exact fate that befell a Hong Kong protest organising app. It also allowed whoever developed the app to keep their identity more private than if they had published their creation through an official app store.

There’s more. To ensure the app remains in the hands of genuine protestors, rather than police or other infiltrators, users can only access it through a QR code from someone who is already a member of the network. Each person who joins receives ten QR codes to invite others.

The app also employs geolocation technology to coordinate activity. When you first download the app, you’re asked for your location (a loose estimation rather than exact coordinates). This means people can be organised in geographical “cells”, and protestors can only see actions taking place within a certain radius – preventing information from sloshing out across the network, and limiting what an infiltrator would be able to find out.

#### Read next

“Even if the police get inside this network, they will only get the notifications for one particular location,” stresses Enric Luján, a professor of Political Science who specialises in technology at the University of Barcelona.

This might mean that it will be easier to orchestrate multi-pronged protest activity. “There are going to be a lot of things going on at the same time. So I think it's going to be a really useful tool to avoid so much police repression,” says Medrano.

Why is the app important?
-------------------------

The app was first announced on Monday, October 14 and Tsunami Democràtic has suggested that something major is planned for Monday, October 21, and that the app will be helpful for those willing to partake. In a Telegram message sent on Friday, October 18, the group stressed that having the app would be useful.

Some of the app’s source code – not all of it – has been released publicly, and technologists have scoured the publicly available parts of the code for indicators about the app’s inner workings.

The app is built on top of [Retroshare](http://retroshare.cc/) – a freely available software used to construct encrypted, friend-to-friend networks (peer-to-peer networks in which users only make contact with people they personally know) to share files or communicate without relying on any central server. “In this mesh, nodes only exchange data with their connected ‘friends’, in order to maintain anonymity between non-friend nodes,” says Cyril Soler, one of Retroshare’s developers. “On top of that, Retroshare implements different techniques to allow data to be passed from node to node beyond your direct friends. That, for instance, allows the software to globally propagate distributed mail or files.”

#### Read next

While the app is decentralised in terms of nodes, experts have speculated that there might be some users who can see an overview of the app – where protestors are active and available across the city. However, whether this is the case is not clear from the publicly available code.

The decentralised nature of the network has other advantages. “These guys who are leading the movement have built a decentralised network in order to distribute the agenda, so that the police couldn't detect them as the central nodes,” says Luján.

Despite the app’s precautions, some concerns still remain. “Its traffic would be quite unusual, especially coming from mobile devices, which would probably make it easier to analyze and inspect for ISPs \[internet service providers\] – although I don't know if the authorities can legally request this kind of information from Spanish Internet Service Providers (ISP),” says Sergio Lopez, a senior software engineer at open source technology firm Red Hat, who has analysed Tsunami Democràtic’s publicly available code.

“This means that, even if the contents are encrypted, ISPs could potentially build a relationship map of nodes participating in this kind of \[friend-to-friend\] network.” It’s for this reason that other protest movements, such as the one in Hong Kong, rely on Bluetooth, thus avoiding and ISP's network.

There is a lack of consensus over how much time and effort it would have taken to create Tsunami Democràtic’s app. “This is not something developed by an activist in his or her free time,” says Luján. In contrast, Lopez suggests it may not be as complicated as it first appears. “The implementation of the F2F network, which would be the hardest part to implement, seems to be borrowed from RetroShare,” he says. “The rest is basically front-end. This could very well be done by a single developer, or a small team of them.”

#### Read next

However, there are caveats. “You also need to "bootstrap" the network, which means distributing the app, or a variant of the app to a significant amount of people, who would act as recruiters when the app is made available for everyone,” Lopez says. “These kind of logistics can't be accomplished by a single person, or a small group.”

As well as entering your location, you are also asked to enter the times when you’re available to protest. “It's like a clandestine army that you can invoke whenever and for whatever reason you want – you can decide to block one, two, three or 100 roads,” says Luján.

Okay, who is behind Tsunami Democràtic, really?
-----------------------------------------------

The organisation presents itself as an online grassroots movement, but it’s widely recognised that the app is a fairly sophisticated piece of software and the campaign is a tightly-run strategic operation.

Theories abound. “I think they're a few people, and that they're very intelligent and technically informed, like programmers,” says Medrano.

But another theory is also gaining ground. “I think it's a change of strategy of the main groups, which were involved in the first of our referendum two years ago,” says Luján. He believes that Tsunami Democràtic is a proxy group for the larger separatist organisations, and former members of the former [Catalan government](https://www.wired.co.uk/article/catalan-government-independence-internet-spain), currently residing in Brussels after fleeing the country in 2017.

#### Read next

Some of the self-exiled politicians – including president of the Generalitat, Quim Torra; its vice president, Pere Aragonès, and the president of the Parliament, Roger Torrent – have publicly supported the group on social media. Tsunami Democràtic denies any link.

Spain’s interior ministry has expressed the desire to discover who is behind the group and the app, but this will likely be difficult – given it could be set up and run from anywhere in the world.

While the movement’s chief focus is of course on Catalan independence, Tsunami Democràtic has also signalled the possibility for scope beyond this. On Github, the developers specify that it’s a platform for the organisation of peaceful civil disobedience, which could be adapted for protests in any part of the world. “It's really ambitious, because technically speaking, you could destabilise any political system you wanted,” says Luján.

#### More great stories from WIRED

**💰 Meet the economist with a [brilliant plan to fix capitalism](https://www.wired.co.uk/article/mariana-mazzucato?utm_source=More%20Stories&utm_medium=internal)**

**🎮 Long Read: [Inside Google Stadia](https://www.wired.co.uk/article/google-stadia?utm_source=More%20Stories&utm_medium=internal)**

**🎧 Expand your mind with the WIRED [guide to the best podcasts](https://www.wired.co.uk/article/best-podcasts?utm_source=More%20Stories&utm_medium=internal)**

**🤕 No-deal Brexit would [trigger a huge data problem](https://www.wired.co.uk/article/no-deal-brexit-data-adequacy-gdpr?utm_source=More%20Stories&utm_medium=internal)**

**📧 Get the [best tech deals and gadget news in your inbox](https://www.wired.co.uk/newsletters?utm_source=More%20Stories&utm_medium=internal)**

Get WIRED Weekender, your at-a-glance roundup of the most important, interesting and unusual stories from the past week. In your inbox every Saturday by 10am.

by entering your email address, you agree to our [privacy policy](https://www.condenast.co.uk/privacy/)

Thank You. You have successfully subscribed to our newsletter. You will hear from us shortly.

Sorry, you have entered an invalid email. Please refresh and try again.

  
  
from Hacker News https://ift.tt/32vBv2C