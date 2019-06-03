# Webdesign Voorbeelden
Enkele voorbeelden gezien in de cursus

Inhoudstabel  
- [Les 2, Favicon](#les-2-favicon)
- [Les 3, Fonts](#les-3-fonts)
- [Les 4, .htaccess en errorpages](#les-4-htaccess-en-errorpages)
- [Les 5, Update mediaqueries](#les-5-update-mediaqueries)
- [Les 6, Responsieve afbeeldingen](#les-6-responsieve-afbeeldingen)
- [Les 8, Formulieren en formulierafhandeling](#les-8-formulieren-en-formulierafhandeling)


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

## Les 4, .htaccess en errorpages
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

___

# Les 6, Responsieve afbeeldingen

Allemaal soorten afbeeldingen, fun voor de hele familie:
```html
<img src="huis.svg" alt="Is svg huis">
<figure>
  <img src="huis.png" alt="Is png huis">
  <img src="huis.jpg" alt="Is jpeg huis">
  <figcaption>Huizen</figcaption>
</figure>
```

Bij gebruik van figures is er soms bij default een left marge
```css
figure {
  margin-left: 0;
}
```

Foto cirkelvormig weergeven:
```css
img {
  border-radius: 50%;
  border: 5px solid #000;
  box-shadow: 3px 3px 3px #666;
  background-color: lightblue;
  color: #000;
}
```
Afbeeldingen in vage vormen weergeven is (niet zo goed) ondersteund via clip-path, gebruik gewoon https://bennetfeely.com/clippy

Filters:
```css
img {
  filter: grayscale(100%);
```
Andere filters: blur(), brightness(), contrast(), drop-shadow(), hue-rotate(), invert(), opacity(), saturate(), sepia()
En nog meer: https://developer.mozilla.org/en-US/docs/Web/CSS/filter

Achtergrondimage:
```css
body {
  background-image: url(ster.png);
  background-repeat: no-repeat;
  /*background-size: 100px 200px;*/ /* Vaste hoogte */
  background-size: cover; /* Contain is blijkbaar default, cover is ook handig */
  background-position: center;
}
```
Oversized background-image:
```css
body {
  color: black;
  background-color: #909b6f;
  background-image: url(afbeelding.jpg);
  background-position: center;
  background-attachment: fixed;
  background-size: cover;
}
```
Bij achtergrondimages, gebruik background-color gerelateerd aan de image: www.colorexplorer.com/imageimport.aspx
Of gebruik patterns: https://leaverou.github.io/css3patterns/
Of gebruik gradients: https://cssgradient.io/

Responsive image css:
```css
img {
  max-width: 100%;
  vertical-align: middle;
}
```
PS: blijkbaar adviseert Google Audit om width="waarde" en height="waarde" in HTML te schrijven maar ???

Meerdere versies van afbeelding (jpg/png/gif) voor verschillende pixeldensiteiten:
```html
<img src="afbeelding-360w.jpg" alt="afbeelding"
     srcset="afbeelding-360w.jpg 360w, afbeelding-450w.jpg 450w, afbeelding-675w.jpg 675w, afbeelding-765w.jpg 765w"
     sizes="(min-width: 765px) 765px">

<!-- Alternatief, nog iets minder ondersteund (en moet mogelijk in een figure) -->
```html
<picture>
  <source media="(min-width: 401px)" srcset="auto-700w.jpg">
  <img src="auto-500w.jpg" alt="zelfrijdend autootje">
</picture>
```
Vanaf viewpoortbreedte van 765px, wordt de afbeeldingsbreedte beperkt tot 765px
(Wanneer je via de console in mobile view gaat, kan je het uittesten met de DPR setting bovenaan)

___

## Les 8, Formulieren en formulierafhandeling

Toegankelijke formulieren gebruiken labels:
```html
<p>
  <label for="naam">Naam<sup>*</sup></label>
  <input type="text" id="naam" name="gebruikersnaam" placeholder="Typ hier je naam">
  <!-- Label for en input id zijn gerelateerd -->
  <!-- ID's moeten uniek zijn, moet beginnen met een letter, alleen uit kleine letters bestaan, en geen blanco's bevatten -->
  <!-- Name wordt gebruikt in PHP, geef het alleen aan inputs (niet aan form of iets anders) -->
</p>
<p>
  <label for="wachtwoord">Wachtwoord</label>
  <input type="password" id="wachtwoord" size="15" maxlength="20" name="passwoord" value="demo">
</p>
<p>
  <input type="hidden" name="veiligheidscode" value="123">
  <!-- Geeft info door dat niet door de gebruiker moet worden ingegeven -->
  <!-- Wordt IIRC soms ook gebruikt om bots te checken die alles automatisch invullen -->
</p>
<p>
  <label for="url">URL</label>
  <input type="url" id="url" name="url" placeholder="url?">
  <!-- Geldige waardes zijn scheme://deRest (bv https://example.com) of een relatieve url -->
</p>
<p>
  <!-- Text met regex (regular expression / reguliere expressie) pattern -->
  <label for="postcode">Postcode</label>
  <input type="text" id="postcode" name="postcode" pattern="[0-9]{4}">
  <!-- Vaak voorkomende regex: http://html5pattern.com/ -->
</p>
<p>
  <label for="email">Email</label>
  <input type="email" id="email" name="email" required>
  <!-- Required attribuut zorgt ervoor dat het ingevuld moet zijn vooraleer te drukken -->
</p>
<p>
  <label for="range">Range</label>
  <input type="range" id="range" name="range" min="0" max="100" step="5" value="40">
</p>
<p>
  <label for="number">Nummer</label>
  <input type="number" id="number" name="number" value="40">
</p>
<p>
  <label for="stepnumber">Nummer met step</label>
  <input type="number" id="stepnumber" name="stepnumber" min="0" max="100" step="5" value="40">
</p>
<p>
  <label for="date">Datum</label>
  <input type="date" id="date" name="date">
</p>
<p>
  <label for="week">Week</label>
  <input type="week" id="week" name="week">
</p>
```
