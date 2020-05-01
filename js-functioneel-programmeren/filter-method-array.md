# filter method \(array\)

De filter-methode retourneert een array gevuld met array-elementen die aan een test voldoen. De test wordt in de vorm van een functie als parameter meegegeven. De filter-methode wordt niet uitgevoerd op de array-elementen zonder waarden. De filter-methode zal de oorspronkelijke array niet muteren.

## syntax

```javascript
array.filter(function(currentValue,index,arr), thisValue)
```

## parameters en argumenten

`function(currentValue, index, arr)`is een functie die voor elk element in de array uitgevoerd zal worden \(**verplichte parameter**\)

* `currentValue` __is de waarde van het lopende element \(**verplicht argument**\)
* `index` is de array-index van het lopende element \(**optioneel argument**\)
* `arr` is de array waarvan het lopende element deel van uitmaakt \(**optioneel argument**\)

`thisValue` is een waarde die aan de functie meegegeven kan worden en die als haar "this" waarde kan optreden \(**optionele parameter**\)

## toepassing

**Wat als slechts een gedeelte van de array getransformeerd moet worden?**

Veronderstel dat binnen de bron-array een aantal waarden getransformeerd moet worden en andere waarden die genegeerd moeten worden. Dat kan niet met de `map` methode alleen, want hiervoor zijn het aantal invoerwaarden altijd gelijk aan het aantal uitvoerwaarden.  
Stel dat oneven getallen moeten verdubbeld worden en de even getallen hierbij genegeerd dienen te worden. Dit kan met de onderstaande constructie.

```javascript
let numberList = [1, 2, 3, 4, 5, 6];
let newNumberList = [];

for(let i = 0; i < numberList.length; i++) {
    if(numberList[i] % 2 !== 0) {
        newNumberList[i] = numberList[i] * 2;
    }
}
console.log("The doubled numbers are", newNumberList); // [2, 6, 12]
```

Dit kan ook met de `map` en de `filter` methode.

```javascript
let numberList = [1, 2, 3, 4, 5, 6];
let newNumberList = numberList.filter(function(number) {
    return (number % 2 !== 0);
}).map(function(number) {
    return number * 2;
});
console.log("The doubled numbers are", newNumberList); // [2, 6, 12]
```

De `filter` callback respecteert - net zoals bij de `map` methode -  de regels dat er niet gemuteerd wordt en veroorzaakt geen neveneffecten, enkel de bewerkingen zijn verschillend.  
De geretourneerde waarde van de `filter` callback moet een `boolean` zijn. Die geeft aan of de oorspronkelijke waarde in het resultaat moet worden opgenomen \(`true`\) of eruit moet gelaten worden  \(`false`\). De waarde zelf moet dus niet geretourneerd worden, maar een `boolean`. De waarde kan vanuit de callback niet gewijzigd worden. De return-waarde bepaalt of de waarde zal worden opgenomen in het resultaat of niet.



#### BRONNEN

Una Kravets, [An Illustrated \(and Musical\) Guide to Map, Reduce, and Filter Array Methods](https://css-tricks.com/an-illustrated-and-musical-guide-to-map-reduce-and-filter-array-methods/), Mar 26, 2019

