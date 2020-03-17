# JS - map method \(array\)

Mapping is een interessante functionele programmeertechniek voor het bewerken van alle elementen in een array en het retourneren van een array van dezelfde lengte met getransformeerde inhoud. De `map` methode kan je enigszins vergelijken met een `for each` lus, maar dan specifiek **voor het omzetten van waarden**. Eén invoerwaarde komt zo overeen met één getransformeerde output waarde.

## syntax

```javascript
array.map(function(currentValue,index,arr), thisValue)
```

## parameters en argumenten

`function(currentValue, index, arr)`is een functie die voor elk element in de array uitgevoerd zal worden \(**verplichte parameter**\)

* `currentValue` __is de waarde van het lopende element \(**verplicht argument**\)
* `index` is de array-index van het lopende element \(**optioneel argument**\)
* `arr` is de array waarvan het lopende element deel van uitmaakt \(**optioneel argument**\)

`thisValue` is een waarde die aan de functie meegegeven kan worden en die als haar "this" waarde kan optreden \(**optionele parameter**\)

## toepassing

Onderstaande code is een klassieke en procedurele, maar omslachtige manier om een vrij eenvoudige taak uit te voeren, namelijk het verdubbelen van alle getallen in een array.

```javascript
let numberList = [6, 7, 8, 9];
let newNumberList = [];
for(let i = 0; i < numberList.length; i++) {
    newNumberList[i] = numberList[i] * 2;
}
console.log("The list of doubled numbers: ", newNumberList); // [2, 4, 6, 8]
```

Dit kan beter en een pak efficiënter. Wat als we gewoon de getallen in de array op een manier zouden kunnen verdubbelen om deze elementen nadien in de array toe te passen?   
Er dus geen lus meer nodig en de getallen hoeven niet handmatig toegevoegd te worden aan een array. De  intentie wordt gedefinieerd en de `map` -methode doet verder zijn werk.

```javascript
let numberList = [3, 2, 6, 5];
let newNumberList = numberList.map(function(number){
    return number * 2;
});
console.log("The doubled numbers are", newNumberList); // [6, 4, 12, 10]
```

Dit kan ook makkelijk geketend worden.

```javascript
let numberList = [1, 2, 3, 4];
let newNumberList = numberList.map(function(number){
    return number * 2;
}).map(function(number){
    return number + 1;
});
console.log("The list of doubled and incremented numbers: ", newNumberList); // [3, 5, 7, 9]
```

De intentie kan ook in een benoemde functie gedefinieerd worden die verschillende keren na elkaar wordt opgeroepen. Om bijvoorbeeld een getal te verviervoudigen kan de methode `double` twee keer aan elkaar geketend worden.

```javascript
let numberList = [1, 2, 3, 4];
let double = function(a) {
 return a * 2;
}
let newNumberList = numberList.map(double).map(double);
console.log("The list of doubled and incremented numbers: ", newNumberList); // [4,8,12,16]
```

