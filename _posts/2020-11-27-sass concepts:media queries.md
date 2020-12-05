---
title: sass concepts:media queries
category: SCSS
description: a quick guide Sass media queries 
layout: post
tags:
- sass
- scss
- media queries 
---

One of the foundations of building responsive websites is the ability to "listen" to the browser's viewport for varying dimensions and then apply certain styles based on those dimensions using the `CSS` media query.

This is the connerstone of creating flexible layouts that adapt to different devices.

For instance, you may want to adjust the width of a certain element should the browser be less than 800px wide, using a media query:

```scss
   section.main{
       float:left;
       padding:.5px;
       font-size:normal;
       width:70%;
       color:white;
       background:green;
    }

    @media screen and (max-width:800px) {
        section.main{
            float:none;
            width:auto;
        }
    }
```

### Introducing Sass's nested media queries.

In Sass, you can nest media queries inside the original declaration and they will bubble up into their own declarations when the stylesheet is compiled :


```scss
   section.main{
       float:left;
       padding:.5px;
       font-size:20px;
       width:70%;
       color:white;
       background:green;
  
       @media screen and (max-width:800px){
            float:none;
            width:auto;
        }

        @media screen and (max-width:500px){
            font-size:12px;
            line-height:1.5;
        }
    }
```
<br>
Nesting media queries avoids rewriting the selector each time you want to make adjustments for various breakpoints.

>It’s immensely convenient that the media-query declarations slot right under the original selector.I find it much easier to understand what’s happening to an element under varying viewports by having the media queries nearby in context, rather than gathered at the end of the stylesheet or in a separate document


### Using Variables to define breakpoints.

The breakpoints defined in the previous example may change.It'd be great to define them once and be able to edit them in one spot, say in `variables.scss` instead of relying on static device widths :

```scss
    $width-small: 500px;
    $width-medium: 800px;
    $width-large: 1200px;
```
<br>
With the breakpoints defined as Sass variables, we can(as of Sass 3.2) refer to these whenever we use nested media queries throughout the document for example:

```scss
   section.main{
       float:left;
       padding:.5px;
       font-size:20px;
       color:white;
       background:green;
  
       @media screen and (max-width: $width-large){
            float:left;
            width:70%;
        }

        @media screen and (max-width:$width-medium){
            float:none;
            width:auto;
        }

        @media screen and (max-width:$width-small){
            font-size:12px;
            line-height:1.4;
        }
    }
```
<br>
If we later decide to tweak those breakpoints,we only edit variables once,and sass will take care of updating them wherever we use them.

>This helps tremendously during the initial development of a responsive design, when those breakpoints are a moving target depending on the design requirements and the way the design needs to adapt.
<br>

**We can add or subtract from the breakpoint's value**:


```scss
   section.main{
       float:left;
       padding:.5px;
       font-size:20px;
       color:white;
       background:green;
  
       @media screen and (max-width: $width-large + 20){
            float:left;
            width:70%;
        }

        @media screen and (max-width:$width-medium + 10){
            float:none;
            width:auto;
        }

        @media screen and (max-width:$width-small + 30){
            font-size:12px;
            line-height:1.4;
        }
    }
``` 
<br>

**We can also define an entire media query as a variable not just the numeric value**:

```scss
   $mobile-first:"screen and (min-width: 300px)";

   @media #{$mobile-first} {
       #content{
           font-size:14px;
           line-height:1.5;
       }
   }
```
<br>

>The interpolation brackets `#{}` is a special way to alert Sass to compile something within a selector or property name.

### Combining @content blocks and mixins

Pass entire blocks of styles to a mixin and Saas will place those blocks back into the declaration that calls the mixin using `@content` directive.

Below is a responsive mixin that handles three different breakpoints,with `@content` placeholders for whatever styles we'd like to include for each breakpoint.Small,medium and large breakpoints have been defined using variables.


```scss
      $width-small: 400px;
      $width-medium: 760px;
      $width-large: 1200px;
  
      @mixin responsive($width) {
            @if $width == wide-screens {
                @media only screen and (max-width:$width-large){ @content; }
            }
            @else if $width == medium-screens {
                @media only screen and (max-width:$width-medium){ @content; }
            }
            @if $width == small-screens {
                @media only screen and (max-width:$width-small){ @content; }
            }
        }  
``` 
<br>
With this single mixin setup, we can now call it from any declaration using a compact pattern that reflects the way we think about things:


```scss
      #content {
          float: left;
          width: 70%;
          @include responsive(wide-screens) {
               width:80%
            }
          @include responsive(medium-screens) {
               width:50%;
               font-size:14px;
            }
          @include responsive(small-screens) {
               float:none;
               width:100%;
               font-size:12px;
            }
      }
```
<br>
>Using `@content` blocks for writing  contextually-placed media queries makes responsive design a heck of a lot simpler with less repitition.

It's easier to grasp how an element will be adjusted across device widths-such as how a heading's font-size will vary as the width of the viewport narrows.

The entire progression is spelled out in one spot:

```scss
      #content {
          font-size:55px;
          @include responsive(wide-screens) {
               font-size:50px;
            }
          @include responsive(medium-screens) {
               font-size:30px;
            }
          @include responsive(small-screens) {
               font-size:20px;
            }
      }
```







-----



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


