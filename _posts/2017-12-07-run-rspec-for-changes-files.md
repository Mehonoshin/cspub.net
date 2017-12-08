---
layout: post
title: Run RSpec for changes files
date: 2017-12-07 17:41 +0300
categories: english
---

Sometimes you work on git branch for a while, and at the end you want to run all specs you've modified.

Here is a nice snippet that allows you to do this:

```
gst --short | ruby -e "puts ARGF.read.split(' M ').map(&:strip).select{ |f| f.end_with?('_spec.rb') }.join(' ')"
```
