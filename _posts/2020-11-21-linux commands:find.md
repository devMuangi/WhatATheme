---
title: linux commands:find
category: Unix
description: a quick guide to the find command 
layout: post
tags:
- linux
- terminal
- find
---


Use the `find` command to recursively find files and folders matching a particular search pattern.

For example,find all files under the current tree that have the `.js` extension and print the relative path of each file:

`~$ find . -name '*.js'`


> The special character `*` tells the terminal to print relative path of each file.The quotes tells the shell to avoid interpreting special characters

Find directories under the current tree matching the name `"src"`:

`~$ find . -type d -name src`

Use `-type f` to search only files or `-type l` to only search symbolic links.

`-name` is case sensitive ,use `-iname` to perform a case-insesitive search.

You can search under multiple root trees:

`~$ find folder1 folder2 -name filename.txt`

Find directories under the current tree matching the name "node_modules" or "public":


`~$ find . -type d -name node_modules -or -name public`

Also exclude a path,using `-not -path`:


`~$ find . type d -name '*.md' -not -path 'node_modules'`

Search files that have more than 100 characters(bytes) in them:


`~$ find . -type f -size +100c`

Search files bigger than 100KB but smaller than 1MB:


`~$ find . type f -size +100k -size -1M`

Search files edited more than 3 days ago: 


`~$ find . -type f -mtime +3`

Search files edited in the last 24 hours:

`~$ find . -type f -mtime -1`

You can also delete all the files matching a search by adding the `-delete` option.This deletes all the files edited in the last 24 hours:

`~$ find . -type f -mtime -1 -delete`

You can execute a command on each result of the search.

For example run `cat` to print the file content:

`~$ find . -type f -exec cat {} \;`




[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


