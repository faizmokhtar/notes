---
title: "How to prettify git diff output with diff-so-fancy"
date: 2018-08-13T08:37:39.000Z
categories:
  - Development
tags:
  - git
  - tools
comments: false
---

I find it quite hard to make sense of the output from `git diff`. It is somewhat off-putting and ugly for me. [`diff-so-fancy`][1] is an open source project to solve this problem and help make your diff much less uglier.

## Installation

There are a lot of ways to install it but I prefer to install all my tools with Brew. 
So run the following in your terminal:

```bash
$~ brew install diff-so-fancy
```

## Configuration

To use `diff-so-fancy`, you have to set it up globally. Run the following:

```
$~ git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"
```

This will change your `~/.gitconfig` like so

```toml
[core]
    ... // other settings
    pager = diff-so-fancy | less --tabs=4 -RFX
```

When you run `git diff`, you will noticed how much of an improvement that `diff-so-fancy`
brings. There are a few more customizations that can be done. Try it on your own.

[1]:https://github.com/so-fancy/diff-so-fancy
