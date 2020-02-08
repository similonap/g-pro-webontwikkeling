# routes & views

Express staat als server klaar om te luisteren naar vragen of _requests_ van buitenaf. Wel moet er nog een aanreikpunt of endpoint meegegeven worden, vergelijkbaar met paden of webadressen waar een verzoeken naartoe gestuurd kan worden. Het rootpad '/' is standaard, waardoor een request zal gestuurd worden naar het rootdomein, wat tevens endpoint zal zijn.

```javascript
// '/' = waar
// request is bijvoorbeeld url Google
// response is output naar de browser
app.get('/’, (request, response) => {…}
```

Er wordt een route opgesteld die de aanvraag of _request_ opvangt en verder afhandelt. Deze aanvragen kunnen bestaan uit volgende http-request methodes: `get,` `post`, `put`, `use`, `delete`,...

* `get`: Voor het verkrijgen van gegevens van een server. Het gaat dus om een verzoek om informatie. Gegevens op de server worden niet gewijzigd.
* `post`: Voor aanmaken van nieuwe gegevens op de server of wanneer een bepaalde actie moet ondernomen worden.
* `put`: Voor het aanpassen van gegevens op de server.
* `use`: Voor het gebruiken van gegevens op de server.
* `delete`: Voor het verwijderen van gegevens op de server.

```javascript
//voorbeeld van een HTTP get-request
app.get("/", (req, res) => {
    res.send("Bericht van de server");
});

//voorbeeld van een HTTP post-request
app.post("/niews", (req, res) => {
    // Voeg nieuws-items toe
});
```

```javascript
// volgorde is zeer belangrijk!
app.get('/’, (request, response) => {
    res.type('text/html');
    res.send('AP-Hogeschool');
    }
app.get(‘/about', (request, response) => {
    res.type('text/html');
    res.send('Over AP-Hogeschool');
}

app.use((req, res) => {
    res.type('text/html');
    res.status(404);
    res.send('404 - Not Found’);}
);

app.get(‘/contact', (request, response) => {
    res.type('text/html');
    res.send('Contacteer AP-Hogeschool');
    }
```

 

