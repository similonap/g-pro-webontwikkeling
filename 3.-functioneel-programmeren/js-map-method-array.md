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





