# asynchronous callbacks

### voorbeeld EventListener

Asynchrone callbacks binnen **web client code** kwamen reeds aan bod in het vak 'webtechnologie', namelijk de **EventListener** gelinkt aan bijvoorbeeld buttons.

```javascript
btn.addEventListener('click', () => {
    alert('You clicked me!');
});
alert('event listener added')
```

De tweede parameter is de callback-functie. De listener wordt geregistreerd, maar verder wordt hier niets mee gedaan. De alert 'even listener added' wordt wel uitgevoerd. De callback wordt geregistreerd, maar pas uitgevoerd wanneer de gebruiker effectief op button drukt.

### voorbeeld 2 \(fakeFetch met callback\)

Aan de variabele fakeFetch wordt een callback meegegeven \(callback mag ook anders noemen\). De callback wordt pas uitgevoerd als de data geladen is. Concreet wordt de code als callback-functie meegegeven aan fakeFetch. De callback wordt dus pas uitgevoerd als de setTimeout compleet is. Pas dan wordt eindelijk de data content getoond.

```javascript
let data = undefined
let fakeFetch = (callback) =>{
    setTimeout(()=>{
        data = {name:'sven',age:'39'};
        console.log('data is ready');
        callback();
    },
    2000)
}

fakeFetch(
    ()=>{console.log('data content: ' + JSON.stringify(data));}
);
```

Onderstaande uitkomst wordt in de terminal getoond als resultaat van bovenstaande code . Let wel, de volgorde van de uitkomst is veranderd tegenover de uitkomst van voorbeeld 2 uit het vorige topic onder 'asynchroon programmeren'.

```javascript
$ node voorbeeld2
data is klaar // dit wordt in de terminal weergegeven na 2 seconden
data content:{"name":"sven","age":"39"}
```

### voorbeeld callbackHell

Stel... er is een callback die een callback doet, die op zijn beurt ook een callback doet en die op zijn beurt terug een callback doet... en dan pas klaar is. Dat vraagt om potentiële problemen.  
funcA krijgt een callback mee, die gaat naar funcB die ook een callback meekrijgt, en dat tot funcD benaderd wordt.  
Wanneer code klaar is, roept die zelf de volgende code op \(callback\), die dan op zijn beurt ook waar data moet ophalen en dan weer moet wachten om naar de volgende functie met callback te kunnen gaan. Onderstaand code is een summier voorbeeld van een callback hell. 

```javascript
//callbackHell
const funcA = (callback) => funcB(callback);
const funcB = (callback) => funcC(callback);
const funcC = (callback) => funcD(callback);
const funcD = (callback) => callback();
funcA(()=>console.log('done'));
```

```javascript
$ node callbackHell
done
```

Maar wat als iets misloopt?  Dé oplossing zijn 'promises'.



