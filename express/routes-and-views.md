# 2. routes & views

## routes

### requests ontvangen

Express staat als server klaar om te luisteren naar vragen of _requests_ van buitenaf. Wel moet er nog een aanreikpunt of endpoint meegegeven worden, vergelijkbaar met paden of webadressen waar een verzoeken naartoe gestuurd kan worden. Het rootpad '/' is standaard, waardoor een request zal gestuurd worden naar het rootdomein, wat tevens endpoint zal zijn.

```javascript
// '/' = waar
// request is bijvoorbeeld url Google
// response is output naar de browser
app.get('/', (req, res) => {…});
```

Er wordt een route opgesteld die de aanvraag of _request_ opvangt en verder afhandelt. Deze aanvragen kunnen bestaan uit volgende http-request methodes: `get,` `post`, `put`, `use`, `delete`,...

```javascript
// volgorde is zeer belangrijk!
app.get('/', (req, res) => {
    res.type('text/html');
    res.send('AP-Hogeschool');
    }
);

app.get('/about', (req, res) => {
    res.type('text/html');
    res.send('Over AP-Hogeschool');
    }
);

app.use((req, res) => {
    res.type('text/html');
    res.status(404);
    res.send('404 - Not Found’);
    }
);

// de contact-pagina gaat niet gevonden worden omwille van de volgorde
app.get('/contact', (req, res) => {
    res.type('text/html');
    res.send('Contacteer AP-Hogeschool');
    }
);
```

##  views

### model-view-controller \(MVC\)

![bron: firebirdsql.org](../.gitbook/assets/image%20%284%29.png)

Het concept dat aan het Model-View-Controller-patroon ten grondslag ligt -voor het maken van websites en webapplicaties-, splitst een applicatie op in drie delen:

* **controller**: Controllers werken met het model en zorgen voor interactie met de gebruiker. Ze bieden ook _view_-opties aan voor het weergeven van de gebruikersinterface \(UI\). In een MVC-toepassing geeft _view_  enkel data weer, terwijl de controller de invoer verwerkt en reageert op activiteiten van de gebruiker. vb.: De controller kan waarden van een string in een query verwerken en naar het model verzenden, die deze waarden op zijn beurt in een ​​query naar de database kan verzenden.
* **view**: Dit is het visuele gedeelte van de gebruikersinterface van de applicatie. De gebruikersinterface wordt meestal gemaakt om de data binnen het model weer te geven.
* **model**: Modelobjecten zijn de delen van de applicatie die de logica voor het werken met data implementeren. Modelobjecten ontvangen doorgaans de status van het model en slaan deze op in de database.

### EJS-package

[EJS](https://ejs.co/) of **Embedded Javascript templating** is een eenvoudig template framework waarmee de HTML-opmaak genereert kan worden met gewone JavaScript.

```bash
# installeer de module ejs uit npm
npm install --save ejs
```

```javascript
const app = express();

// set up handlebars view engine
const ejs= require('ejs');
app.set('view engine', 'ejs');
```

Bovenstaande code creëert een view engine en configureert Express om deze standaard te gebruiken. 

### EJS-views

Maak nu een submap met de naam views met daarin de naam van de lay-out-pagina's \(ook wel hoofdpagina's genoemd\). Bij het bouwen van een website is er een bepaalde hoeveelheid HTML die op elke pagina hetzelfde is \(of bijna hetzelfde is\).  Door het gebruiken van views moet code voor soortgelijke pagina's niet herschreven worden en wordt een gemeenschappelijk kader gecreëerd voor de pagina's op een website.

* /views/index.ejs 
* /views/about.ejs 
* /views/contact.ejs

```javascript
app.get('/', (req, res) => 	
	{res.render('index', )});
app.get('/about', (req, res) => 	
	{res.render('about', )});
app.get('/contact',(req, res) => 
	{res.render('contact', )});
```

### statische content

Er kunnen een of meerdere mappen aangewezen worden die statische content bevatten en eenvoudig aangeleverd kunnen worden zonder speciale afhandeling, zoals mappen met afbeeldingen, CSS-bestanden en client-side JavaScript-bestanden. Maak hiervoor in uw projectmap een submap genaamd public \(_public_ omdat alles in deze map zonder speciale afhandeling wordt aangeboden\).   
vb.: statische bestanden als CSS, images,...

```javascript
app.use(express.static(__dirname + '/public'));
```

### dynamische content

De echte kracht van views is dat ze dynamische informatie kunnen bevatten, bijvoorbeeld via `<%= naam_variabel %>`

```javascript
app.get('/contact',(req, res) => 
	{res.render('contact', {naam_variable:  'waarde'})
	}
);
```

