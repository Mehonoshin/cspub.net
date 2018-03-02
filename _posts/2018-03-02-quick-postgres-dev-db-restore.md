---
layout: post
title: Quick postgres dev db restore
date: 2018-03-02 18:22 +0300
tags: [db, postgres, til]
---

Recently I worked on massive data migration in single postgres database. It involed running a bunch of scripts, that modify rows in several DB tables.

It was a repetitive process, that required multiple runs of the same script for debugging purposes. And having a convenient way of resetting the database was 'a must'.

Restoring the whole database from an SQL dump is quite a painful process, that takes too much time(aroung 20 minutes on my machine). So I decided to find a faster way,
that can make my 'run-review-debug' cycle shorter.

The solution, that I want to share is creating postgres DB from template DB.

* First, you should import full dump in some database, called for example `database_development_template`
* Create a new database, using previous DB as template `create database database_development template database_development_template;`

I extracted this task into a separate script on my github, so [check it out](https://github.com/Mehonoshin/toolkit/blob/master/tools/db_reset/db_reset.sql).
