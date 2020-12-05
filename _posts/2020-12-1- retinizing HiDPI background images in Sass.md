---
title: retinizing HiDPI background images in Sass
category: SCSS
description: how to retinize background images in Sass 
layout: post
tags:
- sass
- scss
- HiDPI images
---

The rise of **High Dots Per Inch(HiDPI)** screens has created a challenge for web developers.Apple's retina screens,for example squeeze twice the number of pixels compared to that of a normal display.That means beautiful clarity and saying goodbye to fuzzy pixels.But only if you take the time to create graphics that reflect this super-sharp world.

For `<img>` elements on the page,this typically means creating images twice as large and compressing them to half the size using the width attribute in the markup.

>There are craftier ways to handle selective image-serving via media queries and Javascript,such as [Scott Jehl's brilliant Picturefill project](https://bkaprt.com/sass/14){:target="blank"}

Retinizing interfaces can result in a pile of repitition, referencing that media query and a second image every time you want to override normal resolution background images.

`Sass` makes this process painless.

We can create a mixin that handles all the heavy lifting :

```scss
  @mixin retinize($file, $type, $width, $height){
    background-image:url('../img/'+$file+'.'+$type);

    @media (-webkit-min-device-pixel-ratio: 1.5),
    (min--moz-device-pixel-ratio: 1.5),
    (-o-min-device-pixel-ratio: 3/2),
    (min-device-pixel-ratio:1.5),
    (min-resolution:1.5dppx){
    &{
        background-image: url('../img/' + $file + '-2x.' + $type);
        -webkit-background-size: $width $height;
            -moz-background-size: $width $height;
                 background-size: $width $height;
        }
    }
}
```
<br>
The first line of the mixin sets up the four arguments needed to build the right compiled code:

* The file name
* The type of image (JPG,GIF,PNG)
* Image width on screen
* Image height on screen

They are listed like so:

```scss
    @mixin retinize($file,$type,$width,$height)
```
<br>
The second line forms the normal-resolution background-image rule by stringing(concantenate) the arguments together.

```scss
  @mixin retinize($file, $type, $width, $height){
    background-image:url('../img/'+$file+'.'+$type);
    }
```
<br>
The next line is a media query that overrides the normal background image with the @2x version for devices that support a 1.5 ratio or higher.

```scss
  @mixin retinize($file, $type, $width, $height){
    background-image:url('../img/'+$file+'.'+$type);

    @media (-webkit-min-device-pixel-ratio: 1.5),
    (min--moz-device-pixel-ratio: 1.5),
    (-o-min-device-pixel-ratio: 3/2),
    (min-device-pixel-ratio:1.5),
    (min-resolution:1.5dppx){
  
}
```
<br>
The special `&` placeholder is used to reference(insert) the selector we are applying this media query to and that depends on where we've called the mixin from.

```scss
  @mixin retinize($file, $type, $width, $height){
    background-image:url('../img/'+$file+'.'+$type);

    &{
        background-image: url('../img/' + $file + '-2x.' + $type);
        -webkit-background-size: $width $height;
            -moz-background-size: $width $height;
                 background-size: $width $height;
        }
    }
}
```
<br>
The background size property(and it's `-webkit-` and `-moz-` prefixed equivalents),tells the browser what dimensions it's going to stuff that larger image into.

```scss
  @mixin retinize($file, $type, $width, $height){
    background-image:url('../img/'+$file+'.'+$type);

        background-image: url('../img/' + $file + '-2x.' + $type);
        -webkit-background-size: $width $height;
            -moz-background-size: $width $height;
                 background-size: $width $height;
        }
    }
}
```
<br>
This mixin can be used in serving HiDPI background images from any selector just by creating two image assets and one line of SCSS:

For example:

```scss
  li.instagram a {
      @include retinize('icon-instagram','png',24px,24px);
  }
```







-----



[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


