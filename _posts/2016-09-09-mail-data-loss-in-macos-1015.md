---
title: 'Mail Data Loss in macOS 10.15'
date: 2019-10-12T01:13:00+01:00
draft: false
---

I’m working on more posts about the Catalina release, but I wanted to start with a short warning. I’ve heard a bunch of reports of data loss in Apple Mail. Thankfully, none seem to be caused by [my apps](https://c-command.com/blog/2019/10/08/macos-10-15-catalina-compatibility/). (Ironically, one of the bugs I’ve encountered is the _inability_ to delete messages via AppleScript.) And, in fact, most of the damage has occurred without my Mail plug-in even being installed. Nevertheless, people contact me because it’s not unreasonable to wonder if third-party software is to blame, and I also hear from people who want a second opinion because what Apple support told them didn’t make sense.

What I’m hearing:

*   Updating Mail’s data store from Mojave to Catalina sometimes says that it succeeded, but large numbers of messages turn out to be missing or incomplete.
    
*   Moving messages between mailboxes, both via drag-and-drop and AppleScript, can result in a blank message (only headers) on the Mac. If the message was moved to a server mailbox, other devices see the message as deleted. And eventually this syncs back to the first Mac, where the message disappears as well.
    

I don’t know whether these are due to Mail bugs or to other factors such as problems on the Mac or with the mail server. But my advice is to hold off on updating to Catalina for now. These sorts of issues are pernicious because:

1.  You may not notice that anything is wrong unless you are looking at the particular mailbox or messages that are affected.
    
2.  Because the data is synced to the server, problems can propagate to other Macs and iOS devices.
    
3.  Making a backup is difficult because, even if you set the preference, Mail no longer automatically fully downloads all messages. So the backup of the [local data](https://mjtsai.com/blog/2019/09/26/what-time-machine-doesnt-back-up/) will necessarily be incomplete. (See EagleFiler’s [Importing Attachments](https://c-command.com/eaglefiler/help/importing-mail-from-app) instructions for more about this. I’m happy to have most of my mail archived outside of Mail.)
    
4.  Restoring a backup is difficult because Mail data is constantly changing. There is no straightforward way to merge restored data in with messages received since the last backup, and also with the live data on the server.

Of course, it’s good to make backups anyway.

Apple advisors are apparently telling customers that if Mail data gets lost on Catalina, it can’t be recovered from a Time Machine backup that was made using Mojave. This didn’t make sense to me, and I’ve verified that it’s not the case. You can use Time Machine to get at previous versions of the folders in Mail’s data store, and then use the **File ‣ Import Mailboxes…** command to selectively import them into Catalina Mail. Since they import as new, local mailboxes, this shouldn’t affect messages that are on the server.

I also think that the advice to restore the whole Mac to Mojave makes no sense because as soon as you launch Mail it’s going to delete all the messages that were deleted on the server. In order to actually restore them, you have to make _copies_ of the messages that might have already been deleted. That’s what **Import Mailboxes** does.

[Apple Mail](https://mjtsai.com/blog/tag/applemail/) [AppleCare](https://mjtsai.com/blog/tag/applecare/) [AppleScript](https://mjtsai.com/blog/tag/applescript/) [Backup](https://mjtsai.com/blog/tag/backup/) [Bug](https://mjtsai.com/blog/tag/bug/) [Datacide](https://mjtsai.com/blog/tag/datacide/) [E-mail Client](https://mjtsai.com/blog/tag/emailclient/) [EagleFiler](https://mjtsai.com/blog/tag/eaglefiler/) [IMAP](https://mjtsai.com/blog/tag/imap/) [iOS](https://mjtsai.com/blog/tag/ios/) [iOS 13](https://mjtsai.com/blog/tag/ios-13/) [Mac](https://mjtsai.com/blog/tag/mac/) [macOS 10.15 Catalina](https://mjtsai.com/blog/tag/macos-10-15/) [Microsoft Exchange](https://mjtsai.com/blog/tag/microsoft-exchange/) [MobileMail](https://mjtsai.com/blog/tag/mobilemail/) [SpamSieve](https://mjtsai.com/blog/tag/spamsieve/) [Time Machine](https://mjtsai.com/blog/tag/timemachine/)

Stay up-to-date by subscribing to the [Comments RSS Feed](https://mjtsai.com/blog/2019/10/11/mail-data-loss-in-macos-10-15/feed/) for this post.

### Leave a Comment

  
  
from Hacker News https://ift.tt/3199RXZ