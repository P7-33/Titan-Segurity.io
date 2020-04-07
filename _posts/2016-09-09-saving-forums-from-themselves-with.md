---
title: 'Saving forums from themselves with shared hierarchical white lists (2009)'
date: 2020-01-13T06:47:00+01:00
draft: false
---

Outer Circle
============

The idea in brief
-----------------

Online forums collapse under the weight of spam, trolling and mediocre posts. Current approaches fail because they try to create a single forum, which requires agreement on what is good. Blacklisting fails because you end up playing whack-a-mole with authors you don't want to read. White listing fails because a successful forum has many posters. You could spend forever building up your white list and weeding it.

The solution is hierarchical sharing of white lists. If Albert likes Bob's posts Albert can add Bob to his white list at level zero. If Albert is impressed by Carol's judgment he can add Carol to his white list at level one. This adds Carol and the top level of her white list. If Carol's list is ((David 0) (Edgar 1) (Fred 0)) that makes Albert's direct-list ((Bob 0)(Carol 1)) and his full-list (Bob Carol David Edgar Fred).

Albert starts seeing posts by Edgar and Fred. Poking about, Albert notices that Edgar and Fred have shown good taste in assembling their white lists, so Albert bumps Carol up to level two on his own white list. Albert's direct-list reads ((Bob 0)(Carol 2)). Building his full-list is more complicated. Carol's direct-list adds David, Edgar, and Fred, but since Albert has placed Carol at level 2 we also add the direct-list of any-one that Carol has placed at level 1 or above. Since Edgar's direct list is ((George 1)(Howard 2)(Isabel 0)(Juliet 2)) that adds four names to Albert's full-list. Fred's direct list is ((Karl 1)(Lisa 2)(Murdo 3)(Norman 2)) and Albert is surprised that these haven't been added. The reason is that Carol only has Fred at level zero, and standard inheritance of white lists gets choked off by a low rating along the inheritance path.

Albert is also surprised that Carol doesn't rate Fred highly. Albert adds Fred to his direct list at level 2. Now Albert's direct-list reads ((Bob 0)(Carol 2)(Fred 2)) and his full-list reads (Bob Carol David Edgar Fred George Howard Isabel Juliet Karl Lisa Murdo Norman Oscar Paul) where Oscar has been inherited by the route Fred->Karl->Oscar and Paul by the route Fred->Murdo->Paul.

This approach answers the three objections above. Albert and Carol disagree on how to rate Fred, but this does not lead to any kind of mod-fight. They just end up with different direct lists. The problems of black listing are avoided by doing white listing. The problems of white listing are avoided by using hierarchical sharing to build white lists whose size grows exponentially with the depth of sharing.

There are other problems. In a system of threaded comments, pure white listing breaks the flow of conversation. Perhaps Carol adds Albert at level one. Now she sees Albert's reply to Paul, which Albert sees because he rates Fred highly. But Carol isn't seeing Paul's original comment. Whoops!

The basic fix is for a reply by anyone on your white list to function as a temporary endorsement of the authors up-thread. So Carol sees Paul's comment because of Alberts reply. The basic fix is too simple. Albert's reply functions as an endorsement of Paul's comment even if the content of Albert's reply is to disparage Paul's comment. The second level fix lets Albert control whether his reply is an endorsement or not. The third level fix introduces a second kind of endorsement that does not require a reply.

The original problem with white listing, that it does not include enough authors is now well under control. You not only have a large white list due to inheritance but you are seeing additional posts that those on your white list recommend. This is not entirely satisfactory. It is quite likely that you value no-reply-endorsements and do not wish to turn the feature off, and yet some of the authors you most value for their own words are promiscuous with their no-reply-endorsements. You want more finely grained control.

Another issue is variety. Posts vary in topic, quality, and seriousness. If you are a serious minded reader you may well find that the forum (meaning the personalized forum you have created with you white list) is 90% fluff. It is rather fun, but it is also too much. It would be great to turn down the recursion depth for fluff, so that one saw perhaps 50:50 serious:fluff. That depends on posters marking their posts serious or fluffy. Perhaps one doesn't really want to restrict the number of authors. One would like to read other peoples _best_ jokes. That depends on posters marking their posts best or 2nd-best. Topic also depends on posters including topic markers.

The interesting thing here is the incentives for posters who want their opinions read. The naive approach is to mark all your posts as top quality. That means that people cannot filter out your less good posts, because you haven't marked them as such. I anticipate that some participants will gain a reputation as gate keepers, maintaining large direct-lists and being on many white lists at positive levels. If one of them drops you because he thinks you are more noise than signal, you lose a lot of readers. You would have done better to be modest and guard your reputation. Indeed you can have fun posting crap and still keep your reputation as a high minded, deep thinker. All you have to do is remember to use the _crap_ tag. Those who filter out crap never see your crap posts and so never drop you from their white lists, while bored people who find your style of crap entertaining post witty or witless replies according to their talents.

The core idea of Outer Circle is shared, hierarchical white lists. Many additional user-interface details need to be filled in correctly to make Outer Circle take off. These additional user interface details are to do with tagging and fine grained control. They may be quite ordinary, requiring lots of experimentation and lots of hard work but nothing else as radical as shared, hierarchical white lists.

There are also technical details about how to write the Outer Circle protocol. This is a peer to peer application that probably needs a lot of caching that follows the sharing heir archy. It is unlikely to be simpler than Usenet. Tricky.

  
  
from Hacker News https://ift.tt/2uGZno8