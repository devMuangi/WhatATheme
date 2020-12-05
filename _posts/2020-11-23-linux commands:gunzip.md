---
title: linux commands:gunzip
category: Unix
description: a quick guide to the gunzip command 
layout: post
tags:
- linux
- terminal
- gunzip
---


`gunzip` is equivalent to `gzip`,except the `-d` option is always enabled by default:

`$ gunzip filename.gz`

Will gunzip and remove the `.gz` extension,putting the result in the filename file.If that file exists,it will overwrite it.

Extract to a different filename using output redirection:


`$ gunzip -c filename.gz > anotherfilename`





[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


