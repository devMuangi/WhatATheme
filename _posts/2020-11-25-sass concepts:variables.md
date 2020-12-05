---
title: sass concepts:variables
category: SCSS
description: a quick guide to sass variables 
layout: post
tags:
- sass
- scss
- variables 
---

Variables in `Sass` are defined like regular `CSS` rules using `$` like so:


```scss
    $color-main:black;
    $color-light:grey;

    $font-main:ubuntu;
    $font-second:Proxima Nova;

```

Once defined,they can be invoked within declarations:

```scss
body {
    color:$color-main;
    background-color:$color-light;
    font-family:$font-main;
}
```

`Sass` will replace the variables with their values in `CSS` output.

>Wholesale changes to a stylesheet's repeated patterns are updated in seconds with `Sass` variables.



-----



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


