---
title: sass concepts:@extend
category: SCSS
description: a quick guide to the @extend function
layout: post
tags:
- sass
- scss
- extend 
---

Use Sass's `@extend` function to chain together styles that are shared amongst multiple selectors.

For example,say you have two buttons on your page with the same styling apart from the background color.

The first option is to give each button its own class say `.background-green` and `.background-red` and style them accordingly.The problem with this method is that you will have to repeat the same CSS rules apart from background color property.

To solve this, use the `@extend` function to include styles from another class and then add extra overriding rules to make a new unique style without duplicating the shared styles.




```scss
   .background-green{
       padding:.5px;
       font-size:normal;
       color:white;
       text-transform:uppercase;
       background:green;
    }
```

Use `@extend` to write the styles for the `background-red` button as below:


```scss
   .background-red{
    @extend .background-green;
    background:red;
    }
```

The button will have the styles of `.background-green` but the background will be overriten to red.

>Be careful not to use too much `@extend` in your site as the compiled `CSS` will start to look a bit hairy leading to monster declarations as a result of using the same class repeatedly throughout the stylesheet.Always keep tabs on how Sass compiles your work to `CSS`.



-----



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


