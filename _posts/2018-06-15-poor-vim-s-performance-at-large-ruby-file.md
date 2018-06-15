---
layout: post
title: Poor Vim's performance at large Ruby file
date: 2018-06-15 16:48 +0300
tags: [vim cli]
---

I use MacVim+Iterm2+tmux stack already for several years.
Today I noticed, that my vim works really slow when I try to open and edit quite large `routes.rb` or `schema.rb` files in Rails project.
On the other hand when I use MacVim in separate window - then it works fine.

My first suspect was an iTerm2. I tried several other terminal emulators, but nothing really helped.
[alacritty](https://github.com/jwilm/alacritty) looked promissing, actually it was a bit faster then regular iTerm2, but nothing changed significantly.

Then I found out that vim without syntax highlighting works really fast, but this wasn't an option for me, since I do a lot of development in my daily life.

After reading several posts about vim performance optimizations, I found that the reason of my specific case was `foldmethod=syntax`.
I can't even remember when did I introduce it in my vimrc, but switching it off helped me a lot.

Thanks to [https://stackoverflow.com/questions/22949067/macvim-quite-slow-when-syntax-is-set-to-ruby](https://stackoverflow.com/questions/22949067/macvim-quite-slow-when-syntax-is-set-to-ruby).
