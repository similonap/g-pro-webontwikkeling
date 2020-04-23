# exceptions

## error handling vroeger...

Om **fouten binnen de code te behandelen** werden tot nu toe twee manier gebruikt.   
Ten eerste kan er binnen het schrijven van code gewerkt worden met het **opsplitsen van code** in 'gewone code' en de code die specifiek geschreven wordt om fouten te behandelen.   
Een tweede manier is door het **opvangen van fouten** zodat de applicatie correct kan blijven doorlopen, er ondertussen mogelijke errors gelogd kunnen worden waarvan de gebruiker geen of enkel de nuttige foutmeldingen vermeld krijgt.

### voorbeeld met één functie

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b)) // error code binnen functie
    {
        console.log('Error: only numbers')
        return false;
    }
    return a + b;
}

let c = add('not a number', 3);

if(c !== false) // error code buiten functie
{
    console.log(3 * c);
}
```

De **error code** in bovenstaand voorbeeld is verspreid en staat zowel **binnen**  `if(isNaN(a)|| isNaN(b))`als **buiten de functie** `if(c !== false)`. Bij deze manier van werken zijn er onderling afspraken nodig, zodat bijvoorbeeld elke functie bij een error `false` teruggeeft. maar wat dan gedaan indien er meerdere functies zijn?

### voorbeeld met twee functies

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        console.log('Error add: only numbers')
        return false;
    }
    return a + b;
}

let mult = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        console.log('Error mult: only numbers')
        return false;
    }
    return a * b;
}
```

Hoe moeten al deze fouten behandeld worden?

#### originele error-code \( in 3 lijnen\)

```javascript
let c = add('not a number', 3);
// add geeft error
let d = mult('again, not a number', 4);
// mult geeft error
let e = add(d,c);
```

#### error-code met if \(voor testen exceptions\)

Er komt een 'check' na elke functie call, maar elke keer als er iets fout loopt, stopt het programma. 

```javascript
let c = add('not a number', 3);
if(c === false){
    return;
}
// add geeft error
let d = mult('again, not a number', 4);
if(d === false){
    return;
}
// mult geeft error
let e = add(d,c);
if(e === false){ 
    return;
    // Een return buiten een functie -in main JS-bestand-laat programma stoppen.
    // In Express loopt het programma gewoon verder, tenzij return op einde code.
}
```

Wat als de code niet gewoon mag stoppen, aangezien er bijvoorbeeld nog altijd code na de errors moet uitgevoerd worden?

```javascript
let c = add('not a number', 3);
if(c === false){
    return;
}
// add geeft error
let d = mult('again, not a number', 4);
if(d === false){
    return;
}
let e = add(d,c);
if(e === false){
    return;
}
// meer code die nog uitgevoerd moet worden, gebeurt niet door error/return
console.log('This code must be reached no matter what');
```

#### error-code met if en voorwaarden, zodat code niet stopt

```javascript
let c = add('not a number', 3);
if(c !== false){
    let d = mult('again, not a number', 4);
    if(d !== false){
        let e = add(d,c);
        if(e !== false){
            console.log(e);
        }
    }
}

// meer code die uitgevoerd wordt
console.log('This code must be reached no matter what');
```

De code als geheel is niet meer overzichtelijk, aangezien error handling en 'normale' code gemengd worden.

## ... en nu met exceptions

Let in het volgende voorbeeld op de logica van **wat gedaan wordt met error message,** die niet in een functie bepaald wordt. De functie wordt uitgevoerd, maar bij een probleem is, wordt er een error-code gegooid door middel van `throw`.

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
       throw 'add: only use numbers';
    }
    return a + b;
}
let mult = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        throw 'add: only use numbers';
    }
    return a * b;
}

try{
    let c = add('not a number', 3);
    let d = mult('again, not a number', 4);
    let e = add(d,c);
    console.log(e);
}
catch(exc){
    console.log(exc);
}
finally{
    console.log('This code must be reached no matter what');
}
```

```javascript
$node test.js
add: only use numbers // uitkomst van regel 4
This code must be reached no matter what // uitkomst van regel 26
```

## exceptions

### voordelen

In bovenstaande voorbeeld staan logica en error handling mooi **apart neergeschreven**. De **universele aanpak** van het 'gooien' \(`throw`\) van een error, maakt dat er geen extra afspraken nodig zijn bij het schrijven van code, zoals voorheen wel het geval was. Aangezien de error handling nu slechts op **één plek** staat, kan de manier van behandelen van de errors makkelijk aangepast worden: 

* log naar de console
* bewaar boodschap in database
* verberg boodschap voor gebruiker en zorg dat applicatie blijft draaien
* ...

### basics

* `throw`
* `try` / `catch`
* `finally`
* call stack

## exception: throw

* "gooit" een foutmelding

```javascript
let isFout = true;
if(isFout){
  throw 'Er is een fout'
}
```

* gooi string, nummer, object...

```javascript
let isFout = true;
if(isFout){
throw {waar:'Optellen', wat:'a is geen getal'}
}
```

## exception: finally

* mooi afronden van je code
* wordt altijd uitgevoerd, met of zonder expections

```javascript
try{
add('geen getal', 1);
}
catch(exception)
{
//do something with exception
}
finally {
// this code always runs
}
```

## exception: call stack

functie 2 behandelt error

```javascript
let functie1 = () =>
{
    throw 'Error in functie 1';
}

let functie2 = () =>
{
    try{
        functie1();
    }
    catch(exception){
        console.log(exception);
    }
}

functie2();
```

wanneer niet direct behandeld, wordt die opnieuw gegooid

```javascript
let functie1 = () =>
{
    throw 'Error in functie 1';
}

let functie2 = () =>
{
   functie1();
}

try{
    functie2();
}
catch(exception){
    console.log(exception);
}

```

