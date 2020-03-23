# scope in JS

Variabelen in JS zijn gedefinieerd in een functie **scope**. Concreet betekent dit dat als een variabele gedefinieerd is binnen een functie, deze enkel zichtbaar is binnen de functie en dus onzichtbaar buiten de functie. De **scope** van een variabele is dus het stuk code waarin de variabele bestaat en dus gebruikt kan worden.

### globale scope

Als een variabele gedefinieerd wordt buiten elke functie om of buiten accolades `{}`, dan is dit een **globale scope**. De term **globale variabelen** beschrijft dus variabelen die gedefinieerd zijn buiten elke functie om.

```javascript
const global_var = 1;
// globale variabele, want gedeclareerd buiten een functie om
```

Als een variable echter gedefinieerd is binnen een `if-` of een `for-`blok van de code, is die wel zichtbaar buiten het blok. De term **globale variabelen** beschrijft variabelen die gedefinieerd zijn buiten elke functie. De code binnen een functie heeft toegang tot alle globale variabelen evenals tot zijn eigen **lokale variabelen**.

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
console.log(typeof(local_var));
//"undefined
console.log(global_var);
// de variable global_var behoort tot het globale window object
// 3
console.log('global object: ', window.global_var);
//"global object: " 3
```

Als er bij het declareren van een variabele geen gebruik gemaakt wordt van `let` of `const`, wordt aan deze variabele automatisch een globaal bereik toegewezen.

#### tips

1. Beperk het aantal globale variabelen om botsingen tussen de namen van variabelen te vermijden. Indien voor globale variabelen dezelfde naam zou gebruikt worden -want je bent in team aan het coderen bijvoorbeeld-, kan dit leiden tot onverwachte resultaten en moeilijk op te sporen bugs.
2. Declareer dus altijd variabelen met de instructie `let`.
3. Gebruik een "één let" patroon. Declareer altijd alle variabelen die nodig zijn in je functie aan het begin van de functie. Dan moet je slechts naar één plaats kijken om te zien welke variabelen er gebruikt worden.

