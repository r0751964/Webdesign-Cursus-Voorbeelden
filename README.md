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
