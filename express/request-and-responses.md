# request & responses

## URL

Een **U**niform **R**esource **L**ocator \(afgekort URL\) is een gestructureerde naam die verwijst naar een stuk data. Gekende voorbeelden zijn het unieke adres waarmee de locatie van een webpagina op internet wordt weergegeven, of een e-mailadres.

![](../.gitbook/assets/image%20%283%29.png)

![](../.gitbook/assets/image%20%284%29.png)

* **protocol**: Een protocol is een gedragsovereenkomst, meestal in de vorm van een aantal uit te voeren stappen. Het protocol wordt genoteerd in de vorm van een korte protocolaanduiding \(vaak een afkorting\) gevolgd door een dubbele punt.
* **authenticatie**: Authenticatiegegevens, zoals gebruikersnaam en wachtwoord om zo toegang te krijgen tot bijvoorbeeld een systeem of een service.
* **domeinnaam**
* **poortnummer**
* **padnaam**: De precieze betekenis hangt af van het protocol. Bij FTP verwijst het meestal naar een fysiek bestand, een map of een commando aan een zoekmachine of een database manager.
* **querystring**: Een querystring wordt meestal gebruikt om bepaalde parameters mee te geven aan de URL, zoals zoektermen van een zoekactie. De querystring volgt na het vraagteken, verschillende parameters in de string worden gescheiden met `&`.
* **fragment:** Dit wordt gebruikt om naar een specifiek onderdeel van de informatiebron te verwijzen. Bij HTML-pagina's wordt `#` bijvoorbeeld gebruikt voor tekstankers. 

## HTTP-request methodes

* `get`: Voor het verkrijgen van gegevens van een server. Het gaat dus om een verzoek om informatie. Gegevens op de server worden niet gewijzigd.
  * parameters in url 
  * vb.: [https://www.google.com/search?client=safari&q=ap+antwerpen](https://www.google.com/search?client=safari&q=ap+antwerpen) 
  * niet gebruiken bij gevoelige data 
  * limiet in data lengte
* `post`: Voor aanmaken van nieuwe gegevens op de server of wanneer een bepaalde actie moet ondernomen worden.
  * data in request body
  * geen limiet in data lengte
  * vb.: uploaden van bestanden, paswoorden,...
* `put`: Voor het aanpassen van gegevens op de server.
* `delete`: Voor het verwijderen van gegevens op de server.

ter info: [overzicht alle HTTP-request methodes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

```javascript
//voorbeeld van een HTTP get-request
app.get('/', (req, res) => {
    res.send("Bericht van de server");
});

//voorbeeld van een HTTP post-request
app.post('/nieuws', (req, res) => {
    // Voeg nieuws-items toe
});
```

