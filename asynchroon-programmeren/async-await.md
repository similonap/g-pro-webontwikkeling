# async / await

Async/await is een andere manier om promises te schrijven, waarbij de syntax veel duidelijkere is. Dit mag **enkel gebruikt worden in asynchrone functies**.

```javascript
const hello = () => { return 'Hello' };
let message = hello();
console.log(message);
```

```javascript
$ node test.js
Hello
```

### async

Het woord `async` voor functie plaatsen maakt dat de code niet geblokkeerd wordt. Door de toevoeging van `async` wordt geen waarde teruggegeven, maar geeft **async een promise** terug.

```javascript
const hello = async () => { return 'Hello' };
let promise = hello();
promise.then(msg => console.log(msg)); // geeft nu promise terug ipv "Hello"
```

```javascript
$ node test.js
Promise {'Hello'}
```

### await

Het woord `await` zorgt dat code wacht op het resultaat van een promise. En wanneer de promise voltooid is, krijg je een waarde terug.

```javascript
const doFetch = async () => {
let result = await fetch(...);
// code blijft hangen tot fetch klaar is
// result bevat resultaat!
}
```

#### 

**voorbeeld**: door gebruik async/await is er geen nood aan 'then'-chains

```javascript
const fetch = require('node-fetch');
const doFetch = async () =>{
    let result = await fetch('https://pokeapi.co/api/v2/pokemon/ditto/')
    let response = await result.json();
    console.log(response.name);
}
doFetch();
console.log('code done');
```

```javascript
$ node test.js
code done
ditto
```

#### 

**voorbeeld**: let op voor volgorde output console.log!

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
console.log('code done');
```

```text
$ node test.js
code done
bulbasaur 1
ivysaur 2
charmeleon 5
charmander 4
venusaur 3
```

## exceptions

**voorbeeld**: opvangen van reject met `catch`

```javascript
let done = false;

const isItDone = new Promise((resolve, reject) => {
    if (done) {
        resolve('Done')
    } else {
        reject('Not done')
    }
});

let run = async() =>{
    try{
        let result = await isItDone;
        console.log(result);
    }
    catch(exception){
        console.log(exception);
    }
}
run();
```

```javascript
$ node test.js
Not done
```



**voorbeeld**: correcte methode voor fetch

```javascript
const fetch = require('node-fetch');
const doFetch = async () =>{
    try{
      let result = await fetch('https://pokeapi.co/api/v2/pokemon/ditto/')
      let response = await result.json();
      console.log(response.name);
    }
    catch(exc){
      console.log('error');
    }
}
doFetch();
console.log('code done');
```

```javascript
$ node test.js
Not done
```

