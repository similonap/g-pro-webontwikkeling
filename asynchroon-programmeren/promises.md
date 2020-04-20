# promises

Promises zijn de nieuwe stijl van asynchroon code schrijven die veelal in moderne web-API's gebruikt wordt. Concreet beloof 'promises' met een resultaat te komen van zodra die klaar is. Door het gebruik van promises wordt er propere code geschreven en is er een beter overzicht dankzij chaining, handig wanneer er zich ook fouten voordoen.

## definitie

Een promise is een tussentijdse staat van een operatie, volop bezig \(**pending**\) om de server te raadplegen, maar de uitkomst is nog niet geweten, of het al dan niet succesvol was of net niet en dus gefaald heeft.   
Een promises is dus een belofte dat er een resultaat aan staat te komen. Wanneer de promise **vervuld** is, dan kan er met het resultaat iets gedaan worden. Indien de promise echter werd **afgekeurd,** zal ook de reden waarom meegegeven worden. De promise **bevat dus niet het resultaat**.

## structuur

```javascript
// Dit is dus de structuur van promise.
let promise = fetch('...'); // pending
promise.then(...); // wanneer die vervuld is, doe ...
promise.catch(...) // wanneer die afgekeurd is, doe ...
```

## maken van een promise

```javascript
let done = true;

const isItDone = new Promise((resolve, reject) => {
    if (done) {
        resolve('Done')
    } else {
        reject('Not done')
    }
});
```

Er is een variabele `done`. De variabele `isItDone` geeft een promise terug. Deze promise verwacht een anonieme functie met twee parameters:

* resolve\(result\) stuurt object \(of boodschap\) terug als promise vervuld is 
  * `then(a => {})` waar a === result 
* reject\(error\) stuurt object \(of boodschap\) terug als promise afgekeurd is 
  * `catch(a => {})` waar a === error

De promise in bovenstaande code werd aangemaakt, uitgevoerd, maar binnen de code werd er niets mee gedaan. Hij zal dus een promise terug geven, maar niet de waarde.

```javascript
let done = true;

const isItDone = new Promise((resolve, reject) => {
    //js voert promise uit (2)
    if (done) {
        resolve('done') //resolve wordt uitgestuurd (3)
    } else {
        reject('not done')
    }
});
// dit gebeurt er als promise gelukt is
isItDone.then(msg => console.log(msg)); //en msg word uitgestuurd(4)
// dit gebeurt er als promise faalt
isItDone.catch(err => console.log(err));

console.log('code afgelopen'); //in terminal (1)
```

```javascript
$node test.js
code afgelopen // uitkomst van regel 16
done // uitkomst van regel 12
```

### promise met fetch

```javascript
const fetch = require('node-fetch');
let ditto = {};
let promise1 = fetch('https://pokeapi.co/api/v2/pokemon/ditto/');
let promise2 = promise1.then(response => response.json());
let promise3 = promise2.then(json => {
ditto = json;
console.log('JSON loaded into ditto');
console.log('weight: ' +JSON.stringify(ditto.weight));
});
let errorCatching = promise3.catch(err => {
console.log('Something went wrong: ' + err.message);
})
console.log('code finished');
console.log('ditto === ' + JSON.stringify(ditto));
```

### fetch met chains

```javascript
const fetch = require('node-fetch');
let ditto = {};
fetch('https://pokeapi.co/api/v2/pokemon/ditto/')
.then(response => response.json())
.then(json => {
ditto = json;
console.log('JSON loaded into ditto');
console.log('weight: ' + JSON.stringify(ditto.weight));
})
.catch(err => {
console.log('Something went wrong: ' + err.message);
});
console.log('code finished');
console.log('ditto === ' + JSON.stringify(ditto));
```

## multiple promises

Verschillende promises   
combineren van de resultaten

```javascript
let a = fetch(url1);
let b = fetch(url2);
let c = fetch(url3);
Promise.all([a, b, c]).then(values => {
...
});
```

then\(values =&gt; { wordt pas uitgevoerd als   
promise a klaar is EN   
promise b klaar is EN   
promise c klaar is

### multiple pokemon promises

```javascript
const fetch = require('node-fetch');
let promise1 = fetch('https://pokeapi.co/api/v2/pokemon/ditto/').then(response => response.json());;
let promise2 = fetch('https://pokeapi.co/api/v2/pokemon/pikachu/').then(response => response.json());;
let promise3 = fetch('https://pokeapi.co/api/v2/pokemon/charmander/').then(response => response.json());;
Promise.all([promise1,promise2,promise3]).then(
(pokemon) => {
console.log(pokemon[0].name);
console.log(pokemon[1].name);
console.log(pokemon[2].name);
}
)
console.log('Code done');
```

