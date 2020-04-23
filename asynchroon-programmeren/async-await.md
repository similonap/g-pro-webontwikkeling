# async / await

andere manier om promises te schrijven   
duidelijkere syntax

```javascript
const hello = () => { return "Hello" };
hello();
```

async voor functie:

```javascript
const hello = async () => { return "Hello" };
hello();
```

geeft nu promise terug ipv "Hello"

await zorgt dat code wacht op het resultaat van een promise wanneer promise voltooid is, krijg je waarde terug

```javascript
const doFetch = async () => {
let result = await fetch(...);
// code hangt tot fetch klaar is
// result bevat resultaat!
}
```

enkel gebruiken in async functies

geen nood aan al die "then" chains

```javascript
const fetch = require('node-fetch');
const doFetch = async () =>{
let result = await fetch('https://pokeapi.co/api/v2/pokemon/ditto/')
let response = await result.json();
console.log(response.name);
}
doFetch();
console.log("code done");
```

test dit voorbeeld, kijk naar volgorde console.log

```javascript
const fetch = require('node-fetch');
const doFetch = async (pokemonName) =>{
let result = await fetch('https://pokeapi.co/api/v2/pokemon/'+pokemonName+'/')
let response = await result.json();
console.log(response.name + ' ' + response.id);
}
doFetch('1');
doFetch('2');
doFetch('3');
doFetch('4');
doFetch('5');
console.log("code done");
```

