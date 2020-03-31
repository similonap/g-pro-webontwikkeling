# labo 8: Asynchronous JavaScript

### 1. Maak het project aan

Open Visual Studio Code en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm-package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn.

### **2. Promises**

maak een bestand `slow_math.js` met de volgende inhoud:

```javascript
const slowSum = (a,b) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a+b);
        },1000)
    });
}

const slowMult = (a,b) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(a*b);
        },1500)
    });
}
```

Dit zijn 2 functies die een promise terug geven. Ze simuleren een trage som functie en een trage vermenigvuldigings functie. 

1. Roep de `slowSum` functie aan met de getallen 1 en 5 en zorg dat ze het resultaat van deze functie op het scherm laat zien. \(zie output\)
2. Roep de `slowSum` functie opnieuw aan met de getallen 1 en 5 maar zorg deze keer dat na het optellen de vermenigvuldigings functie \``slowMult` wordt aangeroepen dat het resultaat vermenigvuldigd met 2 en dan op het scherm laat zien. \(zie output\)
3. Maak een eigen `slowDiv` functie dat een deling doet \(laat deze 2000 milliseconden duren\). Zorg ervoor dat als je een deling door nul doet dat je de promise afkeurt met de melding "You cannot divide by zero". 
4. Roep deze functie aan met de getallen 6 en 3 en laat het resultaat op het scherm zien. \(zie output\)
5. Roep deze functie aan met de getallen 6 en 0 en laat de error op het scherm zien. \(zie output\)

**Verwachte output:**

```text
➜  node set_timeout.js
You cannot divide by zero
1 + 5 = 6
(6 / 3) = 2
(1 + 5) * 2 = 12
```

### **3. Promises.all en fetch**

maak een bestand `cocktail.js` en installeer de dependency node-fetch:

```text
npm install node-fetch --save
```

Maak gebruik van `Promise.all` om de drie volgende cocktails via de cocktail api met de volgende ids in te lezen: **11000**, **11001**, **11002** en vervolgens de naam van de drie cocktails op het scherm te laten zien. 

Je kan een cocktail via een id via de volgende api call binnenhalen:

```text
https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=11000
```

**Verwachte output:**

```text
Mojito
Old Fashioned
Long Island Tea
```

