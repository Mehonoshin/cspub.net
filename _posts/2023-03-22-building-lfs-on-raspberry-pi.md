---
layout: post
title: Building Linux From Scratch on Raspberry Pi 1
date: 2023-03-22 18:53 +0300
---


### What is LFS?

Linux world is huge. There hundreds, maybe even thousands of distros available on the internet. For a long time I enjoyed trying new distros and every time learning something new. 
But LFS always seemed to be complex and time consuming experience, something that requires non-trivial skills. Because of that it has been in my learning todo list for a long time.

If you are not familiar, LFS is not a real distro. In reality it is just a cook book that describes the process of building your own distro step by step. The sweet part is that you don't use any prepared packages, but build everything from the sources. Sounds similar to Gentoo, right? But LFS goes further, it does not provide you a package manager like Gentoo. You have to download a vanilla tar.gz archive from developer's website for each tool that you will install. If the package needs some security patch, you again apply it manually.

And then the magic happens: __./configure && make && make install__

### LFS flavors

If you visit LFS website, you will also discover that BLFS and ALFS exist. The idea is that after building LFS you get a very basic Linux system, something like Debian minimal but much simplier. So no UI, just bare minimum of CLI tools.

For those brave souls, who wish to build a feature rich system the [BLFS(Beyond LFS)](https://www.linuxfromscratch.org/blfs/view/stable/) project exists. It aims to add UI and a bunch of essential software.

Another use case for LFS is building a minimal purpose driven distro for embedded systems. Developers of such systems need automation that allows to get reproducible builds without human intervention. So [ALFS](https://www.linuxfromscratch.org/alfs/) project solves this problem by providing the tooling for continuous bulding.

### PiLFS

To get more fun I have chosen PiLFS project instead of vanilla LFS. The main difference is that PiLFS is oriented on Raspberry Pi Arm boards, so it requires some extra tricks and tweaks to make it work. I grabbed my old 1st generation Raspberry Pi and started reading the LFS book in parallel with PiLFS website.

Luckily there are not that many differences between LFS and PiLFS, most of the time I followed the original LFS book and just had to make minor adjustments for PiLFS.

### The plan

Probably at this point you are curious how does the build process look like? I don't want to repeat the contents of the LFS book, so will just share a short and rough plan of the whole process for those who are curious.

- Prepating for the build
	- Making partition
	- Downloading packages
	- Compiling tools
- Building LFS toolchain and temporary tools
- Switching to chroot environment
- Building the system
	- Installing packages
	- Setting up boot scripts
	- Compiling kernel

In order this plan to be executed you need to satisfy several prerequisitives. First of all you need a working Linux system that has a set of required build tools. This system should run on the same architecture as your future LFS system. In my case I used a [base system](https://intestinate.com/pilfs/) from PiLFS that has all build tools and runs on ARM boards. But generally any of Linux distros with some extra packages would work for this purpose.

The whole process starts with creating a separate partition on your disk and mounting it to the host system. You download all required sources there. All the work will happen on that partition, so it's always worth having a backup. 
Then you start building a temporary toolkit on your host system. That toolkit will be used for building the final system itself.
When you are done with the first phase of compillation, you switch into chroot environment from the host system and finalize the build there.
As a result you have a full Linux system placed on the separate partition, and it becomes just a matter of changing the boot process to start your new system.

### My experience

First of all I have to admit that picking Raspberry Pi 1 was a brave decision, taking into the account its CPU power. It took around 300+ hours to compile the system.

Secondly, following PiLFS way wasn't absolutely smooth process. Unfortunately some ARM specific packages and patches were not available or moved to other locations on developer websites. So it took a while to figure out where to get the required archives. 

Thirdly, PiLFS offers a couple of scripts that automate the routine of compiling packages. Basically the installation of any package involves the following steps:
1. Extract the archive
2. Apply patches if needed
3. Run ./configure
4. Run make
5. Run make install

There are tens or even hundred of such packages required for LFS, so PiLFS scripts simplified the process significantly. Without them it would take much more of my time to build everything, because I would have to perform those routinous operations for every package manually. But don't treat it as a cheating! There is a plenty of manual work that is more important for the learning process and not automated at all.

Together with reading the book, writing notes and reading extra materials it took a bit more than one month to finally complete the system. I intentionally didn't hurry with the process and tried to read and learn as much as I can.

### The main benefit

So, you might ask, did it worth it? Why should someone spend tens or hundreds of hours on building just another linux distro? Where is the payback?

From my perspective experience and knowledge is the major benefit that LFS brings to the most of engineers. Unless your work project requires a custom distro, the only purpose of building LFS is unvaluable learning process. It is possible to build an LFS in speed run mode, by just copy and pasting the commands from the book in order to get the final system as soon as possible. But it should not be your goal if you eager to get the most from the process. The final system is extremely simple, has the most basic functionality and no practical use cases. I personally booted the final system just once, to make sure that it works.

On the other hand, while you go through the book you will most probably read about multiple different concepts that are unfamiliar for you. I encourage everyone to spend time and read all those extra materials and make notes in meanwhile. Many thanks to the book authors who added lots of links to other reading materials. They are not a part of the book and can be easilly skipped, though that's where the most of value is hidden.

- Most probably you have heard about [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/) standard, but have you wondered what is included there? Have you ever read the specification document itself?
- Or do you know why [Linux filesystem](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html) has the structure that it has? What is the conceptual difference between _/bin_ and _/sbin_ folders?
- What is the difference between interactive and non-interactive, login/non-login bash shells?

These are just sample questions that can pop up during build process. That knowledge is not essentially required for LFS process, but those are fundamental concepts that many of us are not aware. Just think about it, in the recent decade cloud became a thing, old-fashioned SysAdmins were replaced by DevOps, but Linux is still the same fundametal layer that runs most of the modern internet. Investing in fundamental knowledge and skills is probably the best what you can do with your free time.

I personally learned a lot, but also I collected a huge list of topics where I have gaps in my knowledge. So crossing one item from the learning list brought a dozen of others.

_"The more you know, the more you realize you don't know."_ - LFS once again confirms that it is truth. 


