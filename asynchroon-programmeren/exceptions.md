# exceptions

## error handling 'old school'

Om fouten binnen de code te behandelen werden tot nu toe twee manier gebruikt.   
Ten eerste kan er binnen het schrijven van code gewerkt worden met het **opsplitsen van code** in 'gewone code' en de code die specifiek geschreven wordt om fouten te behandelen.   
Een tweede manier is door het **opvangen van fouten** zodat de applicatie correct kan blijven doorlopen, er ondertussen mogelijke errors gelogd kunnen worden waarvan de gebruiker geen of enkel de nuttige foutmeldingen vermeld krijgt.

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        console.log("Error: only numbers")
        return false;
    }
    return a + b;
}

let c = add("not a number", 3);

if(c !== false)
{
    console.log(3 * c);
}
```

error code verspreid: if\(isNaN\(a\)\|\| isNaN\(b\)\) \(in functie\) if\(c !== false\) \(buiten functie\) afspraken nodig zodat elke functie bv. false teruggeeft bij error wat indien meerdere functies?

bv. 2 functies:

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        console.log("Error add: only numbers")
        return false;
    }
    return a + b;
}

let mult = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        console.log("Error mult: only numbers")
        return false;
    }
    return a * b;
}
```

hoe behandelen al deze fouten?

```javascript
let c = add("not a number", 3);
// add geeft error
let d = mult("again, not a number", 4);
// mult geeft error
let e = add(d,c);
```

een "check" na elke functie call

```javascript
let c = add("not a number", 3);
if(c === false){
    return;
}
// add geeft error
let d = mult("again, not a number", 4);
if(d === false){
    return;
}
// mult geeft error
let e = add(d,c);
if(e === false){
    return;
}
```

what als code niet gewoon mag stoppen, bv. er is nog code na de errors die altijd moet uitgevoerd worden

```javascript
let c = add("not a number", 3);
if(c === false){
    return;
}
// add geeft error
let d = mult("again, not a number", 4);
if(d === false){
    return;
}
let e = add(d,c);
if(e === false){
    return;
}
// more code that must be run, but will not be reached because of error/return
console.log("This code must be reached no matter what");
```

```javascript
let c = add("not a number", 3);
if(c !== false){
    let d = mult("again, not a number", 4);
    if(d !== false){
        let e = add(d,c);
        if(e !== false){
            console.log(e);
        }
    }
}

// more code that must be run
console.log("This code must be reached no matter what");
```

"messy": error handling en "normale" code gemengd

### error handling through exceptions

merk op: logica **wat gedaan wordt met error message** niet in functie bepaald

```javascript
let add = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
       throw "add: only use numbers";
    }
    return a + b;
}

let mult = (a,b) =>{
    if(isNaN(a)|| isNaN(b))
    {
        throw "add: only use numbers";
    }
    return a * b;
}
```

```javascript
try{
    let c = add("not a number", 3);
    let d = mult("again, not a number", 4);
    let e = add(d,c);
    console.log(e);
}
catch(exc){
    console.log(exc);
}
finally{
    console.log("This code must be reached no matter what");
}
```

## exceptions

### voordelen

* logica en error handling mooi apart
* universele aanpak "gooien" error \(geen extra afspraken nodig\)
* error handling op 1 plek = gemakkelijk aanpassen van manier van behandelen
  * bv. log naar de console
  * bv. bewaar boodschap in database
  * bv. verberg boodschap voor gebruiker en zorg dat applicatie blijft draaien

### basics

* `throw`
* `try` / `catch`
* `finally`
* call stack



## exception: throw

* "gooit" een foutmelding

```text
let isFout = true;
if(isFout){
  throw "Er is een fout"
}
```

* gooi string, nummer, object...

```text
let isFout = true;
if(isFout){
throw {waar:"Optellen", wat:"a is geen getal"}
}
```

## exception: finally

* mooi afronden van je code
* wordt altijd uitgevoerd, met of zonder expections

```text
try{
add("geen getal", 1);
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
    throw "Error in functie 1";
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
    throw "Error in functie 1";
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

