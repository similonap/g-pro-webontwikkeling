# 02.JSON

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

JSON kan **nooit** de waarde krijgen van de volgende data types:

* function
* date
* _undefined_

JSON kan wel gebruikt worden voor de onderstaande data types:

* string moet altijd tussen dubbele aanhalingstekens

```javascript
{ "name":"John" }
```

