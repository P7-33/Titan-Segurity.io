---
title: 'Google’s silent Chrome experiment crashes thousands of browsers and angers IT admins'
date: 2019-11-15T11:41:00+01:00
draft: false
---

![](https://cdn.vox-cdn.com/thumbor/Niqmh7PJheiWn5ZSDwjTt-Ey5BM=/0x0:2040x1360/1310x873/cdn.vox-cdn.com/uploads/chorus_image/image/65705986/acastro_180416_1777_chrome_0001.0.jpg) Illustration by Alex Castro / The Verge

Google left thousands of machines in businesses with broken Chrome browsers this week, following a silent experimental change. Business users accessing Chrome through virtual machine environments like Citrix kept seeing white screens on open Chrome tabs, blocking access to the browser and leaving it totally unresponsive. It left many IT admins confused over the problem, as businesses typically manage and control Chrome updates.

After complaints, Google was forced to reveal it had launched an "experiment" on stable versions of Chrome that had changed the browser's behavior. The experiment was made silently, without IT admins or users being warned about Google's changes. Google had simply flipped the switch on a flag to enable a new [WebContents Occlusion](https://docs.google.com/document/d/1tPuJE0Vws7oskjjqrawNfMkwFtGxyHV33yQagiplVfY/edit#heading=h.7nki9mck5t64) feature that's designed to suspend Chrome tabs when you move other apps on top of them and reduce resource usage when the browser isn't in use.

"The experiment / flag has been on in beta for ~5 months," explained David Bienvenu, a software engineer at Google, in a [Chromium bug thread](https://bugs.chromium.org/p/chromium/issues/detail?id=1024837#c52). "It was turned on for stable (e.g., m77, m78) via an experiment that was pushed to released Chrome Tuesday morning. Prior to that, it had been on for about one percent of M77 and M78 users for a month with no reports of issues, unfortunately."

![Chrome](https://cdn.vox-cdn.com/thumbor/2fCzqYjOIjCCRXKJ7ceuOTMgbyU=/400x0/filters:no_upscale()/cdn.vox-cdn.com/uploads/chorus_asset/file/6702153/chromelogo1_2040.0.jpg)

Google rolled back the change late on Thursday night, following multiple reports from businesses with thousands of users affected. "I'll rollback the launch of this experiment and try to figure out how to deal with Citrix," noted Bienvenu in the bug thread.

"This has had a huge impact for all our Call Center agents and not being able to chat with our members," explained a Costco IT admin in the Chromium thread. "We spent the last day and a half trying to figure this out."

One IT admin that alerted _The Verge_ to the issue said "we felt that this is a shady thing that Google can update Chrome silently without announcing anything and can impact 100,000+ people on a whim." Those concerns are mirrored by hundreds of replies on [Google's support forum](https://support.google.com/chrome/thread/19713332?hl=en), the bug tracker thread, and on Twitter and Reddit.

It has left IT admins angry that they've wasted valuable resources and time on trying to fix issues in their environment, and questions over why Google decided to make a silent change to Chrome in the first place. "I am stunned by your response," said one IT admin in response to Bienvenu's confirmation on the issues. "Do you see the impact you created for thousands of us without any warning or explanation? We are not your test subjects. We are running professional services for multi million dollar programs."

We've reached out to Google for comment on the Chrome issues, and we'll update you accordingly.