# labo 3: herhaling

_Dit is 1 grote oefening. Werk elke opdracht af in hetzelfde project. Je eindigt dit labo met 1 web applicatie._

## 1. Maak het project aan

Open Visual Studio en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal.

Maak de file `app.js` aan en zet de volgende code hierin:

```javascript
const express = require('express');
const ejs = require('ejs');

const app = express();
app.set('port', process.env.PORT || 3000);
app.set('view engine', 'ejs');
app.use(express.static(__dirname + '/public'));

app.get('/', (req,res) => {

});

app.listen(app.get('port'), () => {
  console.log(`Express started on http://localhost:${
    app.get('port')}; press Ctrl-C to terminate.`);
});
```

Initialiseer het project met

```text
npm init
```

en

```text
npm install express --save
npm install ejs --save
```

Maak 2 folders aan in het project: `views` en `public`

## 2. De index-bestand

_tip: Kijk naar de voorbeeldbestanden / slides van de laatste theorieles indien je niet verder kunt._

1. Maak een index.ejs-bestand aan met een simpele HTML structuur die Hello World bevat, vetgedrukt.
2. Zorg ervoor dat de `localhost:3000/` deze pagina laadt.
3. Pas de `index.ejs` file en `app.js` file aan zodat:

   1. de `app.js` een variable `family` bevat met de naam van een familielid erin.
   2. de `index.ejs` file deze variable gebruikt om Hello **naam van je familielid** te zeggen

## 3. JSON inladen

1. Maak een JSON **bestand** `persoon.json` ****aan die het veld `name` bevat met jouw naam.
2. Laad deze JSON in je app.js bestand in en zet die in een variable `persoon`
3. Zorg ervoor dat de `index.ejs` de waarde van de variable `persoon` ipv `family` toont
4. Voeg een foto van jezelf toe in de folder `public`
5. Voeg het veld image aan het `persoon.json` bestand toe met als waarde de volledige naam van je foto bestand \(bv. `sven.png`\)
6. Voeg een `img` tag toe aan `index.ejs` met als `src` de naam van jouw foto bestand. **LET OP: dit moet uit jouw `persoon.json` file geladen worden**

## 4. Pikachu page

1. Installeer het pokedex npm package.
2. Maak een `pokemon.ejs` bestand 
3. Maak een route `/pikachu` aan die `pokemon.ejs` laadt en de naam en animatie \(animated sprite\) van Pikachu doorgeeft aan `pokemon.ejs`
4. Maak de HTML in `pokemon.ejs` aan zodat de naam en de image getoond worden als ik naar `localhost:3000/pikachu` ga.
5. Maak een tweede route aan `/raichu` die hetzelfde doet voor Raichu, MAAR maak geen nieuwe `pokemon.ejs` aan \(gebruik dezelfde `ejs` file\).

## 5. Arrays

1. Maak een lege array `arrayOfPokemon` aan.
2. Doorloop in een for loop Pokemon 10 tem 14
3. In deze for loop, voeg elk van deze 5 Pokemon toe aan `arrayOfPokemon` dmv de methode `arrayOfPokemon.push(...)`
4. Maak een route `/pokemons` aan. Maak een nieuwe `pokemons.ejs` aan. Wanneer je naar `localhost:3000/pokemons` ga zie ik de naam en animatie van deze 5 Pokemon. Tip: je mag de HTML voor elke Pokemon 5 maal herhalen in deze EJS file

## 6. For loop in EJS \(bonus oefening\)

Je kan in EJS ook Javascript toevoegen die uitgevoerd wordt op de server en zo nieuwe HTML naar de client stuurt. Bv. stel ik stuur een variable `toonHelloWorld` naar mijn EJS file die een boolean _true_ of _false_ bevat. Hiermee kan ik in de server code bepalen of Hello World getoond wordt in de client of niet:

app.js route code:

```javascript
app.get('/', (req,res) => {
    res.render('index',{'toonHelloWorld': true});
});
```

index.ejs code:

```javascript
<% if(toonHelloWorld) { %>
    <h1>Hello World</h1>
<% } %>
```

In dit geval wordt &lt;h1&gt;Hello World&lt;/h1&gt; getoond op de client. Wanneer we de waarde false megeven, wordt dit stukje HTML-code niet getoond.

Pas nu pokemons.ejs aan zodat je niet zelf 5 maal de code herhaalt voor elke Pokemon, maar een **for loop** maakt die elke Pokemon's naam en animatie toont.

## 7. 10 nieuwe routes dmv de for loop \(bonus oefening\)

1. Maak een for loop aan die door Pokemon 100 tem 109 loopt.
2. Print de namen van de Pokemon naar de console \(console.log\)
3. In deze loop, maak een nieuwe route aan voor elk van deze Pokemon, waarbij de route de naam van de Pokemon is.  Tip: je hebt geen nieuwe EJS file nodig. Gebruik `pokemon.ejs`

