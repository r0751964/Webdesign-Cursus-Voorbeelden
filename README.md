# Webdesign Voorbeelden
Enkele voorbeelden gezien in de cursus

Inhoudstabel  
- [Les 2, Favicon](#les-2-favicon)
- [Les 3, Fonts](#les-3-fonts)

___

## Les 2, Favicon
We gebruikten http://www.favicon.cc in 1e semester voor icoon te tekenen  
Maar nu gooien we png's in https://realfavicongenerator.net als coole guys

### Favicon in root:
```html
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="manifest" href="/site.webmanifest">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
```

### Favicon in een folder (bv genaamd iconfolder), niet in root
```html
<link rel="apple-touch-icon" sizes="180x180" href="iconfolder/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="iconfolder/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="iconfolder/favicon-16x16.png">
<link rel="manifest" href="iconfolder/site.webmanifest">
<link rel="shortcut icon" href="iconfolder/favicon.ico">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="msapplication-config" content="iconfolder/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

___

## Les 3, Fonts

### Webfonts gebruiken via CDN
```html
<link href=”https://fonts.googleapis.com/css?family=Baloo” rel=”stylesheet”>
```
```css
p {
  font-family: 'Baloo', cursive;'
}
```

### Gedownloade fonts gebruiken
```css
@font-face {
  font-family: 'cowboy_hippie_proregular';
  src: url('fonts/cowboy_hippie_pro-webfont.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}

h1 {
  font-family: 'cowboy_hippie_proregular', sans-serif;
}
```

#### Meerdere versies van een webfont laden
```css
@font-face {
  font-family: 'Material Icons';
  font-style: normal;
  font-weight: 400;
  src: url(https://example.com/MaterialIcons-Regular.eot); /* Internet Explorer 6-8 */
  src: local('Material Icons'),
    local('MaterialIcons-Regular'),
    url(https://example.com/MaterialIcons-Regular.woff2) format('woff2'),
    url(https://example.com/MaterialIcons-Regular.woff) format('woff'),
    url(https://example.com/MaterialIcons-Regular.ttf) format('truetype');
}
```
Goed om te onthouden: bestandstype - format
- .woff2 - format('woff2')
- .woff - format('woff')
- .ttf - format('truetype')




