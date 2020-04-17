# asynchronous callbacks

Asynchrone callbacks binnen web client code kwamen reeds aan bod in het vak 'webtechnologie', namelijk de EventListeners gelinkt aan bijvoorbeeld buttons.

```javascript
btn.addEventListener('click'
, () => {
alert('You clicked me!');
});
alert('event listener added')
```

De tweede parameter is de callback-functie. De listener wordt geregistreerd  en de alert 'even listener added' wordt uitgevoerd.  
De callback wordt geregistreerd, maar pas uitgevoerd wanneer de gebruiker effectief op button drukt.



het fakeFetch voorbeeld met callback

```javascript
let data = undefined
let fakeFetch = (callback) =>{
setTimeout(()=>{
data = {name:'sven'
,age:'39'};
console.log('data is ready');
callback();
},
2000)
}
fakeFetch(
()=>{console.log('data content: ' + JSON.stringify(data));}
);
```



wanneer code klaar is, roept die zelf de volgende code op \(callback\)

```javascript
//callback hell
const funcA = (callback) => funcB(callback);
const funcB = (callback) => funcC(callback);
const funcC = (callback) => funcD(callback);
const funcD = (callback) => callback();
funcA(()=>console.log('done'));
```

wat als iets misloopt?





