---
title: 'Writing Runbook Documentation When You’re an SRE'
date: 2020-02-01T02:13:00+01:00
draft: false
---

Writing Runbook Documentation When You’re An SRE
================================================

Tips and tricks for writing effective runbook documentation when you aren’t a technical writer
----------------------------------------------------------------------------------------------

![](https://d33wubrfki0l68.cloudfront.net/5e3adc67354e9b5f48954b4a68683680fba19b54/aafe9/blog/img/authors/taylor.jpg) Taylor Barnett · Jan 30, 2020

![Keyboard photo by NihoNorway graphy on Unsplash](https://d33wubrfki0l68.cloudfront.net/53b7baed590146829c40852b5b4ec77fce192019/4f30f/blog/img/2020.01.30a.jpg)

The sad reality is, no one actually wants to read your runbook documentation. Engineers who get paged while on-call want to mitigate and resolve an incident as fast as possible, and move on. Nonetheless, runbooks, sometimes called playbooks, are necessary. As [The Site Reliability Workbook](https://landing.google.com/sre/workbook/chapters/on-call/) says, playbooks “reduce stress, the mean time to repair (MTTR), and the risk of human error.”

Often I have found that engineers don’t want to write documentation for two main reasons: There isn’t an incentive structure for doing the work, and they are unsure of how to write good documentation.

Focusing on the latter, while no runbook will be “a substitute for smart engineers able to think on the fly, as the [Site Reliability Engineering: How Google Runs Production Systems](https://landing.google.com/sre/sre-book/chapters/introduction/) book says, “clear and thorough troubleshooting steps and tips are valuable when responding to a high-stakes or time-sensitive page.”

Unlike the tons of content for engineers on how to write good code, there’s a lot less for documentation, especially runbooks. Whether your team is practicing DevOps or traditional IT operations, this blog post is focused on helping Site Reliability Engineers (SREs) and other engineers who are involved in on-call engineering create clearer and more effective runbook documentation.

Runbook Templates [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#runbook-templates)
------------------------------------------------------------------------------------------------------------------------------------

Blank pages are no fun. Using a template can be beneficial because starting from a blank document is incredibly hard. A template gives you an outline to start out with. It’s guidance on how to get started, which is the hardest part when writing. What template you use for your runbooks heavily depends on your team. It’s essential to get buy-in from the team; otherwise, the team won’t use it. If there’s a section that a majority of the team doesn’t find useful, they are unlikely to fill it out.

I’m not going to recommend one template to rule them all, but I can recommend some templates that will hopefully inspire you. I choose these because I feel they have the right balance of information. It’s easy for the template to grow to be very large and daunting for any engineer to fill out. Check out these examples:

The one thing I do recommend is that alert names’ map to the runbook name. This can be very helpful for making your runbooks discoverable. It can also help you evaluate the runbook coverage you have for your on-call team.

The Curse of Knowledge [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#the-curse-of-knowledge)
----------------------------------------------------------------------------------------------------------------------------------------------

[The Curse of Knowledge](https://hbr.org/2006/12/the-curse-of-knowledge) is a cognitive bias that occurs when someone is communicating with others and unknowingly assumes the level of knowledge of the people they are communicating with. As we progress in our fields, we gain more experience, and as this happens, it becomes harder to recreate a state of mind without this new knowledge.

It is a significant barrier to expressing empathy in documentation. The ramifications of the Curse of Knowledge can be pretty harmful.

For example, it can cause us to leave out whole steps in step-by-step instructions, like needing to install a particular piece of software or script. It can also lead to oversimplifying things and using words such as “simply,” “easy,” “just,” and other words that can vary based on experience level. So, what’s the solution?

Remove those words from your documentation. At best, they don’t help anyone. At worst, they are demeaning when you are struggling in an incident. Other solutions include making sure people at all levels who might be using the runbooks have a chance to review and catch anything that might have been missed. To do this effectively, though, you need to have a collaborative environment where someone feels comfortable speaking up on something that feels left out or is confusing. The best part of doing this work is that you are working towards more empathetic documentation.

SRE Documentation Glossaries [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#sre-documentation-glossaries)
----------------------------------------------------------------------------------------------------------------------------------------------------------

Glossaries can be helpful for a few reasons:

*   Glossaries help you repeat yourself less. When you can refer to a definition with a linked explanation, you just saved yourself time and words.
*   Glossaries make descriptions more consistent. If something is explained in five different ways, it can get confusing.
*   Glossaries allow a runbook to be more easily used by engineers with different levels of experience. By referencing a glossary in your runbook, you allow someone newer to the on-call rotation to get the explanation of concepts or terms they need. For more experienced on-call engineers, you remove extraneous information from the runbook.

Also, make sure to add unique acronyms to the glossary too. Some teams and organizations use unique acronyms that might not be widely known. A glossary is a great place to explain them.

Prevent Runbook Search Failure [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#prevent-runbook-search-failure)
--------------------------------------------------------------------------------------------------------------------------------------------------------------

Users quickly glance over documentation to try to find what they are looking for. Commonly, they miss critical information they are looking for because of the structure or format of the documentation, causing what I call “search failure.”

The Nielsen Norman Group has been [researching how people read on the web through eye-tracking studies](https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/) for years. They found that often people read in F-shape patterns. The two implications they pointed out from this pattern is that the “first lines of text on a page receive more gazes than subsequent lines of text on the same page” and the “first few words on the left of each line of text receive more fixations than subsequent words on the same line.” So, what does this mean for your runbook documentation?

Your runbook templates must include a section at the top to describe in one sentence the intent of the runbook. This can help an engineer quickly confirm if they are looking at the right information.

Also, you should only have one step, command, or instruction per paragraph or list item. It will make it easier for readers not to miss a step. Along with this, shorter sentences reduce the chances of search failure. Long, drawn-out paragraphs and sentences often get glanced over, so make sure to break up different information into new sentences, paragraphs, and list items.

Readable Runbook Steps [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#readable-runbook-steps)
----------------------------------------------------------------------------------------------------------------------------------------------

Often paragraphs in a runbook can become more readable if they are turned into a bulleted list. If order matters, make sure to number the list items turning it into a numbered list of steps (E.g., 1, 2, 3). It makes it easier to follow and to reference. It can prevent readers from not skipping steps during incidents when treated as a checklist.

Even a basic three-item list in a sentence can be improved. For example, quickly read the sentence below from another Transposit blog post:

> This blog post is the second in a series of a few posts where I’ll cover how Transposit uses the OpenAPI Specification, AWS APIs, Boto, and why we had to support them differently with OpenAPI, and how we created OpenAPI extensions and what we learned from this process.

And now quickly read the bulleted list below:

> This blog post is the second in a series of a few posts where I’ll cover:
> 
> *   How Transposit uses the OpenAPI Specification
> *   AWS APIs, Boto, and why we had to support them differently with OpenAPI
> *   How we created OpenAPI extensions and what we learned from this process

Which did you get more information out of? (Most likely, the latter.) Anytime there is a list in a sentence, turn it into a bulleted list. It will help search failure and help readers of your list absorb the information.

Lastly, start sentences with an imperative verb, also known as a command, in your lists. For example, words like “download,” “configure,” “restart,” and “open.” This helps readers since their eyes will likely only scan the first few words on the left of each line of text.

Code in Runbooks [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#code-in-runbooks)
----------------------------------------------------------------------------------------------------------------------------------

If you have ever copied and pasted anything from some documentation to the command line, you’ve probably encountered some “command not found” problem. Whether it is documentation including the `$` or a library that should have been installed first, it is vital to give the user context. For example, instead of including the `$` to represent using a command on your command line, instruct the user where to use the command instead: “In your terminal…” Or, if there are some installation prerequisites, describe them in the runbook or add a link to them.

Lastly, if a script is longer than a single line, treat it like code, and check it into a repository to be source control and potentially tested. This will ensure the quality is maintained and that incorrect or even dangerous scripts don’t get used during the response to an incident.

Writing Runbooks Documentation is Hard [#](https://www.transposit.com/blog/2020.01.30-writing-runbook-documentation-when-youre-an-sre/#writing-runbooks-documentation-is-hard)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Hopefully, these tips and tricks will help you when you are writing a new or updating an existing runbook. Like learning any new skill, it can be hard and takes practice. Having on-call teammates of all skill levels help you review your runbooks can be very helpful to progress your skills. Now go improve some runbooks!

P.S. Check out the blog post that my teammate, Dan, wrote about [what makes a good runbook](https://www.transposit.com/blog/2019.11.14-what-makes-a-good-runbook/).

### Try intelligent runbooks and simplified incident resolution

**Thank you for your interest in Transposit**

**Thanks! We'll be in touch soon.**

  
  
from Hacker News https://ift.tt/2OgXky0