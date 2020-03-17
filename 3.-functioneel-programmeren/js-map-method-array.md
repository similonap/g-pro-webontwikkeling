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
Elk getal wordt nu twee keer verdubbeld en hierbij worden de arrays niet handmatig beheerd. We gebruiken gewoon functies die een transformatie toepassen op een enkele waarde.

```javascript
let numberList = [1, 2, 3, 4];
let double = function(a) {
 return a * 2;
}
let newNumberList = numberList.map(double).map(double);
console.log("The list of doubled and incremented numbers: ", newNumberList); // [4,8,12,16]
```

## afspraken omtrent gebruik

Je moet wel rekening houden met enkele 'regels' voor de `map` functies. JavaScript verplicht het niet om die regels na te leven. De regels toch naleven maakt het een stuk makkelijker om te begrijpen wat de code doet.

### invoer- vs uitvoerelementen

Het aantal invoerelementen is gelijk aan het aantal uitvoerelementen  
Je kan in de `map` methode geen 4 waarden invoeren, en er slechts 3 terugkrijgen. Als de bron-array X aantal elementen heeft, zal de resulterende array ook X aantal elementen bevatten. Elk uitvoerelement komt overeen met het invoerelement in dezelfde positie. Ze worden nooit rond geschud.

### invoerwaarden niet muteren

De callback functies mogen geen ingevoerde waarden muteren  
Dit betekent dat je moet geen objecten of arrays rechtstreeks vanuit je callback functies mag wijzigen. Je kan best de invoerwaarde van een object of een array klonen het in plaats daarvan, en de kopie ervan wijzigen.  
  
Op deze manier is er een garantie dat je callback geen neveneffecten veroorzaakt. Dat wil zeggen dat, wat er ook gebeurt in je callback, het alleeninvloed heeft op de kopie. Dit zorgt voor betrouwbare code.  
  
Je kan een array in Javascript met de `array.slice (0)` methode klonen. Dat is echter ondiep klonen, namelijk als de waarden in de array zelf arrays of objecten zijn, hebben die nog steeds dezelfde waarden als in de originele array.  
  
Diepe-klonen maken van een object is ingewikkelder. In een CommonJS omgeving \(Node.js, Webpack, Browserify, ...\), kan je gebruik maken van de `Xtend` module. In het slechtste geval maak je zelf een functie:

```javascript
functie clone (o) {
   let newO = {};
   for (let keyin o) {
      newO [key] = o[key];
   }
   return newO;
}
let cloned = clone(originalObject);
```

Er is een uitzondering op deze regel, maar we dat later krijgt - gewoon aannemen dat deze regel altijd van toepassing, tenzij anders aangegeven.

### geen neveneffecten

Geen neveneffecten veroorzaken  
Doe nooit iets in een `map` methode dat de 'state' ergens anders wijzigt.

### delay door transformatie waarden?

Maar vertragen die callbacks en al dat klonen niet het programma? Daarover hoef je je geen zorgen te maken. Deze operaties lopen als een trein in Javascript, vooral in de V8-gebaseerde engines zoals Node.js. Code schrijf je in de eerste plaats voor de leesbaarheid. Prestatie komt op de tweede plaats. Het is veel gemakkelijker om leesbare code te optimaliseren, dan geoptimaliseerde code leesbaar te maken.

Maar wat als ik wil alleen een deel van de waarden te transformeren?

Misschien is uw bron array heeft een aantal waarden die u wilt transformeren, en een aantal waarden die u wil gewoon helemaal weg te gooien. Dat is niet mogelijk met kaart alleen, het aantal invoerwaarden en het aantal uitvoerwaarden voor een kaart gesprek altijd gelijk.

En met `map` kan je meer dan eenvoudige transformaties uitvoeren. Je methode kan gebruik maken van twee extra parameters, de lopende `index` en de `array` zelf. In het volgende voorbeeld:

```javascript
let starter = [1, 2, 3];
function multiplyByNextElement (value, i, a) {
    let next = i + 1;
    // If at the end of array
    // use the first element
    if (next === a.length) {
        next = 0;
    }
    return value * a[next];
}
let newA = starter.map(multiplyByNextElement);
console.log(newA); // Outputs: [2, 6, 3]
```

wordt het volgende element gebruikt om de transformatie uit te voeren.



#### BRONNEN

Una Kravets, [An Illustrated \(and Musical\) Guide to Map, Reduce, and Filter Array Methods](https://css-tricks.com/an-illustrated-and-musical-guide-to-map-reduce-and-filter-array-methods/), Mar 26, 2019  
M. David Green, [Using Map and Reduce in Functional JavaScript](http://www.sitepoint.com/map-reduce-functional-javascript/?utm_source=SitePoint&utm_medium=email&utm_campaign=Versioning&utm_medium=email&utm_campaign=Versioning%20433&utm_content=Versioning%20433+Version+B+CID_56cfa583c9ca80334b0f9e11cf5eecfa&utm_source=CampaignMonitor%20SitePoint&utm_term=How%20to%20use%20map%20and%20reduce%20in%20JavaScript), March 28, 2016



