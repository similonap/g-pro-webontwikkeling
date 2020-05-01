# closures in JS

## definitie

Een **closure** is eigenlijk een functie in een functie. Deze \(interne\) functie heeft toegang tot de parameters en variabelen van de omvattende functie. Bovendien blijft de staat bewaard, zelfs als de omvattende functie klaar is. Het volgende voorbeeld laat zien hoe dat in de praktijk werkt.

## een probleem...

Een simpel probleem kan eenvoudig opgelost worden met closures.  
Veronderstel dat er bepaalde events moeten geteld worden, bijvoorbeeld om te bepalen hoe vaak bepaalde code zal worden uitgevoerd. 

```javascript
increment(); // number of events is 1
increment(); // number of events is 2
increment(); // number of events is 3
```

Bovenstaande code zou elke keer als deze aangeroepen wordt bijvoorbeeld een bericht kunnen uitsturen met: "number of events: N”.

```javascript
let counter = 0;

const increment() => {
    counter = counter + 1;
    
    console.log("Number of events: " + counter);
}
```

Bovenstaande code is werkbaar en helemaal ok, maar wat bij twee of meer waardes. Je zou dit kunnen oplossen door voor beide waardes  twee losse functies te schrijven.

```javascript
let counter1 = 0;

const incrementCounter1() => {
    counter1 = counter1 + 1;
    
    console.log("Number of events: " + counter1);
}

let counter2 = 0;

const incrementCounter2() => {
    counter2 = counter2 + 1;
    
    console.log("Number of events: " + counter2);
}

incrementCounter1(); // number of events is 1
incrementCounter2(); // number of events is 1
incrementCounter1(); // number of events is 2
```

Bovenstaand voorbeeld bevat veel dubbele code die eenvoudig vervangen kan worden.

## ...opgelost met closure

Bovenstaande code wordt herschreven met een closure en ziet er als volgt uit:

```javascript
const createCounter() => {
    let counter = 0;
    
    const increment() => {
        counter = counter + 1;
        
        console.log("Number of events: " + counter);
    }
    
    return increment;
}
```

En de code kan dan als volgt gebruikt worden:

```javascript
let counter1 = createCounter();
let counter2 = createCounter();

counter1(); // number of events is 1
counter1(); // number of events is 2

counter2(); // number of events is 1

counter1(); // number of events is 3
```

### in detail

Het ziet er complex uit, maar dat is het allerminst. Stap voor stap wordt de functie doorlopen.

1. Een lokale variabele counter wordt aangemaakt.
2. Een lokale functie wordt aangemaakt - genaamd increment - die de lokale variabele counter kan verhogen. 

Het laatste voorbeeld lijkt sterk op het allereerste voorbeeld. Alleen nu staat er om de functie een andere functie, _enclosed_ in het Engels, vandaar de benaming **closures**.

    3. in de _createCounter_ functie wordt de lokale functie _increment_ teruggeven. Dat zorgt ervoor dat de lokale functie wordt aangeroepen. 

Dus als de _createCounter_ functie wordt aangeroepen, wordt er een nieuwe instantie gemaakt met elk een eigen counter. Elke variabele die deze functie aanroept, krijgt een eigen waarde van de lokale variabele counter.

