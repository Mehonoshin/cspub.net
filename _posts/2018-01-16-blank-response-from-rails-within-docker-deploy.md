---
layout: post
title: Blank response from Rails within Docker deploy
date: 2018-01-16 22:20 +0300
---

It is the second time, when I ship application in Docker container and see the following error:

```
An unhandled lowlevel error occurred. The application logs may have details.
```

Usually after that you open application logs inside container, and see nothing.

There are two problems, which are constantly repeated by me:

* I forget to set `RAILS_LOG_TO_STDOUT` env variable to `true`, so rails logs are missing
* When I set logging properly then I can figure out, that `Missing `secret_key_base` for 'production' environment, set this value in `config/secrets.yml``

So I just need to set `secret_key_base`.

Just make sure, that this key value is in safe, so don't keep it in your SCM, but ship it with old good ENV variables.
