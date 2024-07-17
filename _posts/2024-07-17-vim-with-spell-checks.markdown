---
layout: post
title: "Vim with spell checks"
date: 2024-07-17 16:59:35 +1000
categories: til
tags: til vim
author: Eduardo Ramos
---
I still don't know if I am not a good writer because I don't write anything, or I don't write anything because I am not a good writer. Maybe it's just a matter of practising it more.

In any case, I admire people who writes well, and who also share their thoughts and knowledge to others. So, what if I could overcome this limitation of mine, as a person who does not write, and become someone I would admire? :D

That's why I started writing here. Put my thoughts and learns out while I practise my writing skills.

Today, my good friend [Lucas Caton](https://www.lucascaton.com/about), reviewed my previous posts and spotted a few mistakes I made. Also, he recommended me to use some kind of plug-in in my editor, to make it easier to see. What a great idea!

Then I went to search on the web, how I could have such feature enabled on my Vim, and the first result that DuckDuckGo gave me served perfectly. In short, `:set spell spelllang=en` would make it happen.

Initially, I only plan to use spell checking when editing markdown files, so I added the following like into my .vimrc file:
```
autocmd FileType markdown setlocal spell spelllang=en_au
```
It will tell my Vim to enable spell checking using Australian English dictionary whenever I am editing a markdown file. Wrong words will be highlighted, then I can use the keys commands `]s` and `[s` to jump through these words. Use `z=` over the words in order to get suggestions.

Check the article linked below for more detailed information. I loved it!

Thanks Lucas for this amazing idea.

Reference:
* [Using Spell Checking in Vim](https://www.linux.com/training-tutorials/using-spell-checking-vim/)
