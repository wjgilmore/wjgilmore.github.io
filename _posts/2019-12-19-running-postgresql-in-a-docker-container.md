---
layout: post
title: Running PostgreSQL in a Docker Container
published: true
---

I've lately grown rather militant about separating my laptop (macOS) from various developer tools such as MySQL, PostgreSQL, and Nginx. [Homebrew](https://brew.sh/) is great, but running this sort of software in a Docker container is ultimately more flexible and maintainable, with the added benefit of no longer having to intermingle all of this additional software with the macOS operating system.

However, many newcomers to Docker find getting started to be pretty intimidating, particularly when dealing with things like networking and data persistence. So in this post I'll show you how to successfully configure a Dockerized PostgreSQL environment, hopefully showing you how to remove some of these initial barriers along the way. As a prerequisite you should have already [installed Docker on your laptop](https://docs.docker.com/docker-for-mac/install/).

After you've installed and started Docker, create a new directory named for instance `postgresql` and inside it create a file named `docker-compose.yml` and add the following contents to it:

```
version: '3.1'

services:

  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_USER: <USERNAME>
      POSTGRES_PASSWORD: <PASSWORD>
    ports:
        - 5432:5432

  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080
```

This `docker-compose.yml` file identifies one or more images


## Removing PostgreSQL from Homebrew

Once your dockerized PostgreSQL container is online, I suggest removing any local PostgreSQL versions from your operating system. Of course, if your local PostgreSQL databases contain anything of value you'll want to back them up and import them into the Dockerized PostgreSQL environment before continuing.

To view what software is running as a Brew service, run this command:

```
$ brew services list
```

If PostgreSQL is running, you'll want to stop it:

```
$ brew services stop postgresql
```

Finally, remove PostgreSQL:

```
$ brew remove postgresql
```

## Installing the psql Client on macOS

One unexpected side effect of removing PostgreSQL is the loss of the psql client. You can bring it back by installing libpq:

```
$ brew install libpq
```

Next, you'll need to symbolically link the newly installed `psql` client so it is available within your path:

```
$ brew link --force libpq
```

Once linked you'll be able to run `psql`:

```
$ psql --version
```

Now connect to your environment:

```
psql -h 0.0.0.0 -U wjgilmore
```

