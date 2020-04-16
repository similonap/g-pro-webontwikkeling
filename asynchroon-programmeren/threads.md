# threads

Een **thread** is in feite één enkel proces dat een programma kan gebruiken om taken te voltooien. Elke thread kan slechts één taak tegelijk uitvoeren. Elke taak wordt achtereenvolgens uitgevoerd en de taak moet voltooid zijn, voordat de volgende kan opgestart worden.

```javascript
taak a -> taak b -> taak c
```

De meeste computers hebben meerdere kernen \(cores\), waardoor ze  meerdere dingen tegelijk kunnen doen. Sommige programmeertalen die meerdere threads ondersteunen \(multi-threaded\), kunnen dus meerdere cores gebruiken om threads **naast** elkaar en gelijktijdig te laten uitvoeren .

```javascript
taak a -> taak b -> taak c
taak 1 -> taak 2 -> taak 3
```

Het voorbeeld bij 'blocking code' waarbij code tijdrovende berekeningen moet uitvoeren, kan zodoende opgelost worden door het te splitsen in 2 threads.

```javascript
//thread 1
let sum = 0;
for(let i=0;i<99999999999;i++){
sum+=i;
}
console.log('sum done');
```

```javascript
//thread 2
let mult = 1;
for(let i=0;i<99999999999;i++){
mult*=i;
}
console.log('mult done');
```

De code werd dus opgesplitst in 2 threads, waar thread 1 niet wacht op thread 2 en omgekeerd.  Maar wat gedaan als je iets wil doen met de resultaten van thread 1 en 2. Hoe komen we te weten wanneer thread 1 en thread  2 klaar zijn?

```javascript
//wanneer zijn threads klaar?
let total = sum + mult; 
```

