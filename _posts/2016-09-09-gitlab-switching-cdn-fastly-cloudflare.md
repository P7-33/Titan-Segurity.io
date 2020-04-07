---
title: 'Gitlab Switching CDN''s (Fastly – CloudFlare)'
date: 2020-01-17T05:32:00+01:00
draft: false
---

![](https://about.gitlab.com/images/blogimages/daytime-clouds.jpg " Why GitLab.com is changing its CDN provider to Cloudflare | GitLab ")  

Upcoming changes to our CDN for GitLab.com
------------------------------------------

As GitLab.com has grown, so have our needs around the security and scalability of the web application. We are in the process of changing our CDN provider to [Cloudflare](https://www.cloudflare.com/) as part of our improvements to GitLab.com. We are approaching this change with care, and this post is to let everyone know about the shift ahead of time.

### Why are we working on this?

We are currently using [Fastly](https://www.fastly.com) for serving static content, but we want to improve GitLab.com availability, security, and performance with other tools like a Web Application Firewall (WAF), [Spectrum](https://www.cloudflare.com/products/cloudflare-spectrum/), and [Argo](https://www.cloudflare.com/products/argo-smart-routing/). We also want to preserve the current workflow: Interacting with GitLab.com for both `git` and web application interactions. Since GitLab.com serves more than just https traffic, the change is a little more complicated. The traffic pattern requires we use a solution that could handle traffic for port 22 and port 443. As a result of the complexity and requirements, we realized we would like to have a solution for CDN, WAF, and DDOS protection with one vendor.

During the summer of 2019, we did evaluations and chose Cloudflare as the vendor who could best meet our requirements. Now that we are closer to switching over, we have created a [readiness review](https://gitlab.com/gitlab-com/gl-infra/readiness/tree/master/cloudflare) to talk about our plans for the change over.

### What you need to know

First, this change will not affect self-managed users of GitLab, this is only for users of GitLab.com. At a very high level, most users of GitLab.com will not need to take any action.

GitLab.com users with a whitelist of sites in their firewall setup will need to change what is whitelisted for GitLab.com. For the initial change, we will be switching DNS to Cloudflare. This will cause all GitLab.com traffic to be proxied through Cloudflare. This change will be visible by changes in DNS records queried for GitLab.com. A whitelist of IPs can be found [here](https://www.cloudflare.com/ips/). We wanted to make sure this is communicated ahead of time, as this is an important detail, which may be in use by some firewalling setups.

SSH-based `git` actions via `altssh.gitlab.com` on port 443 continue to be supported. As with GitLab.com, any firewalls you set up might need to be reconfigured to the new IP ranges.

Custom runner images or private runners could also be affected if they have any kind of caching of DNS or SSL certificates.

### How can I stay up to date on when the change will happen?

We will update this blog post, [GitLab status](https://status.gitlab.com), and [@gitlabstatus on twitter](https://www.twitter.com/gitlabstatus) with the planned date of this initial change – likely sometime in early February 2020. When it is time for the change on GitLab.com, we will also update [GitLab.com ranges](https://docs.gitlab.com/ee/user/gitlab_com/#ip-range) with the range from [Cloudflare](https://www.cloudflare.com/ips/).

Once we know traffic is flowing through Cloudflare successfully, we will start exploring more features like the WAF in logging-only mode. We will also test [Argo](https://www.cloudflare.com/products/argo-smart-routing/) and we hope again that traffic to GitLab.com is faster.

Feel free to ask our support team your questions, and they will be able to talk to our infrastructure team for the details. Thanks for your continued support and check here for more updates soon!

### Links to our plans and other information

1.  [GitLab status: Subscribe by email, twitter, webhook, slack](https://status.gitlab.com)
2.  [More discussion about this blog post](https://gitlab.com/gitlab-com/www-gitlab-com/issues/5907)
3.  [Production readiness review MR](https://gitlab.com/gitlab-com/gl-infra/readiness/tree/master/cloudflare)
4.  [Top-level epic](https://gitlab.com/groups/gitlab-com/gl-infra/-/epics/94)
5.  [Cloudflare privacy policy](https://www.cloudflare.com/privacypolicy/)
6.  [Cloudflare IP ranges](https://www.cloudflare.com/ips/)

### Definitions

*   Web Application Firewall (WAF): A type of firewall that helps protect web applications from a specific set of attacks
*   Argo: Cloudflare product that helps route web traffic across the fastest and most reliable network paths
*   Spectrum: A Cloudflare product that helps secure the types of ports that GitLab.com uses for SSH access

Cover image by [Sam Schooler](https://unsplash.com/photos/E9aetBe2w40) on [Unsplash](https://unsplash.com/)

  
  
from Hacker News https://ift.tt/2Rn4yB9