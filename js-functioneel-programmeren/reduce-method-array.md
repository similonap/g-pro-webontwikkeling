# reduce method \(array\)

**En wat als je de waarden in een array op een of andere manier wilt combineren?**

* De `reduce` methode herleidt de array naar één enkele waarde. 
* De `reduce` methode voert de ingevoerde functie uit voor elk element in de array, van links naar rechts. De `reduceRight` methode doet hetzelfde, maar van rechts naar links. 
* De geretourneerde waarde van deze functie wordt in een accumulator \(result/total\) opgeslagen. 
* De `reduce` methode respecteert de regels van niet te muteren en geen neveneffecten te veroorzaken. Hierbij maakt het niet uit wat voor soort waarde er in de array staan. Het kan gaan om het optellen van een getal, het aaneenschakelen van een string, het samenstellen van een object,..
* De `reduce` methode retourneert alleen de 'totale waarde'  en die kan je niet koppelen of chainen.
* Let wel, de `reduce` methode wordt niet uitgevoerd op elementen in de array zonder waarde.

## syntax

```javascript
array.reduce(function(total,currentValue,currentIndex,arr),initialValue)
```

## parameters en argumenten

`function(total, currentValue, index, arr)` __is een functie die voor elk element in de array uitgevoerd zal worden \(**verplichte parameter**\)

* `total` __is de waarde die geretourneerd wordt door de functie, of de `initialValue` \(**verplicht argument**\)
* `currentValue` __is de waarde van het lopende element \(**verplicht argument**\)
* `currentIndex` is de array-index van het lopende element \(**optioneel argument**\)
* `arr` is de array waartoe het lopende element behoort \(**optioneel argument**\)

`initialValue` is de beginwaarde die je aan de functie kan meegegeven \(**optionele parameter**\)

## toepassing

De faculteit berekenen wordt meestal gebruikt in een inleiding tot recursief programmeren.   
We vertrekken van de niet-recursieve implementatie ervan...

```javascript
function factorial(n) {
  let f = 1;
  for (let c = 1; c < = n; ++c)
  {
     f *= c;
  }
  return f;
}
```

... en kunnen deze vervangen door een functionele aanpak...

```javascript
function factorial(n) {
  return Array.apply(0, Array(n)).reduce(function(x, y, z) { return x + x * z; }, 1);
}
```

... en bovenstaande code geschreven met de pijlfunctie \(ECMAScript 6 versie\).

```javascript
function factorial(n) {
  return Array.apply(0, Array(n)).reduce((x, y, z) => x + x * z, 1);
}
```



#### BRONNEN

Una Kravets, [An Illustrated \(and Musical\) Guide to Map, Reduce, and Filter Array Methods](https://css-tricks.com/an-illustrated-and-musical-guide-to-map-reduce-and-filter-array-methods/), Mar 26, 2019  
Vicky Lay, [Understanding Array.prototype.reduce\(\) and recursion using apple pie](https://vickylai.io/verbose/reduce-recursion-with-pie/), May 18, 2017  
M. David Green, [Using Map and Reduce in Functional JavaScript](http://www.sitepoint.com/map-reduce-functional-javascript/?utm_source=SitePoint&utm_medium=email&utm_campaign=Versioning&utm_medium=email&utm_campaign=Versioning%20433&utm_content=Versioning%20433+Version+B+CID_56cfa583c9ca80334b0f9e11cf5eecfa&utm_source=CampaignMonitor%20SitePoint&utm_term=How%20to%20use%20map%20and%20reduce%20in%20JavaScript), March 28, 2016

