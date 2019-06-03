# Webdesign Voorbeelden
Enkele voorbeelden, zoals gezien in de cursus en eventueel aangepast/gemaakt door yours truly

[Link naar Theorie Website](https://r0751964.github.io/Webdesign-Theorie/)
[Link naar Theorie pure tekst, als je dat liever hebt](https://github.com/r0751964/Webdesign-Theorie/blob/master/README.md)
[Link naar Voorbeelden Website](https://r0751964.github.io/Webdesign-Cursus-Voorbeelden/)
[Link naar Voorbeelden pure tekst, als je dat liever hebt](https://github.com/r0751964/Webdesign-Cursus-Voorbeelden/blob/master/README.md)
[Link naar Handige Links Website](https://r0751964.github.io/Webdesign-Handige-Links/)
[Link naar Handige Links pure tekst, als je dat liever hebt](https://github.com/r0751964/Webdesign-Handige-Links/blob/master/README.md)

NOTE:
Ik heb hierin niets geschreven over Git of Bootstrap, omdat dat te specifiek is
En over jQuery omdat er geen tegoeie cursus van is.
Als je erover nadenkt, jQuery vat Javascript samen. Hoe ga je een samenvatting samenvatten? It's madness, I say. Madness.

Inhoudstabel  
- [Les 2, Favicon](#les-2-favicon)
- [Les 3, Fonts](#les-3-fonts)
- [Les 4, .htaccess en errorpages](#les-4-htaccess-en-errorpages)
- [Les 5, Update mediaqueries](#les-5-update-mediaqueries)
- [Les 6, Responsieve afbeeldingen](#les-6-responsieve-afbeeldingen)
- [Les 8, Formulieren en formulierafhandeling](#les-8-formulieren-en-formulierafhandeling)
- [Les 12, Sass](#les-12-sass)
- [Les 13, CSS3](#les-13-css3)


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

## Les 6, Responsieve afbeeldingen

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
  <form action="voorbeeld.php" methode="get">
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
  <p>
    <label for="month">Maand</label>
    <input type="month" id="month" name="month">
  </p>
  <p>
    <label for="time">Tijd</label>
    <input type="time" id="time" name="time">
  </p>
  <p>
    <label for="datetimelocal">Local Datetime</label>
    <input type="datetime-local" id="datetimelocal" name="datetimelocal">
    <!-- Werkt niet mogelijk niet op alle browsers -->
  </p>
  <p>
    <label for="color">Kleur</label>
    <input type="color" id="color" name="color">
  </p>
  <p>
    <label for="query">Zoeken</label>
    <input type="query" id="id" name="query">
    <!-- Dit heeft eigenlijk (nog) geen extra functionaliteit -->
  </p>
  <p>
    <label for="tel">Telefoonnummer</label>
    <input type="tel" id="tel" name="tel"
           pattern="0(\d{2,3}\/\d{6}|\d\/\d{7})">
    <!-- Dit heeft (zoals bij search) geen extra functionaliteit uit zichzelf -->
    <!-- Met een pattern is het wel nuttig (\d = [0-9]) -->
  </p>
  <p>
    <input type="checkbox" id="wagen" name="vervoer1" value="auto">
    <label for="wagen">Ik heb een eigen wagen</label>
  </p>
  <p>
    <input type="checkbox" id="fiets" name="vervoer2" value="fiets" checked>
    <label for="fiets">Ik heb een eigen wagen</label>
    <!-- Checked auto-checked de checkbox -->
  </p>
  <p>
    <input type="radio" id="rijbewijs" name="autorijden" value="ja">
    <label for="fiets">Ik heb een rijbewijs B</label>
    <!-- Radiobuttons die bij elkaar horen moeten dezelfde name hebben! -->
  </p>
  <p>
    <input type="radio" id="rijbewijs" name="autorijden" value="neen" checked>
    <label for="fiets">Ik heb geen rijbewijs B</label>
    <!-- Checked kan terug gebruikt worden voor iets automatisch aan te vinken -->
  </p>
  <p>
    <label for="opmerking">Graag hier uw opmerking:</label>
  </p>
  <p>
    <textarea  rows="5" cols="25" id="opmerking" name="feedback"></textarea>
  </p>
  <p>
    <label for="combobox">Hier is een combobox select</label>
  </p>
  <p>
    <select id="combobox" name="combobox">
      <option value="G">Als de size vd select niet gedefined is</option>
      <option value="T">Of gelijk is aan 1</option>
      <option value="H" selected>Krijg je een combobox!</option>
      <!-- Als de size vd select niet gedefined is, of gelijk is aan 1, krijg je een combobox! -->
      <!-- selected bij een select auto-selecteerd die option -->
    </select>
  </p>
  <p>
    <label for="eenkeuzeselect">Hier is een 1-keuze select</label>
  </p>
  <p>
    <select id="eenkeuzeselect" name="eenkeuzeselect">
      <option value="G">Als de size vd select groter is als 1</option>
      <option value="T" selected>Krijg je een 1 keuze select!</option>
      <option value="H">(Of hoe het ook noemt)</option>
      <!-- Als de size vd select groter is dan 1, krijg je een 1 keuze select! (Of hoe het ook noemt) -->
    </select>
  </p>
  <p>
    <label for="meerkeuzeselect">Hier is een meerkeuze select</label>
  </p>
  <p>
    <select id="meerkeuzeselect" name="meerkeuzeselect[ ]" multiple>
      <option value="G">Als het attribuut multiple wordt gegeven</option>
      <option value="M">En de name eindigt met [ ]</option>
      <option value="T" selected>Krijg je een meerkeuze select!</option>
      <option value="H">(Of hoe het ook noemt)</option>
      <!-- Als het attribuut multiple wordt gegeven en de naam eindigt met [ ] krijg je een meerkeuze select! (Of hoe het ook noemt)-->
      <!-- Blijkbaar pas voor 2ITF, maar staat in de cursus dus ??? -->
    </select>
  </p>
  <p>
    <label for="eenkeuzeselectOpt">Hier is een 1-keuze select met optgroup</label>
  </p>
  <p>
    <select id="eenkeuzeselectOpt" name="eenkeuzeselectOpt">
      <optgroup label="Fun voor">
        <option value="G">Als de size vd select groter is als 1</option>
        <option value="T" selected>Krijg je een 1 keuze select!</option>
      </optgroup>
      <optgroup label="De hele familie">
        <option value="H">(Of hoe het ook noemt)</option>
      </optgroup>
    </select>
  </p>
  <p>
    <label for="meerkeuzeselectOpt">Hier is een meerkeuze select</label>
  </p>
  <p>
    <select id="meerkeuzeselectOpt" name="meerkeuzeselectOpt[ ]" multiple>
      <optgroup label="Coole info">
        <option value="G">Als het attribuut multiple wordt gegeven</option>
        <option value="M">En de name eindigt met [ ]</option>
      </optgroup>
      <option value="T" selected>Krijg je een meerkeuze select!</option>
      <option value="H">(Of hoe het ook noemt)</option>
    </select>
  </p>
  <fieldset>
    <legend>Met legend geef je de fieldset een titel</legend>
    Met fieldset groepeer je enkele inputs in een kader!
  </fieldset>
  <p>
    <input type="submit" value="versturen!">
    <!-- Een gewone knop kan ook, maar dan moet je Javascript gebruiken en dat is teveel moeite -->
  </p>
  <p>
    <input type="reset" value="beginwaarden">
  </p>
</form>
```
Emmet:
- form:get
- form:post
- input
- input:p
- input:c
- input:r
- input:s
- input:reset
- ...

Form styling:
```css
input:focus {
  outline: none;
  border: 2px solid #f00;
  box-shadow: none;
}
input[type=date], input[type=number] {
  width: auto; /* Reset width */
}
input:invalid {
  background: #f8bdb2 url(invalid.png) no-repeat center right;
}
input:valid {
  background: #a8e0e5  url(valid.png) no-repeat center right;
}
```
Cursors aanpassen: http://www.echoecho.com/csscursors.htm


### PHP

```php
$_POST /* --> array opvragen van variabelen gestuurd via POST */
$_POST["var"] /* --> variabele var uit POST halen */
. /* strings aan elkaar plakken, bv: */ "<h1>Hallo, ".$_POST["voornaam"]." ".$_["achternaam"]."</h1>"
echo /* --> Zet string op scherm, meestal gebruikt voor HTML code te genereren */
isset() /* --> Returned true indien variabele bestaat, bv: */ isset($_POST["email"])
\n /* newline voor in de html code */
$_GET /* --> array opvragen van variabelen gestuurd via GET */
$_GET["var"] /* --> variabele var uit GET halen */
```

Validation.php:
```php
<div>
  <?php if (isset($_POST["voornaam"]) && $_POST["voornaam"] != "" && isset($_POST["achternaam"]) && $_POST["achternaam"] != "") echo "<h1>Hallo, ".$_POST["voornaam"]." ".$_POST["achternaam"]."</h1>\n"; else echo "<h1>Hallo, John Doe</h1>\n"; ?>
  <h3 class="mb-5">
  <em><?php if (isset($_POST["email"]) && $_POST["email"] != "") echo "Je email adres is ".$_POST["email"]."\n"; else echo "Je hebt geen email adres doorgegeven\n"; ?></em>
  </h3>
  <blockquote class="blockquote">
    <p class="mb-0"><?php if (isset($_POST["checkbox"]) && $_POST["checkbox"] == "ja") echo "Je wilt emails ontvangen op het doorgegeven email adres.\n"; else echo "Je wilt geen emails ontvangen.\n"; ?></p>
    <?php if (isset($_POST["bericht"]) && $_POST["bericht"] != "") echo "<h4>Bericht</h4><p class='blockquote-footer'>".$_POST["bericht"]."</p>\n"; else echo "<h2>Geen bericht</h2>\n"; ?>
  </blockquote>
</div>
```
En een link over HTTPS, ik betwijfel dat we hier iets specifiek uit moeten kennen https://imu.nl/seo/van-http-naar-https-stappenplan/

___

## Les 12, Sass

### Installatie
```
(Installeer Node JS)
npm install -g node-sass

(Indien gulp bestand aanwezig is)
npm install -g gulp-cli
gulp

(Indien gulp niet aanwezig is)
cd parentfolder/van/scss/folder/met/style.scss/in/
npm install browser-sync -g
node-sass scss -o css (De output van de scss komt in de folder css te staan, als gezegd in -o css)
browser-sync start --server "public_html" --files "public_html"

```

### Variabelen
```sass
$hoofdkleur:#f04c25;
$lettertype:verdana, sans-serif;
body {
  color:$hoofdkleur;
  font-family:$lettertype;
}
div {
  background-color:$hoofdkleur;
  font-family:$lettertype;
}
```

### Functies
```sass
$hoofdkleur:#f04c25;
$lettertype:verdana, sans-serif;
body {
  color:$hoofdkleur;
  font-family:$lettertype;
}
div {
  background-color:lighten(invert($hoofdkleur),50%);
  font-family:$lettertype;
}
```
Meer functies: https://sass-lang.com/documentation/functions

### Nesten (nesting)
```sass
.klasse {
  color: red;
  
  div {
    /* Dit past toe op divs BINNENIN een element met .klasse */
  }
  
  /* & selecteert de parent! */
  &.yeet {
    /* Dit past toe op elementen met classes klasse EN yeet */
    background-color: blue;
  }
}

```

### Partials & importeren
\_variables.scss
```scss
$lettertype:verdana, sans-serif;
div {
  background-color: red;
}
```
style.scss
```scss
@import "variables";
body {
  font-family: $lettertype;
}
```

### Mixins & includen
```sass
@mixin kleurencombinatie($achter,$voor) {
  background-color: $achter;
  color: $voor;
}
a {
  &:link {
    @include kleurencombinatie(#000,#fff);
  }
  &:visited {
    @include kleurencombinatie(darkblue,rgb(0,0,100));
  }
}
```

___

## Les 13, CSS3

### Prefixes
```css
h2:last-child {
  -webkit-text-emphasis: "*" #f04c25;
  text-emphasis: "*" #f04c25;
}
```

### Media queries
```css
#achtergrond {
  background-image: url(foto_1x.jpg);
}

/* 1dppx 1:1, 2dppx 2:2, 3dppx 3:3
@media (min-resolution: 2dppx) {
  #achtergrond {
    background-image: url(foto_2x.jpg);
  }
}
```

### Selectors
```css
/* ^: Begint met */
a[href^="mailto"] {}
a[href^="ftp"] {}
a[href^="https"] {}

/* $: Eindigt met */
a[href$=".pdf"] {}
a[href$=".doc"] {}
a[href$=".ppt"] {}

/* *: Bevat */
a[href*="image"] {}

/* Combinatie: pdf via http met naam in titel */
a[href^="http://"][href*="naam"][href$=".pdf"]{}

.selectClass
#selectId
* (Alle elementen)
div (alle divs)
div, p (alle divs en ps)
div > p (alle ps die directe children zijn van div)
div + p (alle ps die de volgende sibling van een div zijn (er recht achter komen))
div ~ p (alle ps die de vorige sibling van een div zijn (er recht voor komen))

[attribute] (Element met attribute)
[attribute="yeet"] (Element met attribute waarvan waarde gelijk is aan yeet)
[attribute~="yeet"] (Element met attribute waarvan de waarde het WOORD yeet bevat)
[attribute^="yeet"] (Element met attribute waarvan de waarde begint met yeet)
[attribute$="yeet"] (Element met attribute waarvan de waarde eindigt met yeet)
[attribute*="value"] (Element met attribute waarvan de waarde yeet bevat (waar dan ook))
```

### Psuedo-klassen & psuedo-elementen

<details><summary>Datamine</summary>
  AUTEURSNOTE: We kunnen allemaal Engels, en ik heb tot nu tot en met de css selectors ALLES handmatig geschreven. Ben het beu. ALS je een datamine spoiler ziet staan onder een titel, dan is dat gedeelte gewoon gedatamined van de cursus. In de datamine spoiler staat ook de code die ik heb geschreven om de cursus te dataminen. High effort diefstal?
  
  ```js
  function DatamineCursus(selector){
    var database = document.querySelectorAll(".lijst li")
    markdown = "```css\n"
    for (var i=0; i < database.length; i++) {
      var data = database[i].textContent
      splitIndex = data.indexOf(" ")
      var arg1 = data.substring(splitIndex, 0).trim().replace(/\s\s+/g, " ")
      var arg2 = data.substring(splitIndex).trim().replace(/\s\s+/g, " ")
      markdown += arg1 + "\t(" + arg2 + ")\n\n"
    }
    markdown += "```"
    console.log(markdown)
  }
  ```
                                    
</details>

```css
/* Psuedo-klassen */
a:link	(Selects all unvisited links)

a:visited	(Selects all visited links)

a:focus	(Selects the focused link)

a:hover	(Selects links on mouse hover)

a:active	(Selects the active link element)

input:checked	(Selects every checked <input> element)

input:disabled	(Selects every disabled <input> element)

p:empty	(Selects every <p> element with no children)

input:enabled	(Selects every enabled <input> element)

p:first-child	(Selects every <p> element that is the first child of its parent)

p:first-of-type	(Selects every <p> element that is the first <p> element of its parent)

input:focus	(Selects the <input> element which has focus)

input:in-range	(Selects <input> elements with a value within a specified range)

input:invalid	(Selects all <input> elements with an invalid value)

p:lang(language)	(Selects all <p> elements with a lang attribute equal to ‘language’)

p:last-child	(Selects every <p> element which is the last child of its parent)

p:last-of-type	(Selects every <p> element which is the last <p> element of its parent)

:not(p)	(Selects every element that is not a <p>)

p:nth-child(2)	(Selects every <p> element that is the second child of its parent)

p:nth-child(odd)	(Selects every <p> element that is an odd child of its parent)

p:nth-child(even)	(Selects every <p> element that is an even child of its parent)

p:nth-last-child(2)	(Selects every <p> element that is the second child of its parent, counting from the last child)

p:nth-last-of-type(2)	(Selects every <p> element that is the second <p> element of its parent, counting from the last child)

p:nth-of-type(2)	(Selects every <p> element that is the second <p> element of its parent)

p:only-of-type	(Selects every <p> element that is the only <p> element of its parent)

p:only-child	(Selects every <p> element that is the only child of its parent)

input:optional	(Selects <input> elements with no ‘required’ attribute)

input:out-of-range	(Selects <input> elements with a value outside a specified range)

input:read-only	(Selects <input> elements with the ‘readonly’ attribute specified)

input:read-write	(Selects <input> elements with the ‘readonly’ attribute not specified)

input:required	(Selects <input> elements with the ‘required’ attribute specified)

:root	(Selects the documents root element)

#id:target	(Selects the current active #id element)

input:valid	(Selects all <input> elements with a valid value)

/* Psuedo-elementen */

p::after	(Insert content after <p> element)

p::before	(Insert content before <p> element)

p::first-letter	(Selects the first letter of every <p> element)

p::first-line	(Selects the first line of every <p> element)

::selection	(Selects the portion of an element that is selected by a user)

```


### Text effects

```sass
span {
  font-size: 5em;
  font-family: $lettertypealternatief;
  text-shadow:
    0 -2px 1px $oranje,
    0 -4px 3px lighten(invert($oranje),20%),
    0 -6px 6px lighten($donker,30%),
    0 -9px 12px $donker;
}
```
Je kan experimenteren met text effecten op:
http://css3generator.com/
https://css3gen.com/wp-content/cache/all/text-shadow/index.html

### Multiple columns (kolommen)
```sass
#col1 {
  columns: 100px 3;
}

#col2 {
  column-count: 4;
  column-width: 100px;
  column-gap: $afstand*5;
  column-rule: $afstand/2 dotted $oranje;
}
```

### Background-images
De space en round properties kunnen gebruikt worden om bij herhaling niet af te snijden, ik denk in background-repeat
Meerdere background images combineren (meerdere achtergronden combineren):
```sass
  background-image: url(man.png), url(man.png), url(landschap.png);
  background-repeat: no-repeat;
  background-position: 20% 70%, 40% 60%, 0% 0%;
```

### Border & box

border-radius: 50%; voor een mooie cirkel uit te komen, voor fun voor de hele familie

Border-image: https://border-image.com/
Shapes: https://css-tricks.com/the-shapes-of-css/
Borders: https://code.tutsplus.com/tutorials/css-refreshers-borders--net-24655

### Color & opacity

currentColor hergebruikt de vorige kleur
```css
h2 {
  padding: 2rem;
  color: rebeccapurple;
  background-color: inherit;
  border: 5px solid currentColor;
  box-shadow: 0 0 5px currentColor;
}
```

Color picker: http://www.workwithcolor.com/hsl-color-picker-01.htm


### Gradients

Gradient generator: https://www.cssmatic.com/gradient-generator#'\-moz\-linear\-gradient\%28left\%2C\%20rgba\%28248\%2C80\%2C50\%2C1\%29\%200\%25\%2C\%20rgba\%28241\%2C111\%2C92\%2C1\%29\%2050\%25\%2C\%20rgba\%28246\%2C41\%2C12\%2C1\%29\%2051\%25\%2C\%20rgba\%28240\%2C47\%2C23\%2C1\%29\%2071\%25\%2C\%20rgba\%28231\%2C56\%2C39\%2C1\%29\%20100\%25\%29\%3B'

### 2D transforms

```css
div {
  transform: translate(20px,-20px) rotate(-290deg) scale(1.3,0.6) skew(45deg);
  transform-origin: 0% 20%;  /* Rotate niet vanaf 50% 50%, maar vanaf 20% onder de linkerbovenhoek */
}
```
Generator: https://www.css3maker.com/css3-transform.html

### 3D transforms

```css
div {
  transform: perspective(200px) rotateY(-50deg);
}
```

### transitions & animations
Transitions laten properties vloeiend veranderen, ipv dat ze in een milliseconde vooruitschieten
```sass
div {
  height: 50px;
  width: 50px;
  transition: height 500ms, width: 1s ease-in 500ms;
  
  /* Transition kan je ook languit schrijven: */
  transition: height;
  transition-duration: 500ms;
  transition-timing-function: ease-in;
  transition-delay: 500ms;
  
  &:hover {
    height: 200px;
    width: 200px;
  }
}
```

Animations laten je toe om complexere transitions te maken:
```css
@keyframes verkleuren_en_verplaatsen {
  /* 0%{} mag als from{} geschreven worden */
  0% {
    border-radius: 50%;
    background-color: red;
  }
  
  20% {
    background-color: yellow;
  }
 
  /* 100%{} mag als to{} geschreven worden */
  100% {
    background-color: blue;
    border-radius: 0%;
    transform: translateX(360px);
  }
  
  div {
    animation_name: verkleuren_en_verplaatsen;
    animation-duration: 10s;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
    animation-direction: alternate;
    animation-play-state: running;
    animation-delay: 2s;
  }
}
```


