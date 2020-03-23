# recursive function

## definitie

**Recursie** \(recursion\) is wanneer een functie zichzelf oproept. 

```javascript
const factorial(x) => {
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
const factorial(x) => {
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
const factorial(x) => {
  if (x < 0) return; // is termination condition of beëindigingsvoorwaarde
  if (x === 0) return 1; // is base case of basisscenario
  return x * factorial(x - 1);
}
factorial(3);
// 6
```

  
In het faculteitvoorbeeld is  `if (x === 0) return 1;` het basisscenario. Van zodra x tot nul werd teruggebracht is het gelukt de faculteit te bepalen.

### recursion



