---
layout: page
title: Disabling SSL Validation in Bruno
published: true
---

I use <a href="https://herd.laravel.com/">Laravel Herd</a> to manage local Laravel development environments. Among many other things, it can generate self-signed SSL certificates. This is very useful however modern browsers and other HTTP utilities tend to complain about these certificates. Fortunately it's easy to disable SSL validation by opening Bruno, navigating to `Settings` under the `Bruno` menu heading, and unchecking `SSL/TLS Certificate Verification`.

<img src="/img/bruno-ssl.png" alt="Disabling SSL validation in Bruno" />
