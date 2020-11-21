---
title: shell commands:ls
category: Unix
description: a quick guide to the ls command
layout: post
tags:
- unix
- terminal
- linux
---

Use ls to list the contents inside a folder. 

Typing 

> ## `~my-project$ ls `

will list the contents that are inside the **my-project** directory.

Also , adding a folder name/path to ls lists the contents of the directory.

> ## `~$ ls/my-project `

will list the contents of the my-project directory.

ls accepts alot more options.

To view hidden files, type 

> ## `~my-project$ ls -a`

on your terminal.You will see directories that start with a dot.Example **.my-project** is a hidden file.

To get alot more information like file permissions ,file owner and file modified date, type 

> ## `~my-project$ ls -l`

on your terminal.

These arguments can also be combined.

Typing 

> ## `~$ ls -al`

on your terminal gives this information.

![Test Image](/assets/images/shell commands ls.png)

From left to right :

* the file permissions (and if your system supports
ACLs, you get an ACL flag as well)
* the number of links to that file
* the owner of the file
* the group of the file
* the file size in bytes
* the file modified datetime
* the file name



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)

