# asynchroon programmeren

In voorbeeld 1 wordt een [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) genomen van een bepaalde API en de verkregen data zal dan gerenderd worden.

```javascript
//dit is pseudocode (geen echte code)
let data = fetch('http://webdev.com/api/getData');
res.render('/data',{mijnData:data}); //data nog niet klaar
```

Fetch moet echter wachten tot de data binnen is, want er wordt eerst geconnecteerd met de webserver \(call\), data wordt opgevraagd, **fetch wacht op het resultaat van de API** en pas als de data binnenkomt, kan deze verwerkt worden.  
Ondertussen **blokkeert JavaScript de uitvoering van de code niet** en worden de resultaten - die nog niet binnengekomen zijn, waardoor `let data` leeg is - gerendeerd \(res.render\). De uitkomst van mijnData zal **undefined** geven `mijnData === undefined`, want de uitvoering van het stuk code gebeurt voor de voltooing van fetch. JavaScript blokkeert de code dus niet. Dit blijkt hier een probleem, wanneer het renderen is afhankelijk van de resultaten van een eerder proces.  

```javascript
let data = undefined
let fakeFetch = () =>{
setTimeout(()=>{
data = {name:'sven'
,age:'39'};
console.log('data is ready')
},
2000)
}
fakeFetch();
console.log('data content: ' + JSON.stringify(data));
```

In voorbeeld 2 wordt er gestart met 2 variabelen: `let data` wordt niet gedefinieerd en `let fakeFetch`. De fakeFetch maakt gebruik van een setTimeout\(\), een functie die wordt uitgevoerd binnen x aantal seconden en fetch gaat een return van de data van de API geven binnen een aantal seconden. Er zit dus een vertraging op van hoe snel de data in de variabele terecht komt.  
 In de functie wordt na 2 seconden een object aangemaakt voor de data die terugkomt - en dus wordt de data van de functie fakeFetch met een delay van 2 seconden \(2000 milliseconden\) getoond in de terminal.

```javascript
$ node voorbeeld2
data content: undefined
data is klaar // dit wordt in de terminal weergegeven na 2 seconden
```

Modern software-ontwerp draait steeds meer om het gebruik van asynchrone programmering, zodat programma's meer dan één ding tegelijk kunnen doen. Naarmate je nieuwere en krachtigere API's gebruikt, zul je meer gevallen vinden waarbij de enige manier om dingen te doen het asynchroon programmeren is.   
Vroeger was het moeilijk om asynchrone code te schrijven. maar vandaag is dat gelukkig een stuk eenvoudiger geworden. In het volgende hoofdstuk bekijken we waarom asynchrone code zo belangrijk is en hoe code kan geschreven worden die enkele van de hierboven beschreven problemen vermijdt.  


