# 4. API's

## Wat is een API?

Een **Application Programming Interface** \(API\) is een verzameling definities en vormt de basis waarmee een computerprogramma kan communiceren met een ander programma of een onderdeel, zoals een bibliotheek. API's bestaan voor \(web\)applicaties, softwarebibiliotheken en besturingssystemen en kunnen voor allerlei doeleinden worden ingezet. Enkele voorbeelden:

* API binnen besturingssysteem om softwareprogramma's te laten printen. Een tekenprogramma hoeft dus niet te weten hoe het een printer moet aansturen, maar roept hiervoor een gespecialiseerd stuk software aan in een bibliotheek, via een afdruk-API.
* API binnen internetapplicatie om teksten, foto's en video te versturen of te downloaden 

### RESTful API

Een RESTful API \(**RE**presentational **S**tate **T**ransfer\) is een API dat HTTP-requests gebruikt om data te verzenden en aan te passen via `get`, `put`, `post` and `delete`.  
De REST-architectuur maakt dus gebruik van vier veelgebruikte HTTP-methoden:

* **get:** Deze methode helpt bij het aanbieden van gegevens met 'read-only access'.
* **put:** Deze methode wordt geïmplementeerd voor het bijwerken van een bestaande gegevens of het maken van nieuwe.
* **post:** Deze methode wordt geïmplementeerd voor het maken van nieuwe gegevens. 
* **delete:** Deze methode wordt geïmplementeerd voor het verwijderen van gegevens. 

meer info: [https://www.w3schools.in/restful-web-services/intro/](https://www.w3schools.in/restful-web-services/intro/)

### Express API

#### een voorbeeld

```javascript
const gegevens = 
	{
		telefoonnummer:'0123456789',
		email:'contact@ap.be'
	};
app.get('/api/contactgegevens',(req, res) => 
	{
		res.type('application/json');
		res.json(gegevens);
	}
);
```

## public API's

De website [pokeapi](https://pokeapi.co/) geeft meer info over RESTful API gelinkt aan een zeer uitgebreide database met alle details over de Pokémon games.

```bash
npm install request
```

```javascript
const pokemon= req.query.pokemon; 
request('https://pokeapi.co/api/v2/pokemon/' + pokemon, 
(error, response, body) => {
     if (!error && response.statusCode == 200) {
          res.type('application/json');
          res.json(body);
     }        
});
```

