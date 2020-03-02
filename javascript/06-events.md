# 06. Events

Wanneer je op het internet rondsurft, registreert jouw browser verschillende soorten van activiteiten of _events_. JavaScript kan op deze events reageren door gebruik te maken van _event handlers_ en/of _listeners_.

Door te reageren op deze events kunnen we een website interactief maken.

## Event types

Er bestaan verschillende soorten van events. Elk van deze events kan gebruikt worden om functies in JavaScript mee uit te voeren.

Wanneer een event voorkomt, dan beschrijven we dit als _fired_ of _raised_. Wanneer een event een functie aanroept, dan beschrijven we dit als een _trigger_.

### User Interface events

Komen voor wanneer de gebruiker de browsers UI gebruikt om iets te veranderen.

| Event | Beschrijving |
| :--- | :--- |
| load | De webpagina is klaar met laden. |
| unload | Er wordt een andere pagina geladen. |
| error | De browser komt een JavaScript-fout tegen. |
| resize | Het browservenster verandert van grootte. |
| scroll | De gebruiker scrollt door de pagina. |

### Keyboard events

| Event | Beschrijving |
| :--- | :--- |
| keydown | De gebruiker drukt een toets in. |
| keyup | De gebruiker laat een toets los. |
| keypress | Een nieuw karakter wordt ingevoegd door de gebruiker. |

### Mouse events

| Event | Beschrijving |
| :--- | :--- |
| click | De gebruiker klikt op een element. |
| dblclick | De gebruiker dubbelklikt op een element. |
| mousedown | De gebruiker drukt een muisknop in. |
| mouseup | De gebruiker laat een muisknop los. |
| mousemove | De gebruiker verplaatst de muis. |
| mouseover | De gebruiker gaat met de muis over een element. |
| mouseout | De gebruiker verwijdert de muis van het element. |

Er zijn nog meer events die je zal tegenkomen, maar de bovenstaande lijst bevat al een belangrijke start.

## Event Binding

Een event aan een DOM-node koppelen noemen we _binding._ Er bestaan 3 grote groepen van manieren om events aan DOM-nodes te koppelen.

### HTML event handlers

{% hint style="danger" %}
Niet meer gebruiken in moderne code. Je zal het nog wel tegenkomen in oudere projecten.
{% endhint %}

In eerdere versies van HTML bestond er een groep attributen die we konden gebruiken om events mee te binden en JavaScript-functies te triggeren. Aangezien we werken in een scheiding tussen de pagina-opbouw en functionele code, is het ook beter om deze niet meer te gebruiken.

```markup
<input type="text" id="username" onblur="checkUsername()">
```

### DOM event handlers

{% hint style="warning" %}
Kan nog wel gebruikt worden, maar is minder interessant dan event listeners.
{% endhint %}

In de oorspronkelijke DOM-specificatie werden de event handlers al toegevoegd. Ze worden in alle belangrijke browsers ondersteund en geven de mogelijkheid om JavaScript en HTML van elkaar te scheiden.

Het belangrijkste nadeel van deze oorspronkelijke handlers is dat ze slechts 1 functie aan een event kunnen koppelen. Wanneer er meerdere scripts op dezelfde events zouden reageren, zal er maximaal 1 script uitgevoerd worden.

```javascript
function checkUsername() {
    // code to check username
}

let elUsername = document.getElementById('username');
elUsername.onblur = checkUsername;
```

### DOM level 2 event listeners

Event listeners werden in een update \(in 2000\) aan de DOM-specificatie toegevoegd. Ze hebben als grootste voordeel dat je meerdere functies kan koppelen aan eenzelfde event.

```javascript
function checkUsername() {
    // code to check username
}

let elUsername = document.getElementById('username');

elUsername.addEventListener('blur', checkUsername, false);
// 'blur' is één van de vele DOM events die wordt aangeroepen
```

meer info ivm onBlur event: [https://www.w3schools.com/jsref/event\_onblur.asp](https://www.w3schools.com/jsref/event_onblur.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_onblur\_addeventlistener](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_onblur_addeventlistener)

## Event Flow

Aangezien HTML-elementen in elkaar worden gestoken, zal je bij een event vaak ook hetzelfde event op het parent-element uitvoeren. Als je op een element klikt, klik je eigenlijk op elke parent van dat element, tot op het _document_ zelf.

Wanneer je events oproept, kan je dus op 2 manieren kijken naar de flow van deze events:

* Event Bubbling: Event start bij het meest specifieke element en flows terug naar buiten naar het document.
* Even Capturing: Event start bij het document en gaat naar binnen tot aan het meest specifieke element.

De flow van events is enkel belangrijk als er event handlers staan op boven- en/of onderliggende elementen. In het laatste voorbeeld zie je een derde argument meegegeven worden met de event listener. Dit argument staat op _false_. Dit betekent dat we _event bubbling_ toepassen.

## Event Object

Wanneer een event voorkomt, krijgt dit event een eigen object dat informatie over het event bevat. Het event object wordt vaak met de letter 'e' benoemd.

```javascript
function checkUsername(e) {
    // code to check username
    let target = e.target; // get target of event
}

let elUsername = document.getElementById('username');
elUsername.addEventListener('blur', checkUsername, false);
```

## Extra info voor labo

### addEventListener\(\)

**addEventListener \(\)** voegt een gebeurtenis toe aan het opgegeven element.  
Gebruik de methode **removeEventListener \(\)** om een ​​gebeurtenis te verwijderen die is gekoppeld is met de methode addEventListener \(\). Gebruik de methode **document.addEventListener \(\)** om een ​​gebeurtenis aan het opgegeven element te koppelen.

meer info: [https://www.w3schools.com/jsref/met\_element\_addeventlistener.asp](https://www.w3schools.com/jsref/met_element_addeventlistener.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_element\_addeventlistener](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_element_addeventlistener)

### preventDefault\(\)

**preventDefault\(\)** methode stopt de standaardactie van een element.  
voorbeeld 1: Het voorkomt dat een verzendknop een formulier verzendt.   
voorbeeld 2: Het voorkomt dat een link de URL volgt.

meer info: [https://www.w3schools.com/jsref/event\_defaultprevented.asp](https://www.w3schools.com/jsref/event_defaultprevented.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_event\_defaultprevented](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_event_defaultprevented)



