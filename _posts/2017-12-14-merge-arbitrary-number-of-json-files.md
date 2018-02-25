---
layout: post
title: Merge arbitrary number of json files
date: 2017-12-14 18:05 +0200
tags: [cli]
---

Sometimes you need to merge an arbitrary amount of json files.
For example, simplecov reports for Ruby application.

```
jq -s 'reduce .[] as $item ({}; . * $item)' *.json .*.json > r.txt
```
