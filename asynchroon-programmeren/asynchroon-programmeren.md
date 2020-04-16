# asynchroon programmeren

```javascript
//dit is pseudocode (geen echte code)
let data = fetch('http://webdev.com/api/getData');
res.render('/data',{mijnData:data}); //data nog niet klaar
```

In voorbeeld 1 wordt een [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) genomen van een bepaalde API en de verkregen data zal dan gerenderd worden.  
Fetch moet echter wachten tot de data binnen is, want er wordt eerst geconnecteerd met de webserver \(call\), data wordt opgevraagd, **fetch wacht op het resultaat van de API** en pas als de data binnenkomt, kan deze verwerkt worden.  
Ondertussen **blokkeert JavaScript de uitvoering van de code niet** en worden de resultaten - die nog niet binnengekomen zijn, waardoor `let data` leeg is - gerendeerd \(res.render\). De uitkomst van mijnData zal **undefined** geven `mijnData === undefined`, want de uitvoering van het stuk code gebeurt voor de voltooing van fetch. JavaScript blokkeert de code dus niet. Dit blijkt hier een probleem, wanneer het renderen is afhankelijk van de resultaten van een eerder proces.  

