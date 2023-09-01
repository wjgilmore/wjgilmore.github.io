---
layout: post
title: Blitz Building with AI: Creating and Launching SaaS Products in Less Than 24 Hours
published: true
---

In August, 2023 I launched two new SaaS products: <a href="https://emailreputationapi.com">EmailReputationAPI</a> and <a href="https://blogignite.com">BlogIgnite</a>. While neither are exactly moonshots in terms of technical complexity, both solve very real problems that I've personally encountered while working at multiple organizations. EmailReputationAPI scores an email address to determine validity, both in terms of whether it is syntactically valid and is deliverable (via MX record existence verification), as well has the likelihood there is a human on the other end (by comparing the domain to a large and growing database of anonymized domains). BlogIgnite serves as a writing prompt assistant, using AI to generate a draft article, as well as associated SEO metadata and related article ideas.

Launching a SaaS isn't by itself a particularly groundbreaking task these days, however building and launching such a product in less than 24 hours might be somewhat more notable accomplishment. And that's exactly what I did for both products, deploying MVPs approximately 15 hours after writing the first line of code. Both are written using the <a href="https://www.laravel.com">Laravel framework</a>, a technology I happen to know pretty well. However there is simply no way I would have met this self-imposed deadline without leaning heavily on artificial intelligence throughout the process. After working through this process twice, I am convinced AI coding assistants are opening up the possibility of rapidly creating, or "blitz building", new software products.

## Clearly Define the Product's Purpose

Once defined, cut the desired feature set in half, and then cut it again. To the bone. Determine what are the absolute minimum requirements necessary to launch the MVP in less than 24 hours. Believe me, that list will be much smaller than you believe.

For EmailReputationAPI, that initial list consisted of the following:

- Marketing website
- Account management (register, login, trial, paid account)
- Crawlers and parsers to generate various datasets (valid TLDs, anonymized domains, etc)
- Secure API endpoint and documentation
- Stripe integration

There are now plenty of additional EmailReputationAPI features, such as a <a href="https://packagist.org/packages/emailreputationapi/reputation">Laravel package</a>, but most didn't make the list critical to the first release and so were delayed.

## Use Familiar Technology

Both EmailReputationAPI and BlogIgnite are built atop the Laravel framework, use the MySQL database, with Redis used for job queuing. They are hosted on Digital Ocean, and deployed with Laravel Forge. Stripe is used for payment processing. The common thread here is I am extremely familiar with all of these technologies and platforms. Blitz building is not a time for experimenting with new technologies, because you will only get bogged down in the learning process.

Notably missing from these products is JavaScript (to be perfectly accurate, there are miniscule bits of JavaScript found on both sites due to unavoidable responsive layout behavior) and custom CSS. I don't like writing JavaScript, and am terrible at CSS and so leaned heavily on my <a href="https://tailwindui.com/">Tailwind UI</a> account for layouts and components.

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

I have no idea what the classes `-m-2.5`, `inline-flex`, etc do, and so can ask Copilot chat to explain:

<img src="/img/blitzbuilding/css-explanation.png" />

```
<div class="flex justify-center">
<img src="/img/mark.png" alt="BlogIgnite" />
</div>
```

## Is the Product a Vaccine or Vitamin?

## Trials Must be Self-Serve

## Use Free Online Services

https://favicon.io/favicon-converter/
