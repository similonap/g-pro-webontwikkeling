# Oefeningen

### Opdracht 1: Opfrissing van JavaScript

Start de Node.js CLI \(via node ****zonder argumenten\) op. Probeer hier een aantal JavaScript statements uit:

* Maak een variabele a, b, c aan en initialiseer deze met een waarde \(gebruik let, niet var!\) en tel deze bij elkaar op.
* Maak een array myArray\[\] en voeg daar een aantal getallen aan toe. Tel alle getallen van deze array bij elkaar op.
  * Je kan hiervoor een gewone for lus gebruiken maar ook het forEach\(\) statement.
* Verlaat de REPL tool en doe het bovenstaande in een eigen index.js bestand in visual studio code. Als je hier output wil hebben zal je moeten gebruik maken van console.log statements.
* Gebruik de debugger van visual studio code en zet een breakpoint ergens in de for lus en stap daarna doorheen de code. 

### **Opdracht 2: JSON Modelleren**

Maak een JSON bestand waarin je een winkel mandje modeleerd:

* Het bevat een array van producten
* Een product bevat de volgende eigenschappen
  * naam
  * beschrijving
  * prijs
  * hoeveelheid in stock

**Er moeten minimum 3 producten in het winkelmandje liggen en 1 van de producten heeft geen beschrijving.**

* Installeer jsonlint en kijk na of jouw json file voldoet aan de specificaties:

```text
npm install -g jsonlint
jsonlint shopping.json
```

### Opdracht 3: Eenvoudige webserver met JSON

Je kan in Node.js heel eenvoudig een webserver maken. 

```text
const http = require('http');
const server = http.createServer((request, response) => {
    response.writeHead(200, {'Content-Type':'text/plain'});
    response.write('Hello World');
    response.end();
});

server.listen(3000);
```

* Pas deze webserver aan zodat deze JSON kan terug geven. Je kan een lijst van Content-Type's [hier](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types) vinden.
* Pas deze webserver aan zodat het op een andere poort runt \(1337?\)
* Retourneer een JSON object dat je voornaam en achternaam bevat als je naar http://localhost:1337 surft. Hou er rekening mee dat de write functie alleen strings aanvaard dus je zal je object nog moeten omzetten.
* Ga op zoek naar headers in het request object naar informatie over je browser en je operating system. Geef dit ook mee terug in het JSON object. _\(Je kan ofwel via de debugger het request object inspecteren of gewoon het object afprinten via console.log\)_
* Hou een teller bij hoeveel keer de pagina is geladen en geef ook dit mee in de response van je http server.

Interessante functies die eventueel nodig gaan zijn voor dit labo: [JSON.stringify\(\)](https://www.w3schools.com/js/js_json_stringify.asp) en [JSON.parse\(\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)



