# labo 4: Javascript in-depth + API

### 1. FizzBuzz

**Dit is een bekende sollicitatievraag bij bedrijven:**

Schrijf een programma dat getallen van 1 tot 100 print. Maar voor veelvouden van 3 print "Fizz" in plaats van het getal en voor veelvouden van 5 print "Buzz". Voor getallen die veelvouden zijn 3 en 5 print je "FizzBuzz". 

Voorbeeld output: 

```text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz 
11
Fizz
13
14
FizzBuzz
16
```

### 2. Getallen zoeken

```text
var items = [2, 5, 3, 7, 8, 10, 15, 18, 24, 111, 12, 19, 87];

const search = (items, number) => {
    // vul aan
}
```

schrijf een functie die een getal zoekt in de bovenstaande array en de index teruggeeft in de array.

**Voorbeeld**:

```text
 console.log(search(items, 5)); // 1 
 console.log(search(items, 15)); // 6
```

### 3. Cocktails zoeken

We gaan gebruik maken van een publieke API om cocktails op te zoeken aan de hand van hun naam. Een overzicht van de API kan je op de volgende pagina vinden.

{% embed url="https://www.thecocktaildb.com/api.php?ref=apilist.fun" %}

Maak een nieuw project aan en installeer de request module en de readline-sync module. 

```text
npm init
npm install --save node-fetch readline-sync
```

De eerste library is al bekend van de theorie.  Je kan er eenvoudig requests mee maken naar een API. De tweede library is een library voor input te vragen aan de gebruiker \( een beetje zoals Console.ReadLine in C\#\):

```text
// Voorbeeld gebruik:
var readlineSync = require('readline-sync');

var userName = readlineSync.question('May I have your name? ');
console.log('Hi ' + userName + '!');
```

Schrijf nu een programma dat een bepaalde string vraagt aan de gebruiker. Als de gebruiker niets ingeeft moet het programma een foutmelding geven. Als het niet leeg is dan moet je de string gebruiken om te zoeken naar cocktails met de volgende API call:

```text
https://www.thecocktaildb.com/api/json/v1/1/search.php?s=<searchstring>
```

Loop over alle cocktails en print de naam van de cocktail in de console.

**Voorbeeld output:**

```text
Naar welke cocktail wil je zoeken?
De zoekstring mag niet leeg zijn.

Naar welke cocktail wil je zoeken? Mar

Martini
Tia-Maria
Margarita
Bob Marley
Martinez 2
Aquamarine
Bloody Mary
...
```

\*\*\*\*

