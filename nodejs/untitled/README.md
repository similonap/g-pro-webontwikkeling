# 01. NodeJS intro

## Wat is NodeJS?

JavaScript is overal, denk maar aan JS-bibliotheken en -frameworks in de browser. Bekend zijn onder meer [jQuery](https://jquery.com/), [AngularJS](https://angularjs.org/) en [React](https://reactjs.org/). JavaScript wordt tegenwoordig ook gebruikt in server-sided projecten en hiervoor wordt Node.js ingezet. 

[**Node.js**](https://nodejs.org/en/) is een van de populairste projecten op [Github](https://github.com/) en dus open source.  Het is een softwareplatform met een **asynchroon event-driven JS**-runtime architectuur -JavaScript oorspronkelijk ontwikkeld voor de client- aan de serverkant kan gebruiken, die grote hoeveelheden gegevens in realtime moeten verwerken, en buiten een browser om uitgevoerd kan worden. Node.JS is populair voor de realisatie van lichtgewicht webservers. Node.JS wordt dus gebruikt om code te schrijven voor de server, zoals de talen PHP, Java, .NET, Ruby of Python. 

* **event-driven**: werkt enkel bij versturen “event”, anders slaapmodus
* **asynchroon**: code kan parallel uitgevoerd worden en hoeft niet te wachten
* **JavaScript**: alles wordt geschreven in JavaScript = full JS stack \(= frontend + backend\)

Dankzij Node.js kunnen ontwikkelaars JavaScript gebruiken voor command-line-tools en server-side scripting. Node.JS is populair voor de realisatie van lichtgewicht webservers.  
  
Node.js bevat een bibliotheek van diverse JavaScript-modules, die met een eenvoudige functie kunnen worden geladen en beschikbaar zijn als kant-en-klare bouwstenen voor het ontwikkelen van webtoepassingen. Op Github staan tevens duizenden modules voor de Node Package Manager \(NPM\). Node.js wordt gebruikt bij het ontwikkelen van tools als PhoneGap, Grunt, Gulp, Bower e.a. 

## voorbeelden

Een voorbeeld hiervan is de HTTP-module, waarmee je met één enkele functie een rudimentaire webserver kunt maken. Bovendien kun je met de geïntegreerde pakketmanager npm \(Node Package Manager\) extra modules installeren.

```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end('Hello World');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

## installatie

### 1. software downloaden

{% embed url="https://nodejs.org/en/" %}

Terwijl de huidige versie van Node.js je de nieuwste functies van de runtime-omgeving biedt, biedt de LTS-release een stabiele softwareversie voor duurzaam gebruik.

### **2. Node.js en npm installeren**

Ga stap voor stap doorheen de installatie-wizard. Installeer naast Node.js ook de npm package manager.

### 3. testen installatie

Start Node.js op en voer een eerste eenvoudige JavaScript-code uit. De runtime-omgeving biedt daarvoor **twee modi**: Node.js in de interactieve modus of de applicatiecode uitvoeren van een eerder aangemaakt JavaScript \(.js\)-bestand. 

* Kies voor de interactieve modus en test deze in de terminal \(mac\) \| opdrachtprompt \(Windows\).
* Start de JavaScript runtime-omgeving via het commando node.





## terminal



## editor



## eerst script



## situering NodeJS

### 

## voorbeelden

### Hello world

### 

