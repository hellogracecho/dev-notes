# What is Link Type: `preload` 
[Reference - MDN definition](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/preload#what_types_of_content_can_be_preloaded)

[Reference - Google: Preload web fonts to improve loading speed](https://web.dev/codelab-preload-web-fonts/)

## Why `preload`?
Without font preloading, you might run into a situation where a browser is ready to load your site’s text, but it can’t because the font isn’t available yet. 
This is called a __FOIT__(Flash of Invisible Text). Or, it can also lead to a __FOUT__(Flash of Unstyled Text).

- __FOIT__ – the text is invisible until the font file is loaded.
- __FOUT__ – the text is visible, but using a system font. Once the font file loads, the text will switch to the new font style, which can cause a jarring experience for your visitors as the text appears to “jump” and “transform”.

Here is an example:
FOUT without preloading | With preloading
--- | ---
oops.. custom fonts are loaded later 😞 | fonts are nicely loaded right away 👍
![before](assets/preload-fonts-before.gif) | ![after](assets/preload-fonts-after.gif)

  
The reason you want to avoid this situation is that it slows down the perceived page load times for your visitors, which leads to degraded user experience. _Bad Site Performance_ 

With font preloading, you can force a visitor’s browser to load important fonts early on so that the browser can start painting text as soon as it’s ready, rather than potentially waiting to load the font.


## Basic Syntax 
You need to specify:
- The path to the resource in the `href` attribute.
- The type of resource in the `as` attribute.

```html
<head>
    <!-- Exmaples -->
    <link rel="preload" href="style.css" as="style">
    <link rel="preload" href="main.js" as="script">
    <link rel="preload" href="fonts/cicle_fina-webfont.woff2" as="font" type="font/woff2" crossorigin>
</head>
```

## WordPress 
Add your code in `<head>` section
```html
<head>
    <link rel="preload" href="fonts/cicle_fina-webfont.woff2" as="font" type="font/woff2" crossorigin="anonymous">
</head>
```

## Shopify
[Reference - Shopify](https://sections.design/blogs/shopify/preloading-fonts)

```html
<head>
    ...
    ...
    <link rel="preload" href="https://cdn.shopify.com/s/files/1/0580/3933/7151/files/BebasNeue-Regular.woff2?v=1627064891" as="font" type="font/woff2" crossorigin="anonymous">
    <link rel="preload" href="https://cdn.shopify.com/s/files/1/0580/3933/7151/files/fontawesome-webfont.woff2?v=1627066714" as="font" type="font/woff2" crossorigin="anonymous">

    <style>
        @font-face {
            font-family: 'Bebas Neue';
            font-weight: 500;
            font-style: normal;
            font-display: swap;
            src: url('https://cdn.shopify.com/s/files/1/0580/3933/7151/files/BebasNeue-Regular.woff2?v=1627064891') format('woff2'),
            url('https://cdn.shopify.com/s/files/1/0580/3933/7151/files/BebasNeue-Regular.woff?v=1627064891') format('woff');
        }
        
        @font-face {
            font-family: "FontAwesome";
            font-weight: normal;
            font-style : normal;
            font-display: auto;
            src: url('https://cdn.shopify.com/s/files/1/0580/3933/7151/files/fontawesome-webfont.woff2?v=1627066714') format('woff2'),
            url('https://cdn.shopify.com/s/files/1/0580/3933/7151/files/fontawesome-webfont.woff?v=1627066714') format('woff');
        }
    </style>
</head>

```