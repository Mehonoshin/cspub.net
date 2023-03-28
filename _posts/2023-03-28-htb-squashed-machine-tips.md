---
layout: post
title: HTB: Squashed machine review
date: 2023-03-28 21:00 +0300
---

This post starts a series of reviews of machines available at HackTheBox.

Even though I haven't approached HTB for a long time I managed to hack it without looking into walkthroughs. Nice and easy machine. 

The foothold is straightforward. Just run nmap and it will point you to the service that has almost zero security controls. If you don't remember how to enumerate it, then [HackTricks](https://book.hacktricks.xyz/welcome/readme) has everything you need. Enumerate, poke both endpoints and see what you can do with it. The rest is standard, reverse shell and you have the user!

On privesc stage I almost got into a rabbit hole, but thanks to the gut feeling that I stopped digging it deeper. Also, retired HTB machines now have some kind of tags on machine information tab. Not sure if that is something common, but in this specific case one keyword brought my attention. I went through the enumeration process one more time and spotted an unusual file at user's directory.

Thanks to an old good article on Linux hacking, that explained unknown concepts and led me into the right direction https://www.hackinglinuxexposed.com/articles/20040513.html. 
The rest of the clues I found again at HackTricks website. 

XWD to the rescue! Rooted!