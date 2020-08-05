---
layout: post
title: "Vim configuration using Git"
tagline: "How I manage my Vim configurations and plugins"
category: Vim config
tags: [Vim, configuration, Git]
---
{% include JB/setup %}

In the version 8 of Vim there is a builtin mechanism to install plugins, as
described in [Vim: So long Pathogen, hello native package loading](https://shapeshed.com/vim-packages/),
so I stoped using Vundle and started using this simpler method already
supported by Vim-8.

## Tracking configurations and plugins with Git

So I created [this repository](https://github.com/frt/dotfiles) where I put all
my configuration files.  The configuration files for Vim are `.vimrc` and
`.vim`, and the plugins are all added as Git submodules.

So to add the Syntastic plugin I did:

```
cd ~/repos/dotfiles     # repository is already created and cloned
git submodule init
git submodule add https://github.com/vim-syntastic/syntastic.git .vim/pack/plugins/start/syntastic
git add .gitmodules .vim/pack/plugins/start/syntastic
git commit
```

And for configurations that are specific to some machine, I create a branch for
it, while the configurations common to all my machines I track in the `master`
branch.

## Linking the files in `$HOME` to the files in the repository

Then with the repository cloned into `~/repos/dotfiles` I did:

```
ln -s ~/repos/dotfiles/{.vimrc,.vim} ~/
```

So, when I change some configuration where I use to do it, it is automatically
tracked by Git. I only need to `commit` and `push` it.

## Removing a package

Removing a package is just a case of removing the git submodule.

By example:
```
git submodule deinit .vim/pack/plugins/start/syntastic
git rm .vim/pack/plugins/start/syntastic
rm -Rf .git/modules/.vim/pack/plugins/start/syntastic
git commit
```
