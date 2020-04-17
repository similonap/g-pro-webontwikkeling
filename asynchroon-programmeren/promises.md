# promises

nieuwe manier om async code te schrijven "ik beloof met een resultaat te komen zodra ik klaar ben" beter overzicht dankzij chaining ook indien fouten zich voordoen!

een promise is: een tussentijdse staat van een operatie pending, niet succesvol, niet gefaald een belofte dat een resultaat eraan komt wanneer die klaar is: vervuld: je kan nu iets doen met resultaat afgekeurd: je krijgt een reden



```javascript
let promise = fetch('...'); // pending
promise.then(...) // wanneer die vervuld is, doe ...
promise.catch(...) // wanneer die afgekeurd is, doe ...
```

promise bevat NIET het resultaat

```javascript
let done = true;
const isItDone = new Promise((resolve, reject) => {
if (done) {
resolve("Done")
} else {
reject("Not done")
}
});
```

resolve\(result\) stuurt object terug als promise vervuld is   
then\(a =&gt; {}\) waar a === result   
reject\(error\) stuurt object terug als promise afgekeurd is   
catch\(a =&gt; {}\) waar a === error



```javascript
isItDone
    .then(msg => {
    console.log(msg)
    })
    .catch(err => {
    console.error(err)
    })
```

vb. fetch!

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

vb. fetch met chains

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
console.log("Code done");
```
