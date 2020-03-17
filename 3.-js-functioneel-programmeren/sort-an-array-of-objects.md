# sort an array of objects

## Inleiding functioneel programmeren

In dit hoofdstuk leren we binnen JavaScript functioneel programmeren. Hiervoor maken we gebruik van hogere-ordefuncties `map`, `filter`, `reduce` binnen het `array` object.  
Deze methoden zijn native beschikbaar in elke recente browser en in Node.js. Het gebruik van deze functies is eigenlijk zeer eenvoudig, waardoor elke beginnende ontwikkelaar in eenvoudige scripts nuttige dingen kan realiseren.

meer info: [artikel](https://gofore.com/en/why-you-should-replace-foreach/) over het nut van het gebruik van `map` en `filter` functies

## sort and array of objects \(array\)

Om een array van objecten te sorteren in een bepaalde volgorde kan de verleiding groot zijn om op een JavaScript-bibliotheek beroep te doen. Vooraleer je dat echter doet, is het nuttig om te leren hoe je een array van objecten kan ordenen met de inheemse `Array.sort` functie. In [dit artikel](https://www.sitepoint.com/sort-an-array-of-objects-in-javascript/) leer je hoe je een array van objecten zonder al te veel moeite in JavaScript ordent.

## toepassing

Sorteer de elementen. Dit past de array zelf aan \(niet via return-waarde\).

```javascript
const numbers = [3,1,4,2];
numbers.sort();
// numbers = [1,2,3,4]
```

Kopieer de array in een nieuwe array om de originele volgorde te behouden.

```javascript
const numbers = [3,1,4,2];
numbersSorted = [...numbers].sort();
// numbersSorted = [1,2,3,4]
// numbers = [3,1,4,2]
```

Verschillende types kunnen ook gesorteerd worden. 

```javascript
const arr = [3, 'hallo', 1, 4, 2];
arr.sort();
// arr = [ 1, 2, 3 ,4, 'hallo' ]
```

De waarden worden omgezet naar strings, dus er wordt gesorteerd op basis van het eerste karakter, vandaar dat de uitkomst er in de console zo zal uitzien:  arr = \[ **1**2, **2**, **2**2, **3**, **4** \]

```javascript
const arr = [3,2,12,22,4];
arr.sort();
// arr = [ 12, 2, 22, 3, 4 ]
```

## sort functies

Sorteerfunctie bepaalt welk element groter of kleiner is. Stel dat er 2 variabele zijn, namelijk **a** en **b**.

* sorteerfunctie moet &lt; 0 teruggeven als **a &lt; b**
* sorteerfunctie moet &gt; 0 teruggeven als **a &gt; b**
* sorteerfunctie moet 0 teruggeven als **a === b**

In onderstaand voorbeeld worden getallen vergeleken.

```javascript
const sortingNumbers = (a,b) => {
    if(a<b) return -1;
    if(a>b) return 1;
    return 0;
}
```

Hierna kan deze functie doorgegeven worden aan sort.

```javascript
const arr = [3,2,12,22,4];
arr.sort(sortingNumbers);
// arr = [ 2, 3, 4, 12, 22 ]
```

Het kan ook nog een stuk eenvoudiger.

```javascript
const arr = [3,2,12,22,4];
arr.sort((a,b) => {
    if(a<b) return -1;
    if(a>b) return 1;
    return 0;
});
// arr = [ 2, 3, 4, 12, 22 ]
```

... of nog korter.

```javascript
const arr = [3,2,12,22,4];
arr.sort((a,b) => {
    return a-b;
});
// arr = [ 2, 3, 4, 12, 22 ]
```

## sort functies & objecten

```javascript
const arr = [
    {name:'George', age:33},
    {name:'Abe', age:20},
    {name:'Mabel', age:29}
];
```

```javascript
arr.sort((a,b)=>{
    const name1 = a.name.toUpperCase();
    const name2 = b.name.toUpperCase();
    if(name1 < name2 ) return -1;
    if(name1 > name2 ) return 1;
    return 0;
}
);

/*
[
    { name: 'Abe', age: 20 },
    { name: 'George', age: 33 },
    { name: 'Mabel', age: 29 }
]
*/
```

```javascript
arr.sort((a,b)=>{
    if(a.age < b.age ) return -1;
    if(a.age > b.age ) return 1;
    return 0;
}
);

/*
[
    { name: 'Abe', age: 20 },
    { name: 'Mabel', age: 29 },
    { name: 'George', age: 33 }
]
*/
```



#### BRONNEN

Olayinka Omole, [Quick Tip: How to Sort an Array of Objects in JavaScript](https://www.sitepoint.com/sort-an-array-of-objects-in-javascript/?utm_source=javascriptweekly&utm_medium=email), March 01, 2017

