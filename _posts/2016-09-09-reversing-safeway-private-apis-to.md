---
title: 'Reversing Safeway''s private APIs to automate coupon collection'
date: 2019-10-15T07:04:00+01:00
draft: false
---

Safeway is an American supermarket chain that has historically had a pretty comprehensive coupon program. They have recently tried to modernize their offerings (as they were founded in 1915, and are pretty much the definition of “old guard” companies), which brought what used to be a painstaking process of clipping coupons from magazines to the slightly less painful process of having to click “Add” on all the coupons every week after logging onto their site.

I’m not particularly invested in couponing, but figured with so many coupons offered and how often I need to get groceries, if I were to completely automate the process of “adding” coupons to my account it would be worthwhile in the long run, or at the very least provide for an interesting afternoon.

Background
----------

You’re able to automatically add coupons to your Safeway account (“just for U”) online at `https://www.safeway.com/justforu/coupons-deals.html`. The page is built in Angular, and was built in production mode (which means no easy Angular devtools inspections).

![Safeway offers](https://blog.jonlu.ca/images/safeway_offers.png)

When you navigate to the coupon page you see 30 coupons. At the bottom there is a “Load more” button, which will load an additional 30 coupons.

![Safeway add](https://blog.jonlu.ca/images/safeway_add.png)

Getting all the coupons
-----------------------

The coupon page makes a request to `https://www.safeway.com/abs/pub/web/j4u/api/ecomgallery?offerPgm=PD-CC&storeId=3031&transformOfferbyUpc=y` if it’s your first time on the site, and stores them in localstorage on subsequent requests. Unfortunately this is not an open URL, so you’ll need to have a valid API key (that is included in the first authenticated request to the page) to be able to access it.

![Safeway Coupons](https://blog.jonlu.ca/images/safeway_comp.png)

Each of these coupons have specific information related to it:

```
{  "offerId":  "1769990482",  "priceType":  "88",  "image":  "https://www.safeway.com/CMS/j4u/offers/images/5_dollars_off.gif",  "offerPrice":  "$5 OFF",  "description":  "*Standard exclusions apply.",  "status":  "U",  "startDate":  "1570644000000",  "endDate":  "10/15/2019",  "offerTs":  "1570554250722",  "usageType":  "O",  "offerPgm":  "PD",  "purchaseInd":  "B",  "extlOfferId":  "2588K4119_760013",  "offerProvider":  "NextGenAutoLoadStoreCpns",  "imageId":  "5_dollars_off.gif",  "hierarchies":  {  "categories":  [  "Special Offers"  ],  "events":  []  },  "name":  "$5 Off Your Purchase of $50 or More",  "offerID":  "1769990482",  "disclaimer":  "Save $5 when you spend $50 or more in qualifying purchases in a single transaction using your just for U® account ($50 minimum purchase calculated after deduction of promotional and loyalty card savings, coupons and all other discounts, offers and savings). Offer is valid 10/09/2019 - 10/15/2019 only at participating Safeway stores located in Northern California and Western Nevada. Qualifying purchases exclude: alcoholic beverages, tobacco products, fluid dairy, fuel, prescription items and co-payments, fishing/hunting licenses and tags, postage stamps, money orders/transfers, bus/commuter passes, amusement park/ski/event/lottery tickets, phone cards, gift cards/certificates and applicable taxes, bottle/container deposits and bag fees.",  "priceTitle":  "Special Offer",  "limits":  "O",  "categoryType":  "Special Offers",  "purchaseRank":  "2",  "arrivalRank":  "16",  "expiryRank":  "16",  "deleted":  false,  "category":  "Special Offers",  "events":  [],  "offerType":  "PD",  "isGroupSplit":  true,  "updBtnText":  "Added",  "updBtnMode":  true,  "usageTypeTxt":  "One time use",  "couponID":  "1769990482",  "brand":  "$5 Off Your Purchase of $50 or More",  "newOfferPrice":  "Special Offer $5 OFF",  "refineBrand":  "$5 Off Your Purchase of $50 or More",  "refineDescription":  "*Standard exclusions apply."  } 
```

There would be two paths forward to make this automatable - either go through the sign in procedure in a headless browser like `puppeteer`, and then just dump `localStorage.getItem('abCoupons')`, like so:

![Safeway local storage](https://blog.jonlu.ca/images/safeway_local.png)

The other way would be to reverse their authentication route and make the request directly using raw requests. Once we get the API token, then we can make requests directly to the above endpoint. This would be a much more reproducible (and faster) way of accomplishing the goal, so we’ll stick to this way.

First we’ll explore how to add coupons to our account, and then connect it all together to make it fully automated.

Adding a coupon to your account
-------------------------------

Fortunately reversing the add coupon functionality is fairly trivial. Clicking “Add” fires off a `POST` request to `https://www.safeway.com/abs/pub/web/j4u/api/offers/clip` with `storeId` as a URL parameter.

![Safeway add coupon](https://blog.jonlu.ca/images/safeway_add_coupon.png)

The body of the request is, interestingly enough, the same ID with two `clipType`s. I’m not entirely sure what `C` and `L` stand for, but it seems they’re the same for any coupon type or category.

```
{  "items":  [  {  "clipType":  "C",  "itemId":  "169451067",  "itemType":  "PD"  },  {  "clipType":  "L",  "itemId":  "169451067",  "itemType":  "PD"  }  ]  } 
```

From here it’s easy to convert the request into code. My preferred way is to right click -> Copy as cURL, then use a tool like [curlconverter](https://curl.trillworks.com/) to turn it into python:

```
import requests cookies = { 'abc': 'abc', # Cookies omitted due to session } headers = { # headers omitted due to session } params = ( ('storeId', 'my_store_id'), ) data = '{"items":[{"clipType":"C","itemId":"836190395","itemType":"PD"},{"clipType":"L","itemId":"836190395","itemType":"PD"}]}' response = requests.post('https://www.safeway.com/abs/pub/web/j4u/api/offers/clip', headers=headers, params=params, cookies=cookies, data=data) 
```

After playing around with it, I figured out that you only needed two headers, and _none of the cookies_, to successfully add a coupon to your account - the `SWY_SSO_TOKEN` header, and `'Content-Type': 'application/json'` to designate the content type of the request.

`SWY_SSO_TOKEN` is actually a [jwt](https://jwt.io/) with the following format:

```
{  "ver":  1,  "jti":  "",  "iss":  "https://albertsons.okta.com/oauth2/",  "aud":  "Albertsons",  "iat":  1570908253,  "exp":  1570910953,  "cid":  "",  "uid":  "",  "scp":  [  "used_credentials",  "offline_access",  "openid",  "email",  "profile"  ],  "zip":  "",  "sub":  "",  "hid":  "",  "dnm":  "",  "aln":  "",  "gid":  "",  "ecc":  "",  "fnm":  "",  "lnm":  "",  "uuid":  "",  "jpr":  "",  "ban":  "safeway",  "str":  "",  "phn":  "",  "bid":  ""  } 
```

We can’t construct our own JWTs as we don’t have their signing secret, but it’s interesting nonetheless.

Cleaning up the code a little and it looks like this:

```
import requests def add_coupon_by_id(id, store_id, type): headers = { 'SWY_SSO_TOKEN': ' jwt', 'Content-Type': 'application/json', } params = ( ('storeId', store_id), ) t = Template('{"items":[{"clipType":"C","itemId":"${id}","itemType":"${type}"},{"clipType":"L","itemId":"${id}","itemType":"${type}"}]}') data = t.substitute(id=str(id), type=str(type)) response = requests.post('https://www.safeway.com/abs/pub/web/j4u/api/offers/clip', headers=headers, params=params, data=data) print(response.status_code) add_coupon_by_id(836190395, 0) 
```

This looks like an atomic action, and calling clip multiple times doesn’t perform any state changes.

Adding all coupons
------------------

To start I just dumped the JSON object containing all the coupon offers into the test python file and iterated over it like so:

```
for id in coupons['offers'].keys(): add_coupon_by_id(id, 0) 
```

This worked really well. It turns out there are also two ways offers are stored - by regular coupon ID, like above, and then by UPC, so you need to make sure to do both.

These are stored as UPC keys with an array of offers.

![Safeway upc](https://blog.jonlu.ca/images/safeway_upc.png)

If you know the UPC of an item you’re following, it would be pretty easy to add functionality that shows you all offers for that item.

After running my script (which took a little over a minute), I refreshed the page and saw that all the offers had been added.

![Safeway all added](https://blog.jonlu.ca/images/safeway_added.png)

Reversing the Auth API
----------------------

The last step of the process is to find a way to generate `SWY_SSO_TOKEN` programmatically, so it can all be done in one function (and run on a cron job).

![Safeway auth flow](https://blog.jonlu.ca/images/safeway_add_coupon.png)

Upon filling in your credentials and hitting enter, the auth flow seems to function as follows:

1.  The browser fires an `OPTIONS` request to `https://albertsons.okta.com/api/v1/authn`. Since we’re doing this programmatically, we don’t need to worry about this (as it’s for cross origin request safety, a browser safety feature). The best part of this is that they’re actually using Okta, as their auth, more info on this later.
    
2.  The browser fires a `POST` request with a body of `{username: "", password: ""}`.
    
3.  The browser fires a `GET` request to `https://albertsons.okta.com/oauth2/` with the state from the previous request.
    
4.  The browser fires a `GET` request to the static redirect URL, which is ``https://shop.safeway.com/bin/safeway/sso/authorize?code=`&state=` ``
    
5.  ``That route replies back with `Set-Cookie` that sets our `SWY_SSO_TOKEN`.``
    

``The interesting thing about (2) is there is no unique token or requirements on the route - all you need to do is set the `Content-Type` and the request will go through:``

```
`headers = { 'Content-Type': 'application/json', } data = '{"username":"[[email protected]](https://blog.jonlu.ca/cdn-cgi/l/email-protection)","password":"oygncHm4iD4a"}' response = requests.post('https://albertsons.okta.com/api/v1/authn', headers=headers, data=data) print(response.text)` 
```

`This replies back with:`

```
`{  "expiresAt":  "2019-10-12T20:56:08.000Z",  "status":  "SUCCESS",  "sessionToken":  "",  "_embedded":  {  "user":  {  "id":  "",  "passwordChanged":  "2019-09-18T01:51:47.000Z",  "profile":  {  "login":  "",  "firstName":  "",  "lastName":  "",  "locale":  "en",  "timeZone":  "America/Los_Angeles"  }  }  },  "_links":  {  "cancel":  {  "href":  "https://albertsons.okta.com/api/v1/authn/cancel",  "hints":  {  "allow":  [  "POST"  ]  }  }  }  }` 
```

`The great part of all this is that there’s no guessing involved - this is actually the Okta auth flow, which is [heavily documented on their own site](https://developer.okta.com/docs/reference/api/authn/#primary-authentication-with-public-application). The last part of this is to just take this session and pass it along with the static application ID to the last okta, along with the static redirect URL.`

``Since this is just using okta’s sign in flow, we can play around with the parameters and authorization type - instead of a `code` response, we could accept a bearer token instead.``

``Having a bearer token lets us hit their `nimbus` API directly. I extracted the raw API route by man-in-the-middle-ing myself on iOS and used BurpSuite to find the route, but I’ll skip that section for brevity. Just know that all the above remains true, I’ll just be hitting their mobile API first instead (which is hosted on `nimbus.safeway.com`.``

`All it takes to authenticate is the following code:`

```
`import requests headers = { 'Host': 'albertsons.okta.com', 'Accept': 'application/json', 'Authorization': 'Basic ', 'Accept-Encoding': 'gzip, deflate', 'Accept-Language': 'en-us', 'Content-Type': 'application/x-www-form-urlencoded', 'charset': 'utf-8', } data = 'username=&password=&grant_type=password&scope=openid profile offline_access' response = requests.post('http://https://albertsons.okta.com/oauth2/ausp6soxrIyPrm8rS2p6/v1/token', headers=headers, data=data, verify=False)` 
```

``Note that `ausp6soxrIyPrm8rS2p6` is the ID okta assigned to Safeway.``

``The response has a `access_token` that can be used to authenticate as myself against their raw API.``

`The final request to their Nimbus API will look like:`

```
`import requests cookies = { 'swyConsumerDirectoryPro': '', } headers = { 'Host': 'nimbus.safeway.com', 'Authorization': 'Bearer ', } params = ( ('storeId', ''), ) response = requests.get('https://nimbus.safeway.com/emmd/service/gallery/offer/mfg>', headers=headers, params=params, cookies=cookies, verify=False)` 
```

``The response format is slightly different for mobile, but still has all the requisite information (specifically, we need our store ID, the `offerPgm`, and the `couponID`).``

```
`{  "ack":  "0",  "errors":  null,  "resultCount":  326,  "manufacturerCoupons":  [  {  "priceType":  null,  "priceSubType":  null,  "image":  "https://www.safeway.com/CMS/j4u/offers/images/440/979440_95beddb0-deab-4943-84f4-30c4a7b1fafc.gif",  "offerPrice":  "SAVE $1.00",  "description":  "on ONE (1) StonyfieldÂ® Organic Kids Multipacks, Tubes or Pouches (4pk or larger)",  "status":  "C",  "startDate":  "\\/Date(1569866400000)\\/",  "endDate":  "\\/Date(1572544800000)\\/",  "offerTs":  "1569341944086",  "usageType":  "O",  "offerPgm":  "MF",  "offerSubPgm":  "09",  "purchaseInd":  "L",  "commonPromoCodes":  null,  "categoryRank":  "null",  "clipTs":  null,  "events":  [],  "redemptions":  [],  "couponID":  "1116974738",  "brand":  "StonyfieldÂ® Organic",  "generalDisclaimer":  "Not subject to doubling. Void if sold, reproduced, altered, or expired and wherever taxed, regulated, restricted or prohibited by law. Limit one coupon per purchase of specified product(s). Consumer pays applicable sales tax. Coupon may not be combined with any other offer. Coupons not properly redeemed will be voided. Retailer: For each coupon accepted as an authorized agent we will pay you the face value of the coupon plus 8 cents handling. Invoices proving purchase of sufficient stock to cover all coupons redeemed must be shown upon request. Cash value 1/20 cent. Redeem by mail to: Stonyfield Farm, Inc., CMS Dept. # 52159, One Fawcett Drive, Del Rio, TX 78840. Void in LA & NV.",  "category":  "Dairy, Eggs & Cheese",  "vndrBannerCd":  "2bbf4b36-a75e-11e6-80f5-76304dec7eb7#C",  "purchaseRank":  "1",  "arrivalRank":  "1",  "expiryRank":  "1"  },  ]  }` 
```

``This returns all the coupons for a given store, which allows me to use the code from above to completely automate the process. I use the response from this code block to populate all the calls to `add_coupon_by_id`, and now it’s a closed loop system!``

`Automating it`
---------------

``I saved all this in a file called `safeway_coupons`, that I set up in a cron job. I threw it up on one of my personal production boxes and have it run every night at midnight with `0 0 * * * /usr/bin/python3 ~/safeway_coupons`. Tada! Every day all my coupons are synced and added automatically, and I don’t need to think about it when I go to the store. Whatever coupons I may have will be applied automatically when I check out, and I don’t need any of the mental overhead of couponing (especially since I’m not someone that “needs” to get the best deal - if what I’m buying has a coupon then great, but I’m not going to change my purchases based on coupons)``

### `Bonus: Speeding things up`

`It took nearly a minute to make 300 network requests - this was way too slow. I was running the code in a linear fashion - we only make the request to add the next coupon once the first has completed.`

`I reused a thread pool from one of my previous articles ([cs](https://blog.jonlu.ca/posts/safeway)), as below:`

```
 `class Worker(Thread): """ Thread executing tasks from a given tasks queue """ def __init__(self, tasks): Thread.__init__(self) self.tasks = tasks self.daemon = True self.start() def run(self): while True: func, args, kargs = self.tasks.get() try: func(*args, **kargs) except Exception as e: # An exception happened in this thread  print(e) finally: # Mark this task as done, whether an exception happened or not  self.tasks.task_done() class ThreadPool: """ Pool of threads consuming tasks from a queue """ def __init__(self, num_threads): self.tasks = Queue(num_threads) for _ in range(num_threads): Worker(self.tasks) def add_task(self, func, *args, **kargs): """ Add a task to the queue """ self.tasks.put((func, args, kargs)) def map(self, func, args_list): """ Add a list of tasks to the queue """ for args in args_list: self.add_task(func, args) def wait_completion(self): """ Wait for completion of all the tasks in the queue """ self.tasks.join()` 
```

`And then wrote a quick wrapper to the above function (since Python mapping doesn’t support multiple arguments without using partial 🙄).`

```
`def add_coupon_by_id_wrapper(params): add_coupon_by_id(*params) pool = ThreadPool(5) values = [] for id in coupons['offers'].keys(): values.append([id, 0, coupons['offers'][id]['offerPgm']]) pool.map(add_coupon_by_id_wrapper, values) pool.wait_completion()` 
```

`Now the entire function runs in about 5 seconds, which is much better!`

`  
  
from Hacker News https://ift.tt/2nESEb2`