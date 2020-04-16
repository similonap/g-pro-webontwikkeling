# blocking code

Asynchrone technieken zijn erg handig vooral dan bij webprogrammeren. Wanneer een webapp in een browser wordt uitgevoerd en een intensief stuk code uitvoert zonder de controle terug te geven aan de browser, kan het lijken alsof de browser bevroren is. Dit wordt blokkeren of 'blocking code' genoemd, waarbij de browser niet langer gebruikersinvoer kan afhandelen en andere taken uitvoeren, totdat de webapp de controle over de processor terugkrijgt.

Hieronder staan een paar voorbeelden van wat net bedoeld wordt  met 'blocking code'. 

```javascript
let i = 1;
console.log(i); // deze lijn wacht op de vorige lijn
```

 De code hierboven wordt lijn voor lijn uitgevoerd. En de code hieronder is afhankelijk van wat voordien gebeurt, zoals een programma dat wacht tot de gebruiker iets heeft ingevuld.

```javascript
let readlineSync = require('readline-sync');
let input = readlineSync.question('Vul iets in: ');
console.log(input);
```

In onderstaand voorbeeld wordt code uitgevoerd die tijdrovende berekeningen moet uitvoeren, want `mult` moet wachten tot `sum` gedaan is. Maar `mult` hangt eigenlijk niet af van `sum`, dus waarop wordt er eigenlijk gewacht?

```javascript
let sum = 0;
for(let i=0;i<99999999999;i++){
sum+=i;
}
console.log('sum done');
let mult = 1;
for(let i=0;i<99999999999;i++){
mult*=i;
}
console.log('mult done');
```



