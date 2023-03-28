---
layout: post
title: HTB: Antique machine review
date: 2023-03-28 21:04 +0300
---

Another easy machine. After a long break in CTFs I prefer to have a warmup with the easiest machines. It helps me to get back an offensive mindset and refresh my tooling and shortcuts.

Antique is just another x86 box that mimics an HP JetDirect printer.
As usually it all starts with a good enumeration, don't forget that UDP exists ;)
A quick googling for default printer creds should lead you to SNMP data exposure.
Reverse shell and user flag is in front you.

Privesc took a bit more time, and I've completely overlooked the intended way.
Eventually I've just used an exploit for CVE-2021-4034 because linpeas told that the machine was vulnerable. But later when reviewing the official walkthrough I realized that I didn't check a CUPS daemon running on the machine.

The intended way is much more interesting, because it involves tunnelling in order to access the CUPS admin interface which is running on localhost. Unfortunately it doesn't provide a way to get a root shell just an arbitrary file read as a root. So my unintended way of privesc was even more effective because I got the root shell.

Anyway, I enjoyed this box and it did a good job for me. Refreshing my skills and knowledge feels damn good!