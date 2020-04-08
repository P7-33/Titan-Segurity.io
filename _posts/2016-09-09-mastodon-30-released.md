---
title: 'Mastodon 3.0 Released'
date: 2019-10-04T08:01:00+01:00
draft: false
---

Verified

This commit was created on GitHub.com and signed with a **verified signature** using GitHub’s key.

[![Mastodon](https://camo.githubusercontent.com/1e2208e34e0106f3bb072dbc9229771888bed973/68747470733a2f2f692e696d6775722e636f6d2f4e685a6334306c2e706e67)](https://camo.githubusercontent.com/1e2208e34e0106f3bb072dbc9229771888bed973/68747470733a2f2f692e696d6775722e636f6d2f4e685a6334306c2e706e67)

Breaking changes
----------------

*   Remove OStatus support
    *   Please use ActivityPub instead
*   Remove deprecated REST API `GET /api/v1/search` API
    *   Please use `GET /api/v2/search` instead
*   Remove deprecated REST API `GET /api/v1/statuses/:id/card`
    *   Please use the `card` attribute on statuses instead
*   Remove deprecated REST API `POST /api/v1/notifications/dismiss?id=:id`
    *   Please use `POST /api/v1/notifications/:id/dismiss` instead
*   Remove deprecated REST API `GET /api/v1/timelines/direct`
    *   Please use `GET /api/v1/conversations` instead

Changelog
---------

### Added

*   Add "not available" label to unloaded media attachments in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11715), [Gargron](https://github.com/tootsuite/mastodon/pull/11745))
*   **Add profile directory to web UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11688), [mayaeh](https://github.com/tootsuite/mastodon/pull/11872))
    *   Add profile directory opt-in federation
    *   Add profile directory REST API
*   Add special alert for throttled requests in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11677))
*   Add confirmation modal when logging out from the web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11671))
*   **Add audio player in web UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11644), [Gargron](https://github.com/tootsuite/mastodon/pull/11652), [Gargron](https://github.com/tootsuite/mastodon/pull/11654), [ThibG](https://github.com/tootsuite/mastodon/pull/11629), [Gargron](https://github.com/tootsuite/mastodon/pull/12056))
*   **Add autosuggestions for hashtags in web UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11422), [ThibG](https://github.com/tootsuite/mastodon/pull/11632), [Gargron](https://github.com/tootsuite/mastodon/pull/11764), [Gargron](https://github.com/tootsuite/mastodon/pull/11588), [Gargron](https://github.com/tootsuite/mastodon/pull/11442))
*   **Add media editing modal with OCR tool in web UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11563), [Gargron](https://github.com/tootsuite/mastodon/pull/11566), [ThibG](https://github.com/tootsuite/mastodon/pull/11575), [ThibG](https://github.com/tootsuite/mastodon/pull/11576), [Gargron](https://github.com/tootsuite/mastodon/pull/11577), [Gargron](https://github.com/tootsuite/mastodon/pull/11573), [Gargron](https://github.com/tootsuite/mastodon/pull/11571))
*   Add indicator of unread notifications to window title when web UI is out of focus ([Gargron](https://github.com/tootsuite/mastodon/pull/11560), [Gargron](https://github.com/tootsuite/mastodon/pull/11572))
*   Add indicator for which options you voted for in a poll in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11195))
*   **Add search results pagination to web UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11409), [ThibG](https://github.com/tootsuite/mastodon/pull/11447))
*   **Add option to disable real-time updates in web UI ("slow mode")** ([Gargron](https://github.com/tootsuite/mastodon/pull/9984), [ykzts](https://github.com/tootsuite/mastodon/pull/11880), [ThibG](https://github.com/tootsuite/mastodon/pull/11883), [Gargron](https://github.com/tootsuite/mastodon/pull/11898), [ThibG](https://github.com/tootsuite/mastodon/pull/11859))
*   Add option to disable blurhash previews in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11188))
*   Add native smooth scrolling when supported in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11207))
*   Add scrolling to the search bar on focus in web UI ([Kjwon15](https://github.com/tootsuite/mastodon/pull/12032))
*   Add refresh button to list of rebloggers/favouriters in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/12031))
*   Add error description and button to copy stack trace to web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/12033))
*   Add search and sort functions to hashtag admin UI ([mayaeh](https://github.com/tootsuite/mastodon/pull/11829), [Gargron](https://github.com/tootsuite/mastodon/pull/11897), [mayaeh](https://github.com/tootsuite/mastodon/pull/11875))
*   Add setting for default search engine indexing in admin UI ([brortao](https://github.com/tootsuite/mastodon/pull/11804))
*   Add account bio to account view in admin UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11473))
*   **Add option to include reported statuses in warning e-mail from admin UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11639), [Gargron](https://github.com/tootsuite/mastodon/pull/11812), [Gargron](https://github.com/tootsuite/mastodon/pull/11741), [Gargron](https://github.com/tootsuite/mastodon/pull/11698), [mayaeh](https://github.com/tootsuite/mastodon/pull/11765))
*   Add number of pending accounts and pending hashtags to dashboard in admin UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11514))
*   **Add account migration UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11846), [noellabo](https://github.com/tootsuite/mastodon/pull/11905), [noellabo](https://github.com/tootsuite/mastodon/pull/11907), [noellabo](https://github.com/tootsuite/mastodon/pull/11906), [noellabo](https://github.com/tootsuite/mastodon/pull/11902))
*   **Add table of contents to about page** ([Gargron](https://github.com/tootsuite/mastodon/pull/11885), [ykzts](https://github.com/tootsuite/mastodon/pull/11941), [ykzts](https://github.com/tootsuite/mastodon/pull/11895), [Kjwon15](https://github.com/tootsuite/mastodon/pull/11916))
*   **Add password challenge to 2FA settings, e-mail notifications** ([Gargron](https://github.com/tootsuite/mastodon/pull/11878))
*   **Add optional public list of domain blocks with comments** ([ThibG](https://github.com/tootsuite/mastodon/pull/11298), [ThibG](https://github.com/tootsuite/mastodon/pull/11515), [Gargron](https://github.com/tootsuite/mastodon/pull/11908))
*   Add an RSS feed for featured hashtags ([noellabo](https://github.com/tootsuite/mastodon/pull/10502))
*   Add explanations to featured hashtags UI and profile ([Gargron](https://github.com/tootsuite/mastodon/pull/11586))
*   **Add hashtag trends with admin and user settings** ([Gargron](https://github.com/tootsuite/mastodon/pull/11490), [Gargron](https://github.com/tootsuite/mastodon/pull/11502), [Gargron](https://github.com/tootsuite/mastodon/pull/11641), [Gargron](https://github.com/tootsuite/mastodon/pull/11594), [Gargron](https://github.com/tootsuite/mastodon/pull/11517), [mayaeh](https://github.com/tootsuite/mastodon/pull/11845), [Gargron](https://github.com/tootsuite/mastodon/pull/11774), [Gargron](https://github.com/tootsuite/mastodon/pull/11712), [Gargron](https://github.com/tootsuite/mastodon/pull/11791), [Gargron](https://github.com/tootsuite/mastodon/pull/11743), [Gargron](https://github.com/tootsuite/mastodon/pull/11740), [Gargron](https://github.com/tootsuite/mastodon/pull/11714), [ThibG](https://github.com/tootsuite/mastodon/pull/11631), [Sasha-Sorokin](https://github.com/tootsuite/mastodon/pull/11569), [Gargron](https://github.com/tootsuite/mastodon/pull/11524), [Gargron](https://github.com/tootsuite/mastodon/pull/11513))
    *   Add hashtag usage breakdown to admin UI
    *   Add batch actions for hashtags to admin UI
    *   Add trends to web UI
    *   Add trends to public pages
    *   Add user preference to hide trends
    *   Add admin setting to disable trends
*   **Add categories for custom emojis** ([Gargron](https://github.com/tootsuite/mastodon/pull/11196), [Gargron](https://github.com/tootsuite/mastodon/pull/11793), [Gargron](https://github.com/tootsuite/mastodon/pull/11920), [highemerly](https://github.com/tootsuite/mastodon/pull/11876))
    *   Add custom emoji categories to emoji picker in web UI
    *   Add `category` to custom emojis in REST API
    *   Add batch actions for custom emojis in admin UI
*   Add max image dimensions to error message ([raboof](https://github.com/tootsuite/mastodon/pull/11552))
*   Add aac, m4a, 3gp, amr, wma to allowed audio formats ([Gargron](https://github.com/tootsuite/mastodon/pull/11342), [umonaca](https://github.com/tootsuite/mastodon/pull/11687))
*   **Add search syntax for operators and phrases** ([Gargron](https://github.com/tootsuite/mastodon/pull/11411))
*   **Add REST API for managing featured hashtags** ([noellabo](https://github.com/tootsuite/mastodon/pull/11778))
*   **Add REST API for managing timeline read markers** ([Gargron](https://github.com/tootsuite/mastodon/pull/11762))
*   Add `exclude_unreviewed` param to `GET /api/v2/search` REST API ([Gargron](https://github.com/tootsuite/mastodon/pull/11977))
*   Add `reason` param to `POST /api/v1/accounts` REST API ([Gargron](https://github.com/tootsuite/mastodon/pull/12064))
*   **Add ActivityPub secure mode** ([Gargron](https://github.com/tootsuite/mastodon/pull/11269), [ThibG](https://github.com/tootsuite/mastodon/pull/11332), [ThibG](https://github.com/tootsuite/mastodon/pull/11295))
*   Add HTTP signatures to all outgoing ActivityPub GET requests ([Gargron](https://github.com/tootsuite/mastodon/pull/11284), [ThibG](https://github.com/tootsuite/mastodon/pull/11300))
*   Add support for ActivityPub Audio activities ([ThibG](https://github.com/tootsuite/mastodon/pull/11189))
*   Add ActivityPub actor representing the entire server ([ThibG](https://github.com/tootsuite/mastodon/pull/11321), [rtucker](https://github.com/tootsuite/mastodon/pull/11400), [ThibG](https://github.com/tootsuite/mastodon/pull/11561), [Gargron](https://github.com/tootsuite/mastodon/pull/11798))
*   **Add whitelist mode** ([Gargron](https://github.com/tootsuite/mastodon/pull/11291), [mayaeh](https://github.com/tootsuite/mastodon/pull/11634))
*   Add config of multipart threshold for S3 ([ykzts](https://github.com/tootsuite/mastodon/pull/11924), [ykzts](https://github.com/tootsuite/mastodon/pull/11944))
*   Add health check endpoint for web ([ykzts](https://github.com/tootsuite/mastodon/pull/11770), [ykzts](https://github.com/tootsuite/mastodon/pull/11947))
*   Add HTTP signature keyId to request log ([Gargron](https://github.com/tootsuite/mastodon/pull/11591))
*   Add `SMTP_REPLY_TO` environment variable ([hugogameiro](https://github.com/tootsuite/mastodon/pull/11718))
*   Add `tootctl preview_cards remove` command ([mayaeh](https://github.com/tootsuite/mastodon/pull/11320))
*   Add `tootctl media refresh` command ([Gargron](https://github.com/tootsuite/mastodon/pull/11775))
*   Add `tootctl cache recount` command ([Gargron](https://github.com/tootsuite/mastodon/pull/11597))
*   Add option to exclude suspended domains from `tootctl domains crawl` ([dariusk](https://github.com/tootsuite/mastodon/pull/11454))
*   Add parallelization to `tootctl search deploy` ([noellabo](https://github.com/tootsuite/mastodon/pull/12051))
*   Add soft delete for statuses for instant deletes through API ([Gargron](https://github.com/tootsuite/mastodon/pull/11623), [Gargron](https://github.com/tootsuite/mastodon/pull/11648))
*   Add rails-level JSON caching ([Gargron](https://github.com/tootsuite/mastodon/pull/11333), [Gargron](https://github.com/tootsuite/mastodon/pull/11271))
*   **Add request pool to improve delivery performance** ([Gargron](https://github.com/tootsuite/mastodon/pull/10353), [ykzts](https://github.com/tootsuite/mastodon/pull/11756))
*   Add concurrent connection attempts to resolved IP addresses ([ThibG](https://github.com/tootsuite/mastodon/pull/11757))
*   Add index for remember\_token to improve login performance ([abcang](https://github.com/tootsuite/mastodon/pull/11881))
*   **Add more accurate hashtag search** ([Gargron](https://github.com/tootsuite/mastodon/pull/11579), [Gargron](https://github.com/tootsuite/mastodon/pull/11427), [Gargron](https://github.com/tootsuite/mastodon/pull/11448))
*   **Add more accurate account search** ([Gargron](https://github.com/tootsuite/mastodon/pull/11537), [Gargron](https://github.com/tootsuite/mastodon/pull/11580))
*   **Add a spam check** ([Gargron](https://github.com/tootsuite/mastodon/pull/11217), [Gargron](https://github.com/tootsuite/mastodon/pull/11806), [ThibG](https://github.com/tootsuite/mastodon/pull/11296))
*   Add new languages ([Gargron](https://github.com/tootsuite/mastodon/pull/12062))
    *   Breton
    *   Spanish (Argentina)
    *   Estonian
    *   Macedonian
    *   New Norwegian
*   Add NodeInfo endpoint ([Gargron](https://github.com/tootsuite/mastodon/pull/12002), [Gargron](https://github.com/tootsuite/mastodon/pull/12058))

### Changed

*   **Change conversations UI** ([Gargron](https://github.com/tootsuite/mastodon/pull/11896))
*   Change dashboard to short number notation ([noellabo](https://github.com/tootsuite/mastodon/pull/11847), [noellabo](https://github.com/tootsuite/mastodon/pull/11911))
*   Change REST API `GET /api/v1/timelines/public` to require authentication when public preview is off ([ThibG](https://github.com/tootsuite/mastodon/pull/11802))
*   Change REST API `POST /api/v1/follow_requests/:id/(approve|reject)` to return relationship ([ThibG](https://github.com/tootsuite/mastodon/pull/11800))
*   Change rate limit for media proxy ([ykzts](https://github.com/tootsuite/mastodon/pull/11814))
*   Change unlisted custom emoji to not appear in autosuggestions ([Gargron](https://github.com/tootsuite/mastodon/pull/11818))
*   Change max length of media descriptions from 420 to 1500 characters ([Gargron](https://github.com/tootsuite/mastodon/pull/11819), [ThibG](https://github.com/tootsuite/mastodon/pull/11836))
*   **Change deletes to preserve soft-deleted statuses in unresolved reports** ([Gargron](https://github.com/tootsuite/mastodon/pull/11805))
*   **Change tootctl to use inline parallelization instead of Sidekiq** ([Gargron](https://github.com/tootsuite/mastodon/pull/11776))
*   **Change account deletion page to have better explanations** ([Gargron](https://github.com/tootsuite/mastodon/pull/11753), [Gargron](https://github.com/tootsuite/mastodon/pull/11763))
*   Change hashtag component in web UI to show numbers for 2 last days ([Gargron](https://github.com/tootsuite/mastodon/pull/11742), [Gargron](https://github.com/tootsuite/mastodon/pull/11755), [Gargron](https://github.com/tootsuite/mastodon/pull/11754))
*   Change OpenGraph description on sign-up page to reflect invite ([Gargron](https://github.com/tootsuite/mastodon/pull/11744))
*   Change layout of public profile directory to be the same as in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11705))
*   Change detailed status child ordering to sort self-replies on top ([ThibG](https://github.com/tootsuite/mastodon/pull/11686))
*   Change window resize handler to switch to/from mobile layout as soon as needed ([ThibG](https://github.com/tootsuite/mastodon/pull/11656))
*   Change icon button styles to make hover/focus states more obvious ([ThibG](https://github.com/tootsuite/mastodon/pull/11474))
*   Change contrast of status links that are not mentions or hashtags ([ThibG](https://github.com/tootsuite/mastodon/pull/11406))
*   **Change hashtags to preserve first-used casing** ([Gargron](https://github.com/tootsuite/mastodon/pull/11416), [Gargron](https://github.com/tootsuite/mastodon/pull/11508), [Gargron](https://github.com/tootsuite/mastodon/pull/11504), [Gargron](https://github.com/tootsuite/mastodon/pull/11507), [Gargron](https://github.com/tootsuite/mastodon/pull/11441))
*   **Change unconfirmed user login behaviour** ([Gargron](https://github.com/tootsuite/mastodon/pull/11375), [ThibG](https://github.com/tootsuite/mastodon/pull/11394), [Gargron](https://github.com/tootsuite/mastodon/pull/11860))
*   **Change single-column mode to scroll the whole page** ([Gargron](https://github.com/tootsuite/mastodon/pull/11359), [Gargron](https://github.com/tootsuite/mastodon/pull/11894), [Gargron](https://github.com/tootsuite/mastodon/pull/11891), [ThibG](https://github.com/tootsuite/mastodon/pull/11655), [Gargron](https://github.com/tootsuite/mastodon/pull/11463), [Gargron](https://github.com/tootsuite/mastodon/pull/11458), [ThibG](https://github.com/tootsuite/mastodon/pull/11395), [Gargron](https://github.com/tootsuite/mastodon/pull/11418))
*   Change `tootctl accounts follow` to only work with local accounts ([angristan](https://github.com/tootsuite/mastodon/pull/11592))
*   Change Dockerfile ([Shleeble](https://github.com/tootsuite/mastodon/pull/11710), [ykzts](https://github.com/tootsuite/mastodon/pull/11768), [Shleeble](https://github.com/tootsuite/mastodon/pull/11707))
*   Change supported Node versions to include v12 ([abcang](https://github.com/tootsuite/mastodon/pull/11706))
*   Change Portuguese language from `pt` to `pt-PT` ([Gargron](https://github.com/tootsuite/mastodon/pull/11820))
*   Change domain block silence to always require approval on follow ([ThibG](https://github.com/tootsuite/mastodon/pull/11975))
*   Change link preview fetcher to not perform a HEAD request first ([Gargron](https://github.com/tootsuite/mastodon/pull/12028))
*   Change `tootctl domains purge` to accept multiple domains at once ([Gargron](https://github.com/tootsuite/mastodon/pull/12046))

### Removed

*   **Remove OStatus support** ([Gargron](https://github.com/tootsuite/mastodon/pull/11205), [Gargron](https://github.com/tootsuite/mastodon/pull/11303), [Gargron](https://github.com/tootsuite/mastodon/pull/11460), [ThibG](https://github.com/tootsuite/mastodon/pull/11280), [ThibG](https://github.com/tootsuite/mastodon/pull/11278))
*   Remove Atom feeds and old URLs in the form of `GET /:username/updates/:id` ([Gargron](https://github.com/tootsuite/mastodon/pull/11247))
*   Remove WebP support ([angristan](https://github.com/tootsuite/mastodon/pull/11589))
*   Remove deprecated config options from Heroku and Scalingo ([ykzts](https://github.com/tootsuite/mastodon/pull/11925))
*   Remove deprecated REST API `GET /api/v1/search` API ([Gargron](https://github.com/tootsuite/mastodon/pull/11823))
*   Remove deprecated REST API `GET /api/v1/statuses/:id/card` ([Gargron](https://github.com/tootsuite/mastodon/pull/11213))
*   Remove deprecated REST API `POST /api/v1/notifications/dismiss?id=:id` ([Gargron](https://github.com/tootsuite/mastodon/pull/11214))
*   Remove deprecated REST API `GET /api/v1/timelines/direct` ([Gargron](https://github.com/tootsuite/mastodon/pull/11212))

### Fixed

*   Fix manifest warning ([ykzts](https://github.com/tootsuite/mastodon/pull/11767))
*   Fix admin UI for custom emoji not respecting GIF autoplay preference ([ThibG](https://github.com/tootsuite/mastodon/pull/11801))
*   Fix page body not being scrollable in admin/settings layout ([Gargron](https://github.com/tootsuite/mastodon/pull/11893))
*   Fix placeholder colors for inputs not being explicitly defined ([Gargron](https://github.com/tootsuite/mastodon/pull/11890))
*   Fix incorrect enclosure length in RSS ([tsia](https://github.com/tootsuite/mastodon/pull/11889))
*   Fix TOTP codes not being filtered from logs during enabling/disabling ([Gargron](https://github.com/tootsuite/mastodon/pull/11877))
*   Fix webfinger response not returning 410 when account is suspended ([Gargron](https://github.com/tootsuite/mastodon/pull/11869))
*   Fix ActivityPub Move handler queuing jobs that will fail if account is suspended ([Gargron](https://github.com/tootsuite/mastodon/pull/11864))
*   Fix SSO login not using existing account when e-mail is verified ([Gargron](https://github.com/tootsuite/mastodon/pull/11862))
*   Fix web UI allowing uploads past status limit via drag & drop ([Gargron](https://github.com/tootsuite/mastodon/pull/11863))
*   Fix expiring polls not being displayed as such in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11835))
*   Fix 2FA challenge and password challenge for non-database users ([Gargron](https://github.com/tootsuite/mastodon/pull/11831), [Gargron](https://github.com/tootsuite/mastodon/pull/11943))
*   Fix profile fields overflowing page width in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11828))
*   Fix web push subscriptions being deleted on rate limit or timeout ([Gargron](https://github.com/tootsuite/mastodon/pull/11826))
*   Fix display of long poll options in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11717), [ThibG](https://github.com/tootsuite/mastodon/pull/11833))
*   Fix search API not resolving URL when `type` is given ([Gargron](https://github.com/tootsuite/mastodon/pull/11822))
*   Fix hashtags being split by ZWNJ character ([Gargron](https://github.com/tootsuite/mastodon/pull/11821))
*   Fix scroll position resetting when opening media modals in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11815))
*   Fix duplicate HTML IDs on about page ([ThibG](https://github.com/tootsuite/mastodon/pull/11803))
*   Fix admin UI showing superfluous reject media/reports on suspended domain blocks ([ThibG](https://github.com/tootsuite/mastodon/pull/11749))
*   Fix ActivityPub context not being dynamically computed ([ThibG](https://github.com/tootsuite/mastodon/pull/11746))
*   Fix Mastodon logo style on hover on public pages' footer ([ThibG](https://github.com/tootsuite/mastodon/pull/11735))
*   Fix height of dashboard counters ([ThibG](https://github.com/tootsuite/mastodon/pull/11736))
*   Fix custom emoji animation on hover in web UI directory bios ([ThibG](https://github.com/tootsuite/mastodon/pull/11716))
*   Fix non-numbers being passed to Redis and causing an error ([Gargron](https://github.com/tootsuite/mastodon/pull/11697))
*   Fix error in REST API for an account's statuses ([Gargron](https://github.com/tootsuite/mastodon/pull/11700))
*   Fix uncaught error when resource param is missing in Webfinger request ([Gargron](https://github.com/tootsuite/mastodon/pull/11701))
*   Fix uncaught domain normalization error in remote follow ([Gargron](https://github.com/tootsuite/mastodon/pull/11703))
*   Fix uncaught 422 and 500 errors ([Gargron](https://github.com/tootsuite/mastodon/pull/11590), [Gargron](https://github.com/tootsuite/mastodon/pull/11811))
*   Fix uncaught parameter missing exceptions and missing error templates ([Gargron](https://github.com/tootsuite/mastodon/pull/11702))
*   Fix encoding error when checking e-mail MX records ([Gargron](https://github.com/tootsuite/mastodon/pull/11696))
*   Fix items in StatusContent render list not all having a key ([ThibG](https://github.com/tootsuite/mastodon/pull/11645))
*   Fix remote and staff-removed statuses leaving media behind for a day ([Gargron](https://github.com/tootsuite/mastodon/pull/11638))
*   Fix CSP needlessly allowing blob URLs in script-src ([ThibG](https://github.com/tootsuite/mastodon/pull/11620))
*   Fix ignoring whole status because of one invalid hashtag ([Gargron](https://github.com/tootsuite/mastodon/pull/11621))
*   Fix hidden statuses losing focus ([ThibG](https://github.com/tootsuite/mastodon/pull/11208))
*   Fix loading bar being obscured by other elements in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11598))
*   Fix multiple issues with replies collection for pages further than self-replies ([ThibG](https://github.com/tootsuite/mastodon/pull/11582))
*   Fix blurhash and autoplay not working on public pages ([Gargron](https://github.com/tootsuite/mastodon/pull/11585))
*   Fix 422 being returned instead of 404 when POSTing to unmatched routes ([Gargron](https://github.com/tootsuite/mastodon/pull/11574), [Gargron](https://github.com/tootsuite/mastodon/pull/11704))
*   Fix client-side resizing of image uploads ([ThibG](https://github.com/tootsuite/mastodon/pull/11570))
*   Fix short number formatting for numbers above million in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11559))
*   Fix ActivityPub and REST API queries setting cookies and preventing caching ([ThibG](https://github.com/tootsuite/mastodon/pull/11539), [ThibG](https://github.com/tootsuite/mastodon/pull/11557), [ThibG](https://github.com/tootsuite/mastodon/pull/11336), [ThibG](https://github.com/tootsuite/mastodon/pull/11331))
*   Fix some emojis in profile metadata labels are not emojified. ([kedamaDQ](https://github.com/tootsuite/mastodon/pull/11534))
*   Fix account search always returning exact match on paginated results ([Gargron](https://github.com/tootsuite/mastodon/pull/11525))
*   Fix acct URIs with IDN domains not being resolved ([Gargron](https://github.com/tootsuite/mastodon/pull/11520))
*   Fix admin dashboard missing latest features ([Gargron](https://github.com/tootsuite/mastodon/pull/11505))
*   Fix jumping of toot date when clicking spoiler button ([ariasuni](https://github.com/tootsuite/mastodon/pull/11449))
*   Fix boost to original audience not working on mobile in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11371))
*   Fix handling of webfinger redirects in ResolveAccountService ([ThibG](https://github.com/tootsuite/mastodon/pull/11279))
*   Fix URLs appearing twice in errors of ActivityPub::DeliveryWorker ([Gargron](https://github.com/tootsuite/mastodon/pull/11231))
*   Fix support for HTTP proxies ([ThibG](https://github.com/tootsuite/mastodon/pull/11245))
*   Fix HTTP requests to IPv6 hosts ([ThibG](https://github.com/tootsuite/mastodon/pull/11240))
*   Fix error in ElasticSearch index import ([mayaeh](https://github.com/tootsuite/mastodon/pull/11192))
*   Fix duplicate account error when seeding development database ([ysksn](https://github.com/tootsuite/mastodon/pull/11366))
*   Fix performance of session clean-up scheduler ([abcang](https://github.com/tootsuite/mastodon/pull/11871))
*   Fix older migrations not running ([zunda](https://github.com/tootsuite/mastodon/pull/11377))
*   Fix URLs counting towards RTL detection ([ahangarha](https://github.com/tootsuite/mastodon/pull/11759))
*   Fix unnecessary status re-rendering in web UI ([ThibG](https://github.com/tootsuite/mastodon/pull/11211))
*   Fix http\_parser.rb gem not being compiled when no network available ([petabyteboy](https://github.com/tootsuite/mastodon/pull/11444))
*   Fix muted text color not applying to all text ([trwnh](https://github.com/tootsuite/mastodon/pull/11996))
*   Fix follower/following lists resetting on back-navigation in web UI ([Gargron](https://github.com/tootsuite/mastodon/pull/11986))
*   Fix n+1 query when approving multiple follow requests ([abcang](https://github.com/tootsuite/mastodon/pull/12004))
*   Fix records not being indexed into ElasticSearch sometimes ([Gargron](https://github.com/tootsuite/mastodon/pull/12024))
*   Fix needlessly indexing unsearchable statuses into ElasticSearch ([Gargron](https://github.com/tootsuite/mastodon/pull/12041))
*   Fix new user bootstrapping crashing when to-be-followed accounts are invalid ([ThibG](https://github.com/tootsuite/mastodon/pull/12037))
*   Fix featured hashtag URL being interpreted as media or replies tab ([Gargron](https://github.com/tootsuite/mastodon/pull/12048))
*   Fix account counters being overwritten by parallel writes ([Gargron](https://github.com/tootsuite/mastodon/pull/12045))

### Security

*   Fix performance of GIF re-encoding and always strip EXIF data from videos ([Gargron](https://github.com/tootsuite/mastodon/pull/12057))

Upgrade notes
-------------

> As always, **make sure you have backups of the database before performing any upgrades**. If you are using docker-compose, this is how a backup command might look: docker exec mastodon\_db\_1 pg\_dump -Fc -U postgres postgres > name\_of\_the\_backup.dump

**Non-Docker only:**

*   The recommended Ruby version has been bumped to 2.6.5. You can upgrade, or you can continue using the old version by overwriting the `.ruby-version` file with e.g. `2.6.1` or `2.5.3` which were recommended previously
*   Install dependencies: `bundle install` and `yarn install`

**Both Docker and non-Docker:**

1.  Run the _pre-deployment_ database migrations by specifying the `SKIP_POST_DEPLOYMENT_MIGRATIONS=true` environment variable:
    *   Non-Docker: `SKIP_POST_DEPLOYMENT_MIGRATIONS=true RAILS_ENV=production bundle exec rails db:migrate`
    *   Docker: `docker-compose run --rm -e SKIP_POST_DEPLOYMENT_MIGRATIONS=true web rails db:migrate`
2.  Precompile the assets:
    *   Non-Docker: `RAILS_ENV=production bundle exec rails assets:precompile`
    *   Docker: The assets are already precompiled during the build step
3.  Restart all Mastodon processes
4.  Clear cache:
    *   Non-Docker: `RAILS_ENV=production bin/tootctl cache clear`
    *   Docker: `docker-compose run --rm web bin/tootctl cache clear`
5.  Now that the new code is running, we can finish the database migrations. This will run the _post-deployment_ ones:
    *   Non-Docker: `RAILS_ENV=production bundle exec rails db:migrate`
    *   Docker: `docker-compose run --rm web rails db:migrate`
6.  Restart all Mastodon processes
7.  If you are using ElasticSearch, there are new indices to be deployed (**this step is likely to take a considerable amount of time**, so running it through `screen` or `tmux` is advisable):
    *   Non-Docker: `RAILS_ENV=production bin/tootctl search deploy`
    *   Docker: `docker-compose run --rm web bin/tootctl search deploy`

Translators
-----------

*   Zoltán Gera (_Hungarian_)
*   Kristijan Tkalec (_Slovenian_)
*   Evert Prants (_Estonian_)
*   borys\_sh (_Ukrainian_)
*   Muha Aliss (_Turkish_)
*   唐宗勛 (_Chinese Simplified_)
*   oɹʇuʞ (_Spanish, Argentina_)
*   Jeong Arm (_Korean; Esperanto; Japanese_)
*   ButterflyOfFire (_French; Arabic_)
*   Roboron (_Spanish_)
*   Osoitz (_Basque_)
*   Ramdziana F Y (_Indonesian_)
*   Alix Rossi (_Corsican; French_)
*   Aditoo17 (_Czech_)
*   Masoud Abkenar (_Persian_)
*   koyu (_German_)
*   spla (_Catalan_)
*   Maya Minatsuki (_Japanese_)
*   Oguz Ersen (_Turkish_)
*   Xosé M. (_Galician_)
*   Jeroen (_Dutch_)
*   Marek Ľach (_Slovak; Polish_)
*   d5Ziif3K (_Ukrainian_)
*   Thai Localization (_Thai_)
*   lamnatos (_Greek_)
*   Diluns (_Occitan_)
*   atarashiako (_Chinese Simplified_)
*   101010 (_Polish_)
*   Yi-Jyun Pan (_Chinese Traditional_)
*   silkevicious (_Italian_)
*   FédiQuébec (_French_)
*   Jaz-Michael King (_Welsh_)
*   tykayn(_French_)
*   Alessandro Levati (_Italian_)
*   carolinagiorno (_Portuguese, Brazilian_)
*   taoxvx (_Danish_)
*   shioko (_Chinese Simplified_)
*   Emyn Nant Nefydd (_Welsh_)
*   Sasha Sorokin (_Russian_)
*   Tiago Epifânio (_Portuguese_)
*   dxwc (_Bengali_)
*   liffon (_Swedish_)
*   Evgeny Petrov (_Russian_)
*   Vanege (_Esperanto_)
*   Johan Schiff (_Swedish_)
*   kat (_Ukrainian; Russian_)
*   oti4500 (_Hungarian; Ukrainian_)
*   Juan José Salvador Piedra (_Spanish_)
*   diazepan (_Spanish_)
*   SHeija (_Finnish_)
*   christalleras (_Norwegian Nynorsk_)
*   Jack R (_Spanish_)
*   Saederup92 (_Danish_)
*   sabri (_Spanish_)
*   Stasiek Michalski (_Polish_)
*   Dewi (_Breton; French_)
*   ariasuni (_French; Esperanto_)
*   AW Unad (_Indonesian_)
*   cybergene (_Japanese_)
*   Andrea Lo Iacono (_Italian_)
*   Ray (_Spanish_)
*   Unmual (_Spanish_)
*   Ryo (_Korean_)
*   juanda097 (_Spanish_)
*   Anunnakey (_Macedonian_)
*   Cutls (_Japanese_)
*   ruine (_Japanese_)
*   MadeInSteak (_Finnish_)
*   Sokratis Alichanidis (_Greek_)
*   dragnucs2 (_Arabic_)
*   frumble (_German_)
*   erikstl (_Esperanto_)
*   Rikard Linde (_Swedish_)
*   PPNplus (_Thai_)
*   EPEMA YT (_German_)
*   Rhys Harrison (_Esperanto_)
*   KEINOS (_Japanese_)
*   JzshAC (_Chinese Simplified_)
*   Rintan1 (_Japanese_)
*   hiphipvargas (_Portuguese_)
*   Ch. (_Korean_)
*   tctovsli (_Norwegian Nynorsk_)
*   vjasiegd (_Polish_)
*   SamitiMed (_Thai_)
*   umelard (_Hebrew_)
*   硫酸鶏 (_Japanese_)
*   Adrián Lattes (_Spanish_)
*   Hinaloe (_Japanese_)
*   Renato "Lond" Cerqueira (_Portuguese, Brazilian_)
*   Marcin Mikołajczak (_Polish_)
*   filippodb (_Italian_)
*   森の子リスのミーコの大冒険 (_Japanese_)
*   Sahak Petrosyan (_Armenian_)
*   Marcepanek\_ (_Polish_)
*   Daniel Dimitrov (_Bulgarian_)
*   Hugh Liu (_Chinese Simplified_)
*   Rakino (_Chinese Simplified_)
*   hussama (_Portuguese, Brazilian_)
*   eichkat3r (_German_)
*   SnDer (_Dutch_)
*   Karol Kosek (_Polish_)
*   Akarshan Biswas (_Bengali_)
*   Tradjincal (_French_)
*   sergioaraujo1 (_Portuguese, Brazilian_)
*   mmokhi (_Persian_)
*   skaaarrr (_German_)
*   Lukas Fülling (_German_)
*   JackXu (_Chinese Simplified_)
*   Zoé Bőle (_German_)
*   Dremski (_Bulgarian_)
*   OpenAlgeria (_Arabic_)
*   waweic (_German_)
*   Benjamin Cobb (_German_)
*   さっかりんにーさん (_Japanese_)
*   Abijeet Patro (_Basque_)

You can’t perform that action at this time.

You signed in with another tab or window. [Reload](https://github.com/tootsuite/mastodon/releases/tag/v3.0.0) to refresh your session. You signed out in another tab or window. [Reload](https://github.com/tootsuite/mastodon/releases/tag/v3.0.0) to refresh your session.

  
  
from Hacker News https://ift.tt/2OfclRA