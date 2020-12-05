---
title: linux commands:gzip
category: Unix
description: a quick guide to the gzip command 
layout: post
tags:
- linux
- terminal
- gzip
---


Use the `gzip` command's compression protocol [LZ77](https://en.wikipedia.org/wiki/LZ77_and_LZ78){:target="blank"} to compress a file:

`$gzip filename`

The file will be appended with a `.gz` extension after succesfull compression and the original file will be deleted.

Use the `-c` option and output redirection to write the output to the `filename.gz` file to prevent deleting the original file:

`$gzip -c filename > filename.gz`

>The -c option specifies that output will go to the standard output stream,leaving the original file intact

You can also use the `-k` option:

`$gzip -k filename`

There are various levels of compression.The more the compression, the longer it will take to compress and decompress.Levels range from 1 (fastest, worst compression) to 9 (slowest, better compression),the default is 6.

Choose a specific level with the `number` option:

`$gzip -3 filename`

Compress multiple files by listing them:

`$gzip filename1 filename2`

Compress all the files in a directory recursively using `-r` option:

 `$gzip -r folder`

Use the `-d` option to decompress a file:

 `$gzip -d filename.gz`





[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


