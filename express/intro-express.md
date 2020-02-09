---
description: web application framework
---

# 1. intro Express

## Wat is Express?

Een applicatie in NodeJS kan verschillende vormen aannemen, maar veelal wordt NodeJS gebruikt voor het bouwen van backend applicaties. Concreet zal er in de Node applicatie een server opstarten met behulp van de http-module, waardoor de applicatie benaderd kan worden over het internet.   
Omdat tijd kostbaar is en we niet allemaal het warm water opnieuw willen uitvinden, is het handig om optimaal te kunnen werken en dit kan binnen deze context door gebruik te maken van een server framework, namelijk Express. 

[Express](https://expressjs.com/) maakt het mogelijk om het bouwen van servers in Node.js te vergemakkelijken. Het **server framework** heeft naast een vaste structuur voor het starten en beheren van een server, ook methodes voor het beantwoorden van externe verzoeken aan de server. Zolang je als ontwikkelaar binnen de lijntjes kleurt, neem het framework een groot aantal taken over van de ontwikkelaar. Express is qua functionaliteiten uitbreidbaar met modules, zowel eigen modules als NPM en kan ingezet worden voor het **bouwen van web-apps** en **API's \(**\(Application Programming Interface\).   
API's kunnen instaan om taken uit te voeren, afhankelijk van de context van de applicatie, zoals data opvragen van de server, data wijzigen via de server, gebruikers laten in- of uitloggen, het uploaden of downloaden van bestanden naar een file-server,...

## Express installeren

### software downloaden

```bash
npm init
```

```bash
npm install --save express
```

meer info: [https://expressjs.com/en/starter/installing.html](https://expressjs.com/en/starter/installing.html)

## eerste script

### express.js

```javascript
const express = require('express');
const app = express();
app.set('port', process.env.PORT || 3000);

// pagina 404 (= http-statuscode 'niet gevonden')
app.use(function(req, res){
res.type('text/plain');
res.status(404);
res.send('404 - Not Found');
});

// pagina 500 (= http-statuscode 'interne serverfout')
app.use(function(err, req, res, next){
console.error(err.stack);
res.type('text/plain');
res.status(500);
res.send('500 - Server Error');
});

app.listen(app.get('port'), function(){
console.log( 'Express started on http://localhost:' +
app.get('port') + '; press Ctrl-C to terminate.' );
});
```

### achtergrond-info: arrow-functie in JavaScript

`(req, res) =>` zal je vanaf nu meermaals zien verschijnen in oefeningen. Deze pijl laat ons toe om functies verkort uit te schrijven. Vanaf nu kiezen we bewust om te werken met de arrow-notatie.

#### functie-notatie \(oude manier\)

```javascript
//functie-notatie met naam
function hello(req, res) {
  return "Hello AP!";
}

//functie-notatie zonder naam
function (req, res) {
  return "Hello AP!";
}
```

#### arrow-notatie \(nieuwe manier\)

```javascript
//arrow-notatie met naam
hello = (req, res) => {
  return "Hello AP!";
} 

//arrow-notatie zonder naam
(req, res) => {
  return "Hello AP!";
} 
```

```javascript
//Wanneer een functie met één instructie een waarde retourneert, mogen de haakjes en het woord return verwijderd worden.
hello = () => "Hello AP!";
```

meer info: [https://www.w3schools.com/js/js\_arrow\_function.asp](https://www.w3schools.com/js/js_arrow_function.asp)





