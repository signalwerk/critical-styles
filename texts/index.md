---
title: Critical Styles and PostCSS
description: Process Critical Styles and PostCSS for fast renderings.
---

# Speed up webpage rendering with critical CSS – a realistic approach

To get the best user experience on Websites  is crucial. While on broadband the performance and optimization of a  


The first meaningful paint of a Website in our browsers is crucial for the user experience. While developers often work on a broadband desktop computer, the final user might be in a 3G mobile situation and is waiting for the website to get slowly loaded


## Traditional blockin CSS loading
External style sheets in the `<head />` of a website prevent the browser from start rendering until these files are loaded and interpretet. While [Render Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css) is loading a white viewport is visible and the user has no other option than to wait. Once the CSS is loaded the CSSOM (CSS Object Model) and DOM (Document Object Model) are finaly interpretet the website gets laid out and rendered.


```html
<html lang="de">
   <head>
      <title>Title</title>
      <link rel="stylesheet" href="styles.css" />
   </head>
   <body>
     <!-- content of website -->
   </body>
</html>
```

<link rel="preload" as="style" href="style.css" onload="this.rel='stylesheet'">


* 26.08.2019 – 3.5h
* 27.08.2019 – 2.5h





External style sheets prevent browsers from rendering the page until the entire CSS is downloaded and parsed. They do not start painting the page. There is also a so-called initial experience, which should fit in 14 kB and in a single HTTP request.


 Externe Stylesheets verhindern, dass Browser die Seite darstellen, bis das gesamte CSS heruntergeladen und analysiert ist. Sie fangen nicht an, die Seite zu malen. Außerdem gibt es eine so genannte Initialerfahrung, die in 14 kB und in einen einzelnen HTTP-Request passen sollte.
281/5000
External style sheets prevent browsers from rendering the page until the entire CSS is downloaded and parsed. They do not start painting the page. There is also a so-called initial experience, which should fit in 14 kB and in a single HTTP request.


##


# First Meaningful Paint

First Contentful Paint
2.3 s
Speed Index
9.8 s
Time to Interactive
15.3 s
First Meaningful Paint
8.7 s
First CPU Idle
12.4 s
Max Potential First Input Delay
1,420 ms






## test
Hello

```
<link rel="stylesheet" href="https://raw.githack.com/signalwerk/signalwerk.styles/gh-pages/styles/main.critical.css" media="all" />
<link rel="preload" as="style" onload="this.onload=null;this.rel='stylesheet'" href="https://raw.githack.com/signalwerk/signalwerk.styles/gh-pages/styles/main.rest.css" media="all" />
```

```
<!DOCTYPE html>
<html lang="de">
  <head>
    <meta charset="utf-8">
    <title>title</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <!-- page content -->
  </body>
</html>
```

## Blog
* lazy load images → https://css-tricks.com/a-deep-dive-into-native-lazy-loading-for-images-and-frames/
* lazy loading https://addyosmani.com/blog/lazy-loading/
* lazy spec https://github.com/whatwg/html/pull/3752
* responsive image FUIF https://css-tricks.com/fuif-responsive-images-by-design/
* JPEG XP https://developers.google.com/web/tools/lighthouse/audits/webp
* JPEG XL https://jpeg.org/jpegxl/index.html
* https://www.liip.ch/en/blog/things-you-should-know-about-responsive-images




## General

The purpose of the blog post ist to explain how to split CSS files in two stages:

*   CSS that blocks the rendering process – critical styles
*   CSS that will be loaded as soon as possible but not blocking the rendering

There will be a general expose plus a technical help how to do that kind of processing.

## Why – Topic

The quicker you have the first impression the more fluent the web experience feels. Plus you basically also just sell more... 

## Why – Me

Because I made some experiments the last couple weeks with new workflows in that regard. Plus I switched about 1–2 years ago from SCSS to PostCSS.

## Why for Liip

A better user experience helps everybody. Plus I think that technic is not (often) used at Liip. I just checked 1–2 sites and just saw blocking CSS.



## Budget

### Basic – 4.75h

*   Blog-Post 
*   Images/Graphics about HTML loading and how the rendering happens
*   Some light Code examples
*   Header-Image of the Blog-Post

### Extended – 7.5h

*   see Basic
*   GitHub repo with a webpack setup to test/see how to setup PostCSS and the automated CSS-splitting
*   Advanced example how to use that technic to have a clever Image-Setup where you get the right image-size depending on your layout and not on approximations solved in srcset/sizes of img-tag

## Licence

I would like to see a Creative Commons Licence on the Content and a MIT Licence on the code.

## Others

I will check with following Liipers for PostCSS exchange:

*   Ingvi Jonasson, Bern 
*   Marin Aeschbach, Zurich

*   No labels
*   [Edit Labels](# "Edit Labels (l)")
