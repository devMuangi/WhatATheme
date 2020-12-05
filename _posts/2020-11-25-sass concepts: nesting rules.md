---
title: sass concepts:nesting rules
category: SCSS
description: how to nest css rules in sass
layout: post
tags:
- sass
- scss
- nesting 
---

Nest CSS rules inside each other instead of repeating selectors in separate declarations.


For example, consider a section of the markup below:


```HTML
    <section id="banner">  
    <div id="logo">
    <img src="logo.jpg" alt="logo">
    </div>

    <h1>Banner section</h1>
    <p>Banner section paragraph</p>
    ...
    </section>
```

Writing the `SCSS` can be as below:

```scss
#banner {
    margin:20px 30px
    border-bottom:4px solid white;

    #logo {
        float:left;
        margin:0 20px 0 0;
    
    img {
        display:block;
        opacity:0.89;
    }
    }

    h1 {
        padding:15px 0;
        font-size:54px;
        line-height:1;
        font-family:Jubilat;
        font-weight:bold;
    }

    p {
        align-text:centre;
    }

}

```

Which compiles into `CSS` below:

```scss
#banner {
    margin:20px 30px
    border-bottom:4px solid white;
}

#banner#logo {
        float:left;
        margin:0 20px 0 0;
        }
    
#banner#logoimg {
        display:block;
        opacity:0.89;
    }
    
#bannerh1 {
        padding:15px 0;
        font-size:54px;
        line-height:1;
        font-family:Jubilat;
        font-weight:bold;
    }

#bannerp {
        align-text:centre;
    }

```

Instead of repeating each element in the selector,`Sass` simplifies things by nesting to show hierarchy.


Nesting also reflects the markup structure.

>Excessive nesting can hinder readability.A few levels deep works great.

**Nesting namespaced properties**

Nest properties that share a namespace (e.g, font-family, font-size, font-weight, etc) like so:

```scss
h1 {
    padding:15px 0;
    font: {
        size:32px;
        family:ubuntu,serif;
        weight:bold;
    }
    line-height:1;
}
```

>This is possible in any namespace eg `text-`, `background-` ,etc.

Nesting in `Sass` means less typing using indentation to reflect the selector and property formation.

**Referencing parent selectors with &**

`Sass` adds the ability to reference the current parent selector using the ampersand as a special placeholder.

For example adding some hover effects on the h1 above :

```scss
h1 {
    padding:15px 0;
    font: {
        size:32px;
        family:ubuntu,serif;
        weight:bold;
    }
    line-height:1;

    &:hover{
        color:red;
        font-size:20px;
    }
}
```

The ampersand inserts the parent selector which will compile like so :

```css
h1 {
    padding:15px 0;
    font: {
        size:32px;
        family:ubuntu,serif;
        weight:bold;
    }
    line-height:1;

    h1:hover{
        color:red;
        font-size:20px;
    }
}
```
The ampersand is also useful in insering overrides that happen in the presence of a specific class.

For example, let's say we style paragraphs in the main section of the site,but we want a slightly different style on a specific page.We add a class to the body,and then we can use `&` to slip this overriding declaration into the main one :

```scss
section.main p {
    padding:15px 0;
    font: {
        size:32px;
        color:pink;
        family:ubuntu,serif;
        weight:bold;
    }
    line-height:1;

    body.store & {
        color:red;
        font-size:20px;
        size:19px;
    }
}
```

Will compile to :


```scss
section.main p {
    padding:15px 0;
    font: {
        size:32px;
        color:pink;
        family:ubuntu,serif;
        weight:bold;
    }
    line-height:1;

    body.store section.main p {
        color:red;
        font-size:20px;
        size:19px;
    }
}
```

On store pages or those with `<body class='store'>`, paragraphs will be smaller and the text color will be red instead of pink.

Instead of writing an entirely new declaration, we nested it using `&` to create a unique case and letting `Sass` reconstruct the full selector.







-----





[follow me on instagram](https://instagram.com/devmuangi){:target="blank"}


[**MORE ARTICLES**](/blog)


