# recursive function

## definitie

**Recursie** \(recursion\) is wanneer een functie zichzelf oproept. 

```javascript
const factorial = (x) => {
  if (x < 0) return;
  if (x === 0) return 1;
  return x * factorial(x - 1);
}
factorial(3);
// 6
```

Bovenstaand voorbeeld retourneert de faculteit van een geleverd geheel getal.   
Op lijn 4 roept de functie zichzelf terug op`factorial(x-1),`maar met een parameter die 1 minder is dan toen die een eerste keer werd opgeroepen. Dit maakt het een **recursieve functie**.

**reminder omtrent faculteit**  
Om de faculteit van een getal te verkrijgen, vermenigvuldig het getal met zichzelf min één totdat  nummer één bereikt wordt. 

* voorbeeld 1: de faculteit **4** is 4 \* 3 \*  2 \*  1 = **24**
* voorbeeld 2: de faculteit van **2** is 2 \* 1 = **2**

## 3 hoofdkenmerken

### termination condition

Termination condition is een **beëindigingsvoorwaarde** waar eenvoudigweg gezegd wordt: 

```javascript
if(something bad happened){ STOP };
```

Zie de termination condition als een **noodrem**. Het wordt daar geplaatst in het geval van slechte invoer, om zo te voorkomen dat de recursie ooit wordt uitgevoerd. 

```javascript
const factorial = (x) => {
  if (x < 0) return; // is termination condition of beëindigingsvoorwaarde
  if (x === 0) return 1;
  return x * factorial(x - 1);
}
factorial(3);
// 6
```

In ons faculteitvoorbeeld is `if (x < 0) return;` de termination condition. Het is namelijk niet mogelijk om de faculteit te nemen van een ​​negatief getal. Daarom zal de recursie stoppen en dus niet doorgaan als een negatief getal wordt ingevoerd.

### base case

De base case of **basisscenario** lijkt sterk op de termination condition, waarbij de base case de recursie effectief stopt.

```javascript
if(this happens) { Yay! We're done };
```

Daar waar de terminal condition een verzamelpunt of _catch-all_ is voor slechte data, is het basisscenario het doel van de recursieve functie. Base cases bevinden zich meestal binnen een `if-statement`. 

```javascript
const factorial = (x) => {
  if (x < 0) return; // is termination condition of beëindigingsvoorwaarde
  if (x === 0) return 1; // is base case of basisscenario
  return x * factorial(x - 1);
}
factorial(3);
// 6
```

  
In het faculteitvoorbeeld is  `if (x === 0) return 1;` het basisscenario. Van zodra x tot nul werd teruggebracht is het gelukt de faculteit te bepalen.

### recursion

De recursie is de functie die zichzelf oproept. 

```javascript
const factorial = (x) => {
  if (x < 0) return; // is termination condition of beëindigingsvoorwaarde
  if (x === 0) return 1; // is base case of basisscenario
  return x * factorial(x - 1); // is de recursion of recursieve functie
}
factorial(3);
// 6
```

In het faculteitvoorbeeld is  `return x * factorial (x - 1);` de plaats waar de recursie daadwerkelijk plaatsvindt. De waarde van het getal x wordt geretourneerd en vermenigvuldigd met de waarde van de faculteit \(x-1\) op dat moment.

dus de drie hoofdkenmerken samengevat:

```javascript
const factorial = (x) => {
  // TERMINATION
  if (x < 0) return;  
  
  // BASE
  if (x === 0) return 1;  
  
  // RECURSION
  return x * factorial(x - 1);
}

factorial(3);
// 6
```

## toepassing 1 - in detail

### functiestroom faculteit

**Wat gebeurt er als de functie factorial wordt aangeroepen?**  
Door het aanroepen wordt de waarde 3 doorgegeven:

```javascript
factorial(3);
```

Dit resulteert dat de functie wordt uitgevoerd, waarin beide if-statements niet van toepassing zijn en de recursie dus aan de orde is. hierbij wordt het gehele getal 3 doorgegeven en vermenigvuldigd met de waarde van `factorial(3-1)`.

```javascript
return 3 * factorial(2);
```

Wanneer`factorial(2)` wordt uitgevoerd, zijn beide if-statements wederom niet van toepassing en biedt de recursie zich aan. Het gehele getal 2 wordt geretourneerd en vermenigvuldigd met de waarde van `factorial (2-1)`. 

```javascript
return 2 * factorial(1#);
```

Wanneer`factorial(1)`wordt uitgevoerd, zijn beide if-statements wederom niet van toepassing en biedt de recursie zich aan. Het gehele getal 1 wordt geretourneerd en vermenigvuldigd met de waarde van `factorial (1-1)`. 

```javascript
return 1 * factorial(0);
```

Wanneer`factorial(0)`wordt uitgevoerd, gebeurt er iets anders. Nul is de base case of basisscenario, zodat wanneer de if-statement slaagt de functie 1 retourneert.

```javascript
if (x === 0) return 1;
```

De functie is eindelijk afgerond. De recursie is een groep geneste functies die worden aanroepen. Bij geneste functies komt de meest interne geneste functie als eerste terug.

`factorial(0)` returns **1**  
`factorial(1)` returns `1 * factorial(0)`, of **1 \* 1**  
`factorial(2)` returns `2 * factorial(1)`, of **2 \* 1 \* 1**  
`factorial(3)` returns 3 `* factorial(2)`, of **3 \* 2 \* 1 \* 1**

```javascript
return 1 * 1 * 2 * 3
// 6
```

### anders gestructureerd

```javascript
factorial(3) returns 3 * factorial(2)
factorial(2) returns 2 * factorial(1)
factorial(1) returns 1 * factorial(0)
factorial(0) returns 1

// Binnen base case of het basisscenario zal 
//de functie retourneren van binnen naar buiten:
factorial(0) returns 1                 => 1
factorial(1) returns 1 * factorial(0)  => 1 * 1
factorial(2) returns 2 * factorial(1)  => 2 * 1 * 1
factorial(3) returns 3 * factorial(2)  => 3 * 2 * 1 * 1

// 3 * 2 * 1 * 1 = 6
```



## toepassing 2

**Wat gebeurt er als een string moet omgedraaid worden?**

Onderstaande code komt uit een populair voorbeeld van het internet om 'reversing' uit te leggen. Weet wel dat er een meer efficiënte manier bestaat, maar deze code is dus geschreven met als doel het nog beter begrijpen van de recursieve functie.

```javascript
const revStr = (str) => {
  if (str === '') return '';
  return revStr(str.substr(1)) + str[0];
}
revStr('cat');
// tac
```

1. `str === ""` is ons basisscenario. Wanneer de string geen karakters meer bevat, is de functie geslaagd. 
2. `return revStr(str.substr(1)) + str[0];` is waar de recursie plaatsvindt. 
3. Hier is er geen termination condition of **beëindigingsvoorwaarde.** In deze toepassing komt de base case overeen met de termination case. Er kan geen tekenreeks verkrijgen worden die negatieve tekens heeft. dus zolang er alleen strings in de functie worden ingevoerd, zit alles goed.

### in detail

In dit voorbeeld wordt de string 'cat' omgedraaid. De functie wordt hiervoor aangeroepen en de string 'cat' wordt doorgegeven.

```javascript
revStr('cat');
```

De recursieve functie wordt uitgevoerd. In JavaScript retourneert de methode`substr ()`een string die begint op een specifieke locatie, hier dus `'cat'.substr (1) === 'at'`  
`str [0]` geeft het karakter bij die index in de string, dus hier `cat [0] === 'c'`

```javascript
return revStr(str.substr(1)) + str[0];

// zelfde als
return revStr('at') + 'c'
```

De recursieve functie wordt terug uitgevoerd.

```javascript
return revStr(str.substr(1)) + str[0];

// zelfde als
return revStr('t') + 'a'
```

En de recursieve functie wordt voor een laatste keer uitgevoerd.

```javascript
return revStr(str.substr(1)) + str[0];

// zelfde als
return revStr('') + 't'
```

Nu wordt de base case aangeroepen en die retourneert een lege string.

```javascript
if (str === '') return '';
```

De functie is eindelijk afgerond en alles zal teruggegeven worden in omgekeerde volgorde.

```javascript
return ‘’ + ‘t’ + ‘a’ + ‘c’
// tac
```

### anders gestructureerd

```javascript
revStr('cat')  returns revStr('at') + 'c'
revStr('at')   returns revStr('t') +  'a'
revStr('t')    returns revStr('') +   't'
revStr('')     returns               ''
```

Dit zijn allemaal geneste functies die worden aangeroepen. Wanneer geneste functies worden aangeroepen, keert de meest interne geneste functie als eerste terug. Dit initialiseert het omkeren zodat ze terug in de juiste volgorde komen te staan.

```javascript
revStr('')     returns                ''  => ''
revStr('t')    returns revStr('') +   't' => '' + 't'
revStr('at')   returns revStr('t') +  'a' => '' + 't' + 'a'
revStr('cat')  returns revStr('at') + 'c' => '' + 't' + 'a' + 'c'
// tac
```

  


