---
layout: post
title: Laravel Jetstream: Changing the Login Redirection URL
published: true
---

By default Laravel Jetstream will redirect newly logged in users to the `dashboard` route. A side project I'm building didn't have a need for a general post-authentication landing page, and so I needed to figure out how to redirect the user elsewhere. Turns out it's pretty easy. Open `config/fortify.php` and locate this line:

```
'home' => RouteServiceProvider::HOME,
```

Change it to:

```
'home' => function(){ return route('queries.index'); },
```

Of course you'll want to swap out `queries.index` with your desired route name. You can retrieve a list of route names for your application by running:

```
php artisan route:list
```
