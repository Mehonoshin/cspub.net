---
layout: post
title: Rename entity across Rails project
date: 2018-08-25 15:59 +0300
tags: [cli, til]
---

Today while working on my open source project [givemepoc.org](https://github.com/howtohireme/give-me-poc) I faced a situation,
when I needed to replace `Developer` and `developer` entity with `Mentor` and `mentor`
across the whole project.

I use vim for my daily development, and it didn't have such tools installed. Most probably
RubyMine or some other IDE can offer such functionality, but I decided to follow Unix way
and find some useful command line utility.

After googling, I found two snippets, which can solve my problem.

1. The first one has an excellent explanation in the [blog](https://isaacsukin.com/news/2013/06/command-line-tip-replace-word-all-files-directory).
We need to run, and it will replace the required keyword across all files.

But pay attention to your `.git` folder, because you can easily break it, as I did :-D

`grep -lr -e "developer" . | xargs sed -i '' -e 's/developer/member/g'\n`


2. The second snippet renames your files and directories since we have just changed the contents of files with the first command.

`find . -name '*developer*' -exec bash -c 'mv $0 ${0/developer/member}' {} \;`

Of course, these tools do not provide you smart refactoring functionality, as most of the IDEs can.
But they are fast and such renamings do not happen often, they should not happen at all if you pick suitable namings for your entities.
