---
title: sass concepts:mixins
category: SCSS
description: a quick guide to sass mixins 
layout: post
tags:
- sass
- scss
- mixins
---


Rather than typing the same rules over and over again in various declarations, use mixins to define a group of styles just once and refer to it anytime those styles are needed.

Say you have a certain heading style for a title that appears in various locations on your site/page.

The `CSS` for these titles is identical which is a perfect situation for a `mixin`.

First,define a mixin in `Sass` using the `@mixin` directive on top of your `.scss` file or in a separate mixin file:


```scss
@mixin mytitles-style {
    margin:0 0 10px 0;
    font-size:19px;
    font-weight:bold;
    text-transform:uppercase;
    }

```

Once defined, you can now refer to this `mixin` anywhere to insert those styles by using the `@include` directive.

For example, to style all `h1` elements for the main section of a page using the mixin:

```scss
section.main h1 {
    @include mytitles-style;
}
```

`Sass` will replace the mixin with its values in `CSS` output.

Say you also want to style `h2` elements in the sidebar the exact same way.

Later in the stylesheet you can call the same mixin and it will compile the same rules:

```scss
section.secondary h2 {
    @include mytitles-style;
}
```

mixins help in avoiding duplicating shared styles or adding a class to the markup that both headings could theoretically share.

Mixins can be icluded with additional rules as well:

```scss
section.secondary h2 {
    @include mytitles-style;
    color:dark-grey;
}
```

Shared styles can be abstracted into mixins,and you'll still have the ability to override or augment those styles with additional rules.This makes `Sass` much more powerful!!

### Mixin arguments

mixins also take arguments which can be passed when the mixin is called.

For example,adding an argument for specifying a background-color along with the `mytitles-style` mixin :


```scss
@mixin mytitles-style($background-color) {
    margin:0 0 10px 0;
    font-size:19px;
    font-weight:bold;
    text-transform:uppercase;
    background-color:$background-color;
    }
```
When calling the mixin,you can now pass the background-color to it along with other rules:

```scss
section.secondary h2 {
    @include mytitles-style(orange);
    color:dark-grey;
}
```

### multiple arguments

Add multiple arguments by separating the values with commas in the mixin definition:

```scss
@mixin mytitles-style($background-color,$font-family) {
    margin:0 0 10px 0;
    font-size:19px;
    font-weight:bold;
    text-transform:uppercase;
    background-color:$background-color;
    font-family:$font-family;
    }

```

Calling the mixin from two different selectors, passing different arguments for background color and font-family:

```scss
section.main h2 {
    @include mytitles-style(orange,ubuntu);
    color:dark-grey;
}
```

```scss
section.secondary h2 {
    @include mytitles-style(orange,open-sans);
    color:dark-grey;
}
```



### some mixin use cases in CSS3

* **border-radius**

A mixin for handling CSS3 rounded corners in all browsers, with an argument for the radius value:

```scss
@mixin rounded($radius) {
    -webkit-border-radius:$radius;
    -moz-border-radius:$radius;
    border-radius:$radius;
    }
```
We can then make anything on the page rounded by calling that mixin:

```scss
li a img {
    float:right;
    margin:0 10px 0 0;
    padding:5px;
    border:1px solid black;
    @include rounded(3px);
    }
```

```scss
div.module {
    float:left;
    margin:0 10px 0 0;
    @include rounded(14px);
    }
```

* **box-shadow**

A mixin for creating drop shadows in CSS3 that gives us the ability to pass in values for the vertical and horizontal positions of the shadow, the amount of blur and the color:

```scss
@mixin shadow($x, $y, $blur, $color) {
    -webkit-box-shadow:$x $y $blur $color;
    -moz-box-shadow:$x $y $blur $color;
    box-shadow:$x $y $blur $color;
    }
```
Adding this mixin to the previous div.module example, making the shadow appear straight from the top, down 1px, with 2px of blur, and balck at 50% opacity:

```scss
div.module {
    float:left;
    margin:0 10px 0 0;
    @include rounded(14px);
    @include shadow(0, 1px, 2px, rgba(0,0,0,0.5));
    }
```

There is no need to write those vendor-prefix stacks over and over.Write once, reuse whenever you like.


>It's good practice to create a mixin library say `_mixins.scss` where all your mixins live,and use `@import` rule to pull the mixin into the main `.scss` file.This will make maintainance of your code easier and save on HTTP connections.


















-----



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


