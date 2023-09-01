---
layout: post
title: "BlitzBuilding with AI: Creating and Launching SaaS Products in Less Than 24 Hours"
published: true
---

In August, 2023 I launched two new SaaS products: <a href="https://emailreputationapi.com">EmailReputationAPI</a> and <a href="https://blogignite.com">BlogIgnite</a>. While neither are exactly moonshots in terms of technical complexity, both solve very real problems that I've personally encountered while working at multiple organizations. EmailReputationAPI scores an email address to determine validity, both in terms of whether it is syntactically valid and is deliverable (via MX record existence verification), as well has the likelihood there is a human on the other end (by comparing the domain to a large and growing database of anonymized domains). BlogIgnite serves as a writing prompt assistant, using AI to generate a draft article, as well as associated SEO metadata and related article ideas.

Launching a SaaS isn't by itself a particularly groundbreaking task these days, however building and launching such a product in less than 24 hours might be somewhat more notable accomplishment. And that's exactly what I did for both products, deploying MVPs approximately 15 hours after writing the first line of code. Both are written using the <a href="https://www.laravel.com">Laravel framework</a>, a technology I happen to know pretty well. However there is simply no way I would have met this self-imposed deadline without leaning heavily on artificial intelligence throughout the process. After working through this process twice, I am convinced AI coding assistants are opening up the possibility of rapidly creating, or "blitzbuilding", new software products.

The goal of blitzbuilding is _not_ to create a perfect or even a high-quality product! Instead, the goal is to minimize business risk incurred via a prolonged development cycle by embracing AI to assist with the creation of a marketable product in the shortest amount of time.

> The term _blitzbuilding_ is a tip of the cap to LinkedIn founder Reid Hoffman's book,
> "Blitzscaling: The Lightning-Fast Path to Building Massively Valuable Companies", in which
> he describes techniques for growing a company as rapidly as possible.

## The Development and Technology Stack

The chosen technology stack isn't important by itself, however it is critical that you know it reasonably well otherwise the AI will give advice and offer code completions that can't easily be confirmed as correct. In my case, EmailReputationAPI and BlogIgnite are built atop the Laravel framework, use the MySQL database, with Redis used for job queuing. They are hosted on Digital Ocean, and deployed with Laravel Forge. Stripe is used for payment processing. The common thread here is I am quite familiar with all of these technologies and platforms. Blitz building is not a time for experimenting with new technologies, because you will only get bogged down in the learning process.

The coding AI is [GitHub Copilot](https://docs.github.com/en/copilot) with the [Chat](https://docs.github.com/en/copilot/github-copilot-chat) functionality. At the time of this writing the Chat feature is only available in a limited beta, but it is already extraordinarily capable insomuch that I consider it indispensable. Among many things it can generate tests, offer feedback, and even explain highlighted code. GitHub Copilot Chat runs in a VS Code sidebar tab, like this:

<a href="/assets/img/blitzbuilding/vscode-copilot.png">
<img src="/assets/img/blitzbuilding/vscode-copilot.png" alt="Visual Studio Code's GitHub Copilot integration" width="75%" />
</a>

Notably missing from these products is JavaScript (to be perfectly accurate, there are miniscule bits of JavaScript found on both sites due to unavoidable responsive layout behavior) and custom CSS. I don't like writing JavaScript, and am terrible at CSS and so leaned heavily on <a href="https://tailwindui.com/">Tailwind UI</a> for layouts and components.

## Clearly Define the Product's Purpose and Scope

24 hours will be over before you know it, and so it is critical to clearly define the minimum acceptable set of product requirements. Once defined, cut the list in half, and then cut it again. To the bone. Believe me, that list should be much smaller than you believe.

For EmailReputationAPI, that initial list consisted of the following:

- Marketing website
- Account management (register, login, trial, paid account)
- Crawlers and parsers to generate various datasets (valid TLDs, anonymized domains, etc)
- Secure API endpoint and documentation
- Stripe integration

There are now plenty of additional EmailReputationAPI features, such as a <a href="https://packagist.org/packages/emailreputationapi/reputation">Laravel package</a>, but most didn't make the list critical to the first release and so were delayed.

It is critical to not only understand but be fine with the fact _you will not be happy with the MVP_. It won't include all of the features you want, and some of the deployed features may even be broken. It doesn't matter anywhere near as much as you think. What does matter is putting the MVP in front of as many people as possible in order to gather feedback and hopefully customers.

## Lean Heavily On AI Instead of Troubleshooting and Googling

I hate CSS with the heat of a thousand suns, largely because I've never taken the time to learn it well and so find it frustrating. I'm also horrible at design. I'd imagine these traits are shared by many full stack developers, which explains why the Bootstrap CSS library was such a huge hit years ago, and why the Tailwind CSS framework is so popular today. Both help design-challenged developers like myself build acceptable user interfaces.

That said, I still don't understand what most of the Tailwind classes even do, but fortunately GitHub Copilot is a great tutor. Take for example the following stylized button:

```
<button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700">
    <span class="sr-only">Open main menu</span>
    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
    <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
    </svg>
</button>
```

I have no idea what the classes `-m-2.5`, `inline-flex`, etc do, but so can ask Copilot chat to explain:

<a href="/assets/img/blitzbuilding/css-explanation.png">
<img src="/assets/img/blitzbuilding/css-explanation.png" alt="Explaining Tailwind with Copilot chat" width="50%" />
</a>

I also use Copilot chat to offer code suggestions. One common request pertains to component alignment. For instance I wanted to add the BlogIgnite logo to the login and registration forms, however the alignment was off:

<a href="/assets/img/blitzbuilding/login-before.png">
<img src="/assets/img/blitzbuilding/login-before.png" alt="Misaligned logo" width="50%" />
</a>

I know the logo should be aligned with Tailwind's alignment classes, but have no clue what they are nor do I care. So after adding the logo to the page I asked Copilot `how to center mark.png in the parent div?`. It responded with:

<a href="/assets/img/blitzbuilding/vscode-alignment.png">
<img src="/assets/img/blitzbuilding/vscode-alignment.png" alt="Aligning a logo" width="50%" />
</a>

After updating the image classes, the logo was aligned as desired:

<a href="/assets/img/blitzbuilding/login-after.png">
<img src="/assets/img/blitzbuilding/login-after.png" alt="Aligned logo" width="50%" />
</a>

## Where to From Here?

Even when using the AI assistant the turnaround time is such that your product will inevitably have a few bugs. Focus on fixing what your early users report, because those issues are probably related to the application surfaces other users will also use. Sometime soon I'd love to experiment with using a local LLM such as [Code Llama](https://ai.meta.com/blog/code-llama-large-language-model-coding/) in conjunction with an error reporting tool to generate patches and issue pull requests. At some point in the near future I could even see this process as being entirely automated, with the AI additionally writing companion tests. If those tests pass the AI will merge the pull request and push to production, with no humans involved!

## Contact Jason

Have any questions or thoughts about this post? Contact Jason at wj@wjgilmore.com.
