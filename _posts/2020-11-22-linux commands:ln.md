---
title: linux commands:ln
category: Unix
description: a quick guide to the ln command 
layout: post
tags:
- linux
- terminal
- ln
---


Use the `ln` command to create links.

A link is a file that points to another file.

They are silmilar to shortcuts in windows.

There are two types of links: **Hard links** and **Soft links**

### Hard Links

They are rarely used because some limitations:

* They can't link to directories and 

* they can't link to external filesystems

A hard link is created using:


`~$ ln <original> <link> `

For example, create a hard link to a file called project.txt as shown:

 `~$ ln project.txt projectlink.txt`

The new hard link is indistinguishable from a regular file.

Any time any of those files is edited,the content will be updated for both.

If the original file is deleted,the link will still contain the original file content,as that's not removed until there is one hard link pointing to it.

### Soft Links

Are more powerful as they can be linked to other filesystems and to directories.

When the original is deleted,the link will be broken.

create a soft link using the `-s` option of `ln`:


`~$ ln -s project.txt projectlink.txt`


When you list the file using `ls -al`,there is a special `l` flag and it is colored differently if you have colors enabled:

![ln screenshot](/assets/images/2020-11-22-linux commands:ln.png)









[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


