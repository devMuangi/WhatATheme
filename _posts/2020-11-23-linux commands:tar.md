---
title: linux commands:tar
category: Unix
description: a quick guide to the tar command 
layout: post
tags:
- linux
- terminal
- tar
---


`tar` is used to create an archive,grouping multiple files in a single file.

For example :

`$ tar -cf archive.tar file1 file2`

Creates an archive named `archive.tar` which contains `file1` and `file2`.

>The c option stands for create.The f option is used to write to file the archive.

Use:

`$ tar -xf archive.tar`

to extract files from an archive in the current folder.

>the x option stands for extract.

To extract them to a specific directory,use:

`$ tar -xf archive.tar -C directoryname`

List files contained in an archive:

`$ tar -tf archive.tar`

`tar` is often used to create a **compressed archive**,gzipping the archive using the `z` option:

`$ tar -czf archive.tar.gz file1 file2`

>this is just like creating a tar archive,and then running gzip on it.

To unarchive a gzipped archive,`gunzip` or `gzip -d` can be used and then unarchiving it,but `tar -xf` will recorgnize it's a gzipped archive and do it automatically.

`$ tar -xf archive.tar.gz`



-----





[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


