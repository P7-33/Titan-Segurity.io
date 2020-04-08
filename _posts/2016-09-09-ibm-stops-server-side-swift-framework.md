---
title: 'IBM Stops Server Side Swift Framework Development'
date: 2019-12-17T01:41:00+01:00
draft: false
---

IBM update
----------

[@IanPartridge](https://forums.swift.org/u/ianpartridge) and [@Chris\_Bailey](https://forums.swift.org/u/chris_bailey) let the group know that following a review by IBM of its open source priorities, it has been decided that they will not be continuing to work on Swift in 2020. As a result, they are both standing down from the workgroup.

[@IanPartridge](https://forums.swift.org/u/ianpartridge) will work to hand over responsibilities for the Swift Docker images and suggested a potential new owner from the community.

The workgroup thanked [@IanPartridge](https://forums.swift.org/u/ianpartridge), [@Chris\_Bailey](https://forums.swift.org/u/chris_bailey) and the rest of the IBM team for their valuable work over the years in getting Swift on server off the ground, and providing the community with reliable solutions during those early days.

Regular agenda
--------------

*   [@tanner0101](https://forums.swift.org/u/tanner0101) to publish 11/14 notes
*   Carry over action items from previous meeting,
    *   [@tanner0101](https://forums.swift.org/u/tanner0101) to test integrating of api-breakage validation into vapor libraries CI
        *   New versions of swift-pm include integration with the tool ![:tada:](https://sjc5.discourse-cdn.com/swift/images/emoji/apple/tada.png?v=9 ":tada:")
        *   [@tanner0101](https://forums.swift.org/u/tanner0101) feels the tool may be “too paranoid”, further investigation required.
    *   [@johannesweiss](https://forums.swift.org/u/johannesweiss) followed up with Apple's Foundation team about the new FoundationNetworking code portability across darwin and linux. Foundation team is considering various solutions.
    *   [@johannesweiss](https://forums.swift.org/u/johannesweiss) to start a forum discussion thread about connection-pooling given the progress on async-http-client connection pool implementation. The goal is educational / state-of-nation, not call for action for a generic connection pooling solution.
    *   [@tomerd](https://forums.swift.org/u/tomerd) to continue working on this swift-nio governance model.
    *   [@timburks](https://forums.swift.org/u/timburks) and [@tanner0101](https://forums.swift.org/u/tanner0101) reply to open-api forum post.
    *   [@tomerd](https://forums.swift.org/u/tomerd) to look into using slack for swift-server communication.
*   [@tanner0101](https://forums.swift.org/u/tanner0101) pitched SQLite and MySQL clients ![:tada:](https://sjc5.discourse-cdn.com/swift/images/emoji/apple/tada.png?v=9 ":tada:")
*   Swift support for distroless
    *   Distroless is gaining popularity for kubernetes deployments.
    *   Discussed with google's project lead in kubecone, happy to take contribution to include Swift support
    *   [@tomerd](https://forums.swift.org/u/tomerd) post a “call for action” forum post looking for community leadership on this.

  
  
from Hacker News https://ift.tt/34vMHMR