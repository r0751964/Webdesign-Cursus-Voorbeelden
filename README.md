# Webdesign Voorbeelden
Enkele voorbeelden gezien in de cursus

Inhoudstabel  
- [Les 2, Favicon](#les-2-favicon)
- [Les 3, Fonts](#les-3-fonts)
- [Les 4, .htaccess](#les-4-htaccess)
- [Les 5, Update mediaqueries](#les-5-update-mediaqueries)

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

___

## Les 4, htaccess
Voorbeeld goede .htaccess
```
Options All -Indexes

ErrorDocument 403 /403.html
ErrorDocument 404 /404.html
```

___

## Les 5, Update mediaqueries

### Belangrijk
Vergeet niet de viewport toe te voegen! De emmet-afkorting meta:vp werkt normaal, maar indien niet:
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Media queries met meerdere CSS bestanden
```html
<link ref="stylesheet" href="klein.css" media="screen and (min-width:500px)">
<link ref="stylesheet" href="groot.css" media="screen and (min-width:1100px)">
```

### Media queries in CSS
```css
@media screen and (min-width: 500px) {
  p {color: yellow;}
}

@media screen and (min-width: 1100px) {
  p {color: red;}
}
```

