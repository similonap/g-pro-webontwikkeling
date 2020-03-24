# scope in JS

## definitie

De **scope** is de toegankelijkheid of bereik van variabelen, functies of objecten in een bepaald deel van de code tijdens runtime.   
Variabelen in JS zijn gedefinieerd in een functie **scope**. Concreet betekent dit dat als een variabele gedefinieerd is binnen een functie, deze enkel zichtbaar is binnen de functie en dus onzichtbaar buiten de functie. De **scope** van een variabele is dus het stuk code waarin de variabele bestaat en dus gebruikt kan worden. Scopes zijn ontstaan ​​toen het principe van het minste privilege werd toegepast bij het ontwerpen van programmeertalen.

## doel

Ze bieden een zekere mate van **beveiliging** voor uw code, d.w.z. ze worden alleen gebruikt wanneer ze echt nodig zijn. Door onderdelen van de code te scopen, verhoogt dit de **efficiëntie** en zijn **bugs makkelijker op te sporen** en te verminderen.   
Het lost ook het **probleem van naamgeving** op wanneer er variabelen met dezelfde naam verschijnen in verschillende 'scopes'. Hierdoor wordt de botsing door gelijke naamgeving verkleind.

## scope types

### globale & local scope

Als een variabele gedefinieerd wordt buiten elke functie om of buiten accolades `{}`, dan is dit een **globale scope**. De term **globale variabelen** beschrijft dus variabelen die gedefinieerd zijn buiten elke functie om.

```javascript
const global_var = 1;
// globale variabele, want gedeclareerd buiten een functie om
```

Als een variable echter gedefinieerd is binnen een `if-` of een `for-`blok van de code, is die wel zichtbaar buiten het blok. De code binnen een functie heeft toegang tot alle globale variabelen evenals tot zijn eigen **lokale variabelen**.

In het volgende voorbeeld:  
heeft de `f()` functie toegang tot de globale variabele `global_var`;  
buiten de `f()` functie bestaat de lokale variabele niet.

```javascript
const global_var = 1;
const f() =>
   let local_var = 3;
   global_var++;
   return global_var;
}
console.log(f()); 
//2
console.log(f());
//3
console.log(global_var);
// de variable global_var behoort tot het globale window object
// 3
```

Als er bij het declareren van een variabele geen gebruik gemaakt wordt van `let` of `const`, wordt aan deze variabele automatisch een globaal bereik toegewezen.

een ander voorbeeld:

```javascript
// global
let mouse = "Mouse";

const test1() => {
  // local
  let name = "Cat";
  console.log(name);
}

const test2() => {
  // Local
  let name = "Dog";
  console.log(name);
}

test1();
test2();

console.log(name);
```

#### tips

1. Beperk het aantal globale variabelen om botsingen tussen de namen van variabelen te vermijden. Indien voor globale variabelen dezelfde naam zou gebruikt worden -want je bent in team aan het coderen bijvoorbeeld-, kan dit leiden tot onverwachte resultaten en moeilijk op te sporen bugs.
2. Declareer dus altijd variabelen met de instructie `let`.
3. Gebruik een "één let" patroon. Declareer altijd alle variabelen die nodig zijn in je functie aan het begin van de functie. Dan moet je slechts naar één plaats kijken om te zien welke variabelen er gebruikt worden.

### lexical scope

Wanneer een functie binnen een andere functie genest is, zal de binnenste functie toegang hebben tot de scope in de buitenste functie, of ook wel de **lexical scope of static scope** genoemd, omdat het alleen mag aangeroepen worden \(waarnaar wordt verwezen\) vanuit het codeblok waarin het is gedefinieerd.

```javascript
const SocialMedia() => {
    let channel = 'Facebook';
    const platform() => {
        // channel is van hieruit bereikbaar
        const comments() => {
            //het binnenste functie van de scope keten
            // channel is ook van hieruit bereikbaar
            let comments = 'Learning scopes';
        }
    }
}
```

JavaScript begint bij het binnenste bereik en gaat zo naar buiten totdat het de variabele \| object \| functie vindt waarnaar het op zoek was. 

Het meest belangrijke om te onthouden is dat de lexicale scope **niet achterwaarts werkt**. d.w.z. er is geen toegang tot de variabele _comments_ binnen de functie _SocialMedia_  en de functie _platform_ in het bovenstaande voorbeeld.

### block scope

Block statements zoals _if_ en _switch_ conditions, of _for_ en _while_ loops en {} creëren -in tegenstelling tot functions- geen nieuwe scope. Variabelen die binnen een block scope gedefinieerd zijn, blijven binnen de scope waarin ze al zaten.

```javascript
// global
let name = "Mouse";
{
  // local
  let name = "Cat";
  console.log(name); // Cat
}
console.log(name); // Mouse
```







