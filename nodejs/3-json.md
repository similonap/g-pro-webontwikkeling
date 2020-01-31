---
description: data formaat
---

# 03. JSON

## Wat is JSON?

[JSON ](https://www.json.org/json-en.html)staat voor **J**ava**S**cript **O**bject **N**otation en is een gestandaardiseerd gegevensformaat. JSON maakt gebruik van voor de mens makkelijk **leesbare tekst** in de vorm van lichtgewicht formaat van data-objecten die bestaan uit een of meer attributen met bijbehorende waarden. Het wordt vooral gebruikt voor het uitwisselen van data tussen webserver en webapplicatie of client. JSON wordt opgeslagen in een database of een bestand.

```javascript
//JSON: string moet geschreven worden tussen dubbele aanhalingstekens
{ "name":"John" }

//JS: string kan geschreven worden tussen enkele of dubbele aanhalingstekens
{ name:'John' }
```

## voorbeeld

```javascript
{
  "name": "tracking",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "MIT",
  "dependencies": {
    "body-parser": "^1.18.2",
    "express": "^4.16.2",
    "http": "0.0.0",
    "https": "^1.0.0",
    "json-stringify": "^1.0.0",
    "net": "^1.0.2"
  }
}
```

voorbeeld van package.json

```javascript
{
    "firstName": "John",
    "lastName": "Smith",
    "isAlive": true,
    "age": 27,
    "address": {
    "streetAddress": "21 2nd Street",
        "city": "New York",
        "state": "NY",
        "postalCode": "10021-3100"
    },
    "phoneNumbers": [
        {
            "type": "home",
            "number": "212 555-1234"
        },
        {
            "type": "office",
            "number": "646 555-4567"
    ],
    "children": [],
    "spouse": null
}
```

## data types

JSON kan nooit _****_de waarde krijgen van de volgende data types: function, date of _undefined._  
JSON kan wel gebruikt worden voor de onderstaande data types:

* **string** moet altijd tussen dubbele aanhalingstekens

```javascript
{ "name":"John" }
```

* **number**

```javascript
{"age" : 32}
{"temperature" : -4}
```

* **boolean** met waarde true of false

```javascript
{"visible" : true}
```

* **null** kan een waarde zijn

```javascript
{"grade" : null}
```

* **array**

```javascript
{"cars" : ["Toyota","BMW","Audi"]}
```

* **object**

```javascript
{
"student" : {"name" : "John","leeftijd" : 32,"grade" : null}
}
```



