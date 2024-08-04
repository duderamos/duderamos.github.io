---
layout: post
title: "Install/Update vim packs"
date: 2024-08-01 13:33:25 +1000
categories: til
tags: til vim packs
author: Eduardo Ramos
---
There are heaps of ways to make vim even a better editor, when adding packs created by other vim lovers. Packs can also be referred as plug-ins.

Some people manage these packs/plug-ins using [pathogen](https://github.com/tpope/vim-pathogen) or [Vundle](https://github.com/VundleVim/Vundle.vim). I personally rather use the native approach, which seems to have been added in Vim 8. [man page](https://raw.githubusercontent.com/vim/vim/master/runtime/doc/version8.txt)

In very short, we just need to clone the pack/plug-in git repository into the path `~/.vim/pack/plugins/start/<pack name>`. In case you keep your vim configuration version controlled in git, you can add your packs as submodules. Then, your setup will stick on the latest version when you installed.

### Examples

Installing a pack:
```shell
git submodule add https://github.com/duderamos/foo.git pack/plugins/start/foo
git commit -m "Install foo"
```

Remove a pack:
```shell
cd ~/.vim
git submodule deinit pack/plugins/start/foo
git rm -r pack/plugins/start/foo
git commit -m "Remove foo"
rm -r .git/modules/pack/plugins/start/foo
```

References:
* [Using git-submodules to version-control Vim plugins](https://gist.github.com/duderamos/a4bcf2477031debdf1673c93703539ee) *Forked from https://gist.github.com/manasthakur/d4dc9a610884c60d944a4dd97f0b3560*
* [Vim 8 package management](https://www.danielfranklin.id.au/vim/vim-8-package-management/)
