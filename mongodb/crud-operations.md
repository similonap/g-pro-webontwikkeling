---
description: 'Create, Read, Update, Delete aka playing with data'
---

# CRUD-operations

## database en collection

* `client.db(<naam van database>)`
* `client.db(...).collection(<naam van collection>)`
* collection maakt nieuwe collectie aan, indien deze nog niet bestaat \(hoofdlettergevoelig! \)

```javascript
await client.db('Les').collection('pokemon')...
```

## create

### **insertOne\(\): aanmaken 1 document**

`insertOne(...)`

```javascript
const pikachu = {name:'pikachu'};
// aanmaken 1 document: insertOne(...)
const result = await client.db('Les').collection('pokemon').insertOne(pikachu);
console.log(`New listing created with the following id: ${result.insertedId}`);
```

* MongoDB maakt zelf een \_id aan
* het formaat van het document staat niet vast \(niet zoals record in RDB\)
* nieuw \_id bij elke insert = verschillende keren JSON-object invoegen ****

### **insertMany: aanmaken meerdere documenten**

`insertMany(...)`

```javascript
const pokemon = [
            {name: 'pichu', age:7},
            {name: 'flareon',age:3},
            {
                name: 'eevee',
                owner: 'sven',
                age: 5
            }
        ];
// aanmaken meerdere documenten: insertMany(...)
result = await client.db('Les').collection('pokemon').insertMany(pokemon);
console.log(`${result.insertedCount} new listing(s) created with the following id(s):`);
console.log(result.insertedIds);
```

## read

### **findOne\(\): lezen 1 document**

* `findOne()` geeft eerste document van query terug
* parameter {} \(leeg object\) geeft alle resultaten terug \(~= select zonder where\)

```javascript
// lezen 1 document: findOne()
result = await client.db('Les').collection('pokemon').findOne({});
console.log(result);
```

* `findOne({name:'eevee'})` geeft eerste document van query terug waar name === 'eevee'
* parameter {name:'eevee'} \(object\) ~= select where name = 'eevee'

```javascript
result = await client.db('Les').collection('pokemon').findOne({name:'eevee'});
console.log(result);
```

\*\*\*\*

### **find\(\): lezen meerdere document**

* `find()` geeft alle documenten van query terug
* geeft cursor terug \(laat toe over resultaten te itereren\)
* gebruik toArray\(\) \(geeft promise terug\) om naar array om te zetten

```javascript
// lezen meerdere document: find()
cursor =  client.db('Les').collection('pokemon').find({});
result = await cursor.toArray();
console.log(result);
```

## **query operators**

### filteren resultaten

Door gebruik te maken van query operators kan er specifiek gezocht worden en kunnen zo resultaten gefilterd worden \(geavanceerde queries\).  In onderstaand voorbeeld is de parameter een JSON-object, namelijk `{age:{$gt:3}}`. Het gefilterde resultaat zal de leeftijd hoger dan 3 weergeven \(age &gt; 3\).

```javascript
cursor =  client
          .db('Les')
          .collection('pokemon')
          .find({age:{$gt:3}});
```

`.find({age:{$gt:3,$lt:7}});`

* age &gt; 3 \(gt\) 
* age &lt; 7 \(lt\)

```javascript
cursor =  client
          .db('Les')
          .collection('pokemon')
          .find({age:{$gt:3,$lt:7}});
```

meer info: [query operators](https://docs.mongodb.com/manual/reference/operator/query/)



### AND queries \| combineren filters

`$and`voert een logische `AND`bewerking uit op een reeks van _één of meer_ uitdrukkingen \(bijv `<expression1>`, `<expression2>`etc.\) en selecteert de documenten die voldoen aan _alle_ expressions in de array. De `$and`operator maakt gebruik van _short-circuit evaluatie_ . Als de eerste expressie \(bijvoorbeeld `<expression1>`\) een `false` teruggeeft, zal MongoDB de resterende expressies niet verder evalueren.  
  
`.find({age:{$gt:3,$lt:7}, name:'pikachu'});`

* `{age:{$gt:3,$lt:7}, name:'pikachu'}` 
* `age:{$gt:3,$lt:7}` EN `name:'pikachu'` 
* `age:{$gt:3}` EN `age:{$lt:7}` EN `name:'pikachu'` 
* age &gt; 3 EN age &lt; 7 EN name == 'pikachu'

```javascript
cursor =  client.db('Les')
          .collection('pokemon')
          .find({age:{$gt:3,$lt:7}, name:'pikachu'});
```

meer info: [and \| logical query operators](https://docs.mongodb.com/manual/reference/operator/query/and/#op._S_and)



### OR queries \| combineren filters

De `$or`operator voert een logische `OR`bewerking uit op een array van _twee of meer_ `<expressions>` en selecteert de documenten die voldoen aan _ten minste_ één van de `<expressions>`.   
  
`.find($or[{age:{$gt:3}}, {name:'pikachu'});` 

* `{age:{$gt:3}}` OR `{name:'pikachu'}` 
* age &gt; 3 OR name == 'pikachu'

```javascript
cursor =  client.db('Les')
          .collection('pokemon')
          .find({$or:[{age:{$gt:3,$lt:7}}, {name:'pikachu'}]});
```

meer info: [or \| logical query operators](https://docs.mongodb.com/manual/reference/operator/query/or/)



### IN queries \| combineren filters

De `$in`operator selecteert de documenten waarbij de waarde van een veld gelijk is aan elke waarde in de opgegeven array.  
  
`.find({name:{$in:['pikachu', 'eevee']}})`

```javascript
cursor =  client.db('Les')
          .collection('pokemon')
          .find({name:{$in:['pikachu', 'eevee']}});
```

meer info: [in \| comparison query operator](https://docs.mongodb.com/manual/reference/operator/query/in/#op._S_in)

## update

### updateOne\(\)

Een enkel document kan bijgewerkt worden door gebruik te maken van `updateOne ()`. `updateOne ()` heeft twee vereiste parameters en een optionele: 

* **filter \(object\)** wordt gebruikt om het document te selecteren dat geüpdate moet worden. De filter is vergelijkbaar met de query die in `findOne()` gebruikt wordt om naar een bepaald document te zoeken. Om te zoeken naar alle documenten is het nodig om binnen de filter geen eigenschappen mee te geven. Eén of meerdere eigenschappen opnemen binnen de filter verfijnt de zoekopdracht.  
* **update \(object\)** wordt gebruikt om het document te updaten.  MongoDB heeft verschillende update-operators, zoals `$inc`, `$currentDate`, `$set` en `$unset`.  Een [volledige lijst van update-operators](https://docs.mongodb.com/manual/reference/operator/update/) en hun beschrijvingen staat te lezen op de officiële documentatie van MongoDB.
* **options \(object\)** is een _optionele_ parameter voor opties. Meer info over deze opties is te vinden op de [updateOne\(\)-documenten](https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#updateOne) online.

`updateOne()` zal het eerste document bijwerken dat overeenkomt met de gegeven zoekopdracht. Indien er meer dan één document overeenkomt met de zoekopdracht, wordt slechts één document bijgewerkt.

### updateMany\(\)

Soms is het handig om ineens meer dan één document tegelijk bij te werken en dat kan met `updateMany()`. Net zoals bij `updateOne()` vereist `updateMany()` dat een filter \(object\) en een update \(object\) wordt doorgegeven. Ook opties van het type object kunnen opgenomen worden te nemen.

## delete

### deleteOne\(\)

`deleteOne()` kan één enkel document verwijderen en heeft één vereiste parameter, namelijk filter\(object\). De filter wordt gebruikt om het te verwijderen document te selecteren, en is vergelijkbaar met de query die in `findOne()` en in `updateOne()` gebruikt worden om naar een bepaald document te zoeken. 

* **filter \(object\)** wordt gebruikt om het document te selecteren dat gedelete moet worden. De filter is vergelijkbaar met de query din `findOne()` en `updateOne()`. Om te zoeken naar alle documenten is het nodig om binnen de filter geen eigenschappen mee te geven. Eén of meerdere eigenschappen opnemen binnen de filter verfijnt de zoekopdracht. 
* **options \(object\)** is een _optionele_ parameter voor opties. Meer info over deze opties is te vinden op de [deleteOne\(\)-documenten](https://mongodb.github.io/node-mongodb-native/3.3/api/Collection.html#deleteOne) online.

`deleteOne()` verwijdert het eerste document dat overeenkomt met de opgegeven zoekopdracht. Zelfs als meer dan één document overeenkomt met de zoekopdracht, wordt er slechts één document verwijderd. Als er geen filter opgegeven wordt, zal het eerste document in natuurlijke volgorde verwijderd worden.

### deleteMany\(\)

Om meer dan één document tegelijkertijd te verwijderen is er `deleteMany()`. Net als bij `deleteOne()` vereist `deleteMany()` dat een filter \(object\) wordt doorgegeven. Ook opties van het type object kunnen opgenomen worden te nemen.

```javascript
let result = await client.db('Les').collection('pokemon').deleteMany({});
```

**let op**: Dit maakt je DB helemaal leeg.

