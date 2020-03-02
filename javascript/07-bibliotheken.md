# 07. Bibliotheken

## Inleiding

Een JavaScript-bibliotheek is een verzameling van voorgedefinieerde scripts met een specifiek doel. Je kan zo een bibliotheek inladen om dan dit specifiek doel uit te voeren.

Het inladen van een bibliotheek gebeurt op dezelfde manier als het inladen van een extern script:

```javascript
<script src="js/leaflet.js"></script>
```

Bibliotheken bestaan vaak niet enkel uit een .js-bestand, maar worden vergezeld van CSS. Hiervoor zal je dan ook een .css-bestand moeten inladen.

### Content Delivery Network \(CDN\)

Om externe bibliotheken te beheren en vlot in te kunnen laden, is het vaak aangewezen om te werken met een _content delivery network_ \(CDN\). Dit is een speciale server die zich specialiseert in het aanleveren van scripts \(e.a.\).

```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.5.1/leaflet.js"></script>
```

## Bibliotheek vs. framework

Een uitbreiding op bibliotheken zijn frameworks. Waar bibliotheken je vrij laten in het schrijven van je eigen HTML, gaan frameworks een stap verder en bepalen zij hoe jouw HTML er gaat uitzien. Dit omdat de volgorde van aanroepen anders is.

Bij een bibliotheek ga jij een extern script vragen om een specifieke taak van je over te nemen. Jij neemt dus het voortouw en roept de bibliotheek op de juiste moment aan.

Bij een framework geef je die controle af. Het framework gaat jouw code oproepen en gebruiken in plaats van omgekeerd.

## jQuery

De meest verspreide JavaScript-bibliotheek is jQuery. Ze werd in 2019 nog in 85% van de websites gebruikt \([https://almanac.httparchive.org/en/2019/javascript](https://almanac.httparchive.org/en/2019/javascript#open-source-libraries-and-frameworks)\).

jQuery maakt veel taken die JavaScript al jaren uitvoert veel eenvoudiger. Maar met de komst van JavaScript 6 \(ECMAscript 6\) werd de noodzaak voor het gebruik weggenomen. Het feit dat er toch nog 85% van de websites deze bibliotheek inlaadt, heeft vooral te maken met oudere projecten en bepaalde CMS-systemen die jQuery standaard ophalen, zelfs als die niet gebruikt wordt.

## Package managers

Met de opkomst van enkele miljoenen aan bibliotheken werd de noodzaak aan goed beheer hiervan ook groter. Daarom bestaan er enkele belangrijke package managers. Deze gaan in jouw plaats een overzicht bijhouden van de belangrijkste bibliotheken die je aan jouw project hebt toegevoegd.

Je kan zo'n package manager ook eenvoudig gebruiken om bij te houden welke versie van een bepaalde bibliotheek je aan het gebruiken bent of om een bibliotheek te updaten naar een nieuwere versie.

We gaan in het vervolgvak \(webontwikkeling\) gebruik maken van zo'n package manager.

## Enkele bibliotheken

Om te leren werken met bibliotheken hebben wij een selectie gemaakt van enkele veel gebruikte bibliotheken die een specifieke nuttig taak uitvoeren. 

### Leaflet \([link](https://leafletjs.com)\)

Bijna elke bedrijfswebsite bevat wel een map met de locatie van het bedrijf. En hoeveel webapps bestaan er niet die op basis van jouw locatie een hoop zaken weergeven op een map. De meest gekende leverancier van mappen is Google Maps. Google is echter een bedrijf met een zeer specifiek en gekend winstmodel.

Een grote tegenhanger van Google Maps is OpenStreetMap. Deze open-source tegenhanger wil toegang tot locatie-gebaseerde informatie voor iedereen mogelijk maken. OpenStreetMap is echter enkel de laag van afbeeldingen die op de wereldkaart worden getoond. Om hierdoor te navigeren hebben we een interactieve bibliotheek nodig: Leaflet.

#### 2 lagen

Elke map \(in Leaflet\) bestaat uit 2 lagen: de coördinatenlaag en de kaartlaag. Elke laag heeft zijn eigen functie en voorziet de gebruiker van de nodige informatie. De coördinatenlaag maakt gebruik van de lengte- en breedtegraden om te kunnen navigeren op onze planeet. De kaartlaag geeft een visuele weergave.

#### HTML

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Leaflet Demo</title>

    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css">
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div id="mapje"></div>

    <script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js"></script>
    <script src="script.js"></script>
  </body>
</html>
```

#### CSS

```css
* {
  margin: 0;
  padding: 0;
}

#mapje {
  width: 100vw;
  height: 100vh;
}
```

#### JS - map initialiseren \(coördinatenlaag

```javascript
/*
 * map initialiseren
 */
let myMap = L.map('mapje', { // gebruik id "mapje" in HTML
  center: [50.22, 6.40], // middelpunt van map
  zoom: 14 // schaal van de map
});
```

#### JS - map initialiseren \(kaartlaag\)

```javascript
/*
 * map activeren
 * kaartlaag toevoegen
 */
L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={accessToken}', {
	id: 'mapbox.streets',
  accessToken: 'pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw',
  attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>'
}).addTo(myMap);
```

#### JS - "duimspijker" toevoegen

```javascript
/*
 * "Duimspijker" toevoegen
 * locatie precies bepalen
 */
let markerKeizerstraat = L.marker([51.221796, 4.406483]);
markerKeizerstraat.bindPopup('Hallo studenten');
markerKeizerstraat.addTo(myMap);
```

#### JS - wereld tonen

```javascript
/*
 * Wereld tonen
 */
myMap.fitWorld();
```

#### JS - geolocatie gebruiker inladen

```javascript
/*
 * Huidige locatie tonen
 */
myMap.locate({
  setView: true,
  maxZoom: 16
});

function onLocationFound(e) {
    let radius = e.accuracy;

    L.marker(e.latlng).addTo(myMap)
        .bindPopup("Je bevindt zich binnen " + radius + " meters van dit punt").openPopup();

    L.circle(e.latlng, radius).addTo(myMap);
}

myMap.on('locationfound', onLocationFound);
```

### Cleave.js \([link](https://nosir.github.io/cleave.js/)\)

Deze bibliotheek is gespecialiseerd in het opmaken van invoer in HTML-formulieren. Dit maakt het gebruik van dergelijk formulier gebruiksvriendelijker. Uiteraard heb je zelf nog een beetje werk met de configuratie van de bibliotheek.

#### HTML

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Cleave Demo</title>

    <link rel="stylesheet" href="style.css">

    <script src="https://cdnjs.cloudflare.com/ajax/libs/cleave.js/1.5.3/cleave.min.js" integrity="sha256-yx/X2dD86fWz9OyQ/ZnQH8BQaS5Ta4OuNJICU17rySE=" crossorigin="anonymous" defer></script>
    <script src="script.js" defer></script>
  </head>
  <body>
      <form class="container" action="#" method="post">
        <input class="input-credit-card" placeholder="Type een kredietkaartnummer" />
        <input class="input-date" placeholder="Geef een datum: DD/MM/JJJJ" />
        <input class="input-numeral" placeholder="Geef een getal in" />
        <input class="input-custom" placeholder="Custom delimiter & blocks" />
      </form>
  </body>
</html>

```

#### CSS

```css
* {
    box-sizing: border-box;
}
.container {
    width: 200px;
}
button {
    margin-bottom: 15px;
    width: 100%;
    height: 24px;
    outline: none;
    border: 1px solid #e6e6e6;
    border-radius: 5px;
    background-color: #fff;
    font-size: 13px;
}
.input-credit-card {
    margin-bottom: 5px;
}
input {
    display: block;
    outline: none;
    border: 1px solid #e6e6e6;
    border-radius: 5px;
    background-color: #fff;
    line-height: 30px;
    vertical-align: middle;
    height: 33px;
    width: 100%;
    font-size: 14px;
    padding: 0 8px;
    margin-bottom: 15px;
}

.input-numeral {
    text-align: right;
}

body {
    font-family: sans-serif;
}

a,
a:hover {
    color: #999;
}

a {
    font-size: 14px;
    margin-top: 20px;
}
```

#### JS - kredietkaart

```javascript
// credit card
let cleaveCreditCard = new Cleave('.input-credit-card', {
    creditCard: true
});
```

#### JS - datum

```javascript
// date
let cleaveDate = new Cleave('.input-date', {
    date: true,
    datePattern: ['d', 'm', 'Y']
});
```

#### JS - getallen

```javascript
// numeral
let cleaveNumeral = new Cleave('.input-numeral', {
    numeral: true,
    numeralThousandsGroupStyle: 'thousand'
});
```

#### JS - aangepaste invoer

```javascript
// custom
let cleaveCustom = new Cleave('.input-custom', {
    blocks: [1, 3, 3],
    delimiter: '-',
});
```

### Flickity \([link](https://flickity.metafizzy.co)\)

Ondanks het feit dat onderzoekers al meerdere malen aantoonden dat _carousels_ op website niet zinvol zijn voor de gebruiksvriendelijkheid, worden ze nog dagelijks aan websites toegevoegd.

Er bestaan dan ook tientallen van interessante bibliotheken die voor jou zo'n carousel kunnen bouwen. Flickity is een van de betere in deze reeks, aangezien deze ook volledig touch-vriendelijk is opgebouwd.

#### HTML

```markup
<!DOCTYPE html>
<html lang="be-NL" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Flickity demo</title>

    <link rel="stylesheet" href="https://unpkg.com/flickity@2/dist/flickity.min.css">
    <link rel="stylesheet" href="css/style.css">

    <script src="https://unpkg.com/flickity@2/dist/flickity.pkgd.min.js" defer></script>
    <script src="js/script.js" defer></script>
  </head>
  <body>
    <div class="carousel">
      <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/orange-tree.jpg" alt="orange tree" />
      <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/submerged.jpg" alt="submerged" />
      <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/look-out.jpg" alt="look-out" />
      <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/one-world-trade.jpg" alt="One World Trade" />
      <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/drizzle.jpg" alt="drizzle" />
    </div>
  </body>
</html>
```

#### CSS

```css
* { box-sizing: border-box; }
body { font-family: sans-serif; }

.carousel {
  background: #EEE;
}
.carousel img {
  display: block;
  height: 200px;
}
```

#### JS - initialiseren carousel

```javascript
// create a flickity instance from the library, using the element-class
let flkty = new Flickity('.carousel');
```

## Extra info voor labo

**defer**: Het script dat in de head van een HTML-bestand staat, wordt pas uitgevoerd nadat de hele pagina geladen is.

```javascript
<script src="javascript.js" defer></script>
```

try it yourself: [https://www.w3schools.com/tags/tryit.asp?filename=tryhtml\_script\_defer](https://www.w3schools.com/tags/tryit.asp?filename=tryhtml_script_defer)

