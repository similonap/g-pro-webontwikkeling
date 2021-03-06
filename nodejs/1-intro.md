# 1. intro NodeJS

## Wat is Node.js?

JavaScript is overal, denk maar aan JS-bibliotheken en -frameworks in de browser. Bekend zijn onder meer [jQuery](https://jquery.com/), [AngularJS](https://angularjs.org/) en [React](https://reactjs.org/). JavaScript wordt tegenwoordig ook gebruikt in server-sided projecten en hiervoor wordt Node.js ingezet. 

![](../.gitbook/assets/node.png)

[**Node.js**](https://nodejs.org/en/) is een asynchrone Javascript _runtime environment_ gebaseerd op de Google V8 engine en één van de populairste projecten op [Github](https://github.com/).  Een runtime environment zet een bepaalde taal, zoals Javascript, om in machinetaal die een computer kan uitvoeren. Node.js is een softwareplatform dat aan de serverkant gebruikt kan worden en die grote hoeveelheden gegevens in realtime moeten verwerken, en buiten een browser om uitgevoerd kan worden. Node.js is populair voor de realisatie van lichtgewicht webservers. Node.js wordt dus gebruikt om code te schrijven voor de server, zoals de talen PHP, Java, .NET, Ruby of Python. 

* **event-driven**: werkt enkel bij versturen “event”, anders slaapmodus
* **asynchroon**: code kan parallel uitgevoerd worden en hoeft niet te wachten
* **JavaScript**: alles wordt geschreven in JavaScript = full JS stack \(= frontend + backend\)

Dankzij Node.js kunnen ontwikkelaars JavaScript gebruiken voor command-line-tools en server-side scripting. Node.js is populair voor de realisatie van lichtgewicht webservers.  
  
Node.js bevat een bibliotheek van diverse JavaScript-modules, die met een eenvoudige functie kunnen worden geladen en beschikbaar zijn als kant-en-klare bouwstenen voor het ontwikkelen van webtoepassingen. Op Github staan tevens duizenden modules voor de [Node Package Manager \(npm\)](https://www.npmjs.com/). 

#### voorbeelden

Node.js wordt gebruikt bij het ontwikkelen van tools als [PhoneGap](https://phonegap.com/), [Grunt](https://gruntjs.com/), [Gulp](https://gulpjs.com/), [Bower ](https://bower.io/)e.a. 

## Node.js installeren

### 1. software downloaden

{% embed url="https://nodejs.org/en/" %}

Terwijl de huidige versie van Node.js je de nieuwste functies van de runtime-omgeving biedt, biedt de LTS-release een stabiele softwareversie voor duurzaam gebruik, dus best **LTS downloaden**.

### **2. Node.js en npm installeren**

Ga stap voor stap doorheen de installatie-wizard. Installeer naast Node.js ook de npm package manager.

### 3. testen installatie

Start Node.js op en voer een eerste eenvoudige JavaScript-code uit. De runtime-omgeving biedt daarvoor twee modi: Node.js in de interactieve modus of de applicatiecode uitvoeren van een eerder aangemaakt JavaScript \(.js\)-bestand. 

* Kies voor de interactieve modus en test deze in de terminal.
* Start de JavaScript runtime-omgeving via het commando node door 'node' te typen in de terminal \(kan eventueel in de terminal van Visual Studio code\).

```bash
node
```

```bash
console.log(“Hello World!”);
```

De uitvoer ‘Hello World!’ laat zien dat de installatie van Node.js is geslaagd.

### 4. nakijken versies

Open de terminal \(opdrachtprompt\) en type onderstaande code. Deze vraagt naar de versie van Node.js op jouw computer, mocht die er reeds opstaan.

voor de versie van Node.js

```bash
node version
```

voor de versie van npm

```bash
npm version
```

## eerste script

Een voorbeeld hiervan is de HTTP-module, waarmee je met één enkele functie een rudimentaire webserver kunt maken. Bovendien kun je met de geïntegreerde pakketmanager npm \(Node Package Manager\) extra modules installeren.

### Hello AP

```javascript
// http-module importeren
// require laadt de bibliotheek 'http' in
const http = require('http');

// het adres van de webserver localhost (= server draaiend op eigen computer)
// poort 9000 is een zelfgekozen nummer van een vrije poort
const hostname = '127.0.0.1';
const port = 9000;

// maakt een webserver door functie 'createServer' aan te roepen van de 'http'-bibliotheek. Neemt een handler methode aan met 2 parameters:
// het request en response object.
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end('Hello AP');
});

// laat de webserver luisteren op de aangegeven poort en adres.
server.listen(port, hostname, () => {
  console.log('Server running at http://' + hostname + ':' + port);
});
```

bron: [https://nodejs.org/en/about/](https://nodejs.org/en/about/)  
ter info: [lijst van statuscodes](https://nl.wikipedia.org/wiki/Lijst_van_HTTP-statuscodes)  
ter info: =&gt; is een verkorte notatie voor functie

## video \(achtergrondinfo\)

{% embed url="https://www.youtube.com/watch?v=TlB\_eWDSMt4" %}

{% embed url="https://youtu.be/gG3pytAY2MY" %}



