---
layout: post
title: Breaking CD with Recaptcha
date: 2018-03-10 15:52 +0300
tags: [ci, cd, captcha, devops]
---

Today I faced a weird situation. Our [howtohireme](https://howtohireme.ru) CD pipeline became red!

I should notice, that we haven't committed anything to this repo for several months, the only change was in ansible playbooks, that
was not able to affect our pipeline.

But we received the following error at our Watir-Cucumber tests:

`Element <button class="btn-slider mt20 reversed" type="submit">...</button> is not clickable at point (403, 552). Other element would receive the click: <iframe src="https://www.google.com/recaptcha/api2/anchor?k=6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI&amp;co=aHR0cDovL25naW54Ojgw&amp;hl=en&amp;v=v1520231465640&amp;size=normal&amp;cb=ojkej8zh6vbk" width="304" height="78" role="presentation" frameborder="0" scrolling="no" sandbox="allow-forms allow-popups allow-same-origin allow-scripts allow-top-navigation allow-modals allow-popups-to-escape-sandbox"></iframe>`

Basically it means, that form button is not clickable, because it has recaptcha elements above.

If we look into recaptcha gem [source](https://github.com/ambethia/recaptcha/blob/master/lib/recaptcha/client_helper.rb#L25) then we can see, that
it has an IFrame, from Google. So it is a kind of dynamic part, that can't be controlled by yourself.

Even if you have a strict versions of libraries in your app, Google can change recaptcha IFrame anytime, and it can possibly break your app.

To sum up, don't trust client-side libraries blindly. They can use 3-rd party parts, that can't be controlled by you, and this can lead to
unstable and not robust CI/CD pipeline.
