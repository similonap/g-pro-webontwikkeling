---
description: 'create, read, update, delete'
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

### **insert\(\): aanmaken 1 document**

`insert(...)`

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

* `find()`'s cursor kan bewerkt worden:
* `.limit(3)` limiteert tot 3 resultaten
* `.sort({age:-1})` sorteert op naam

```javascript
cursor =  client.db('Les').collection('pokemon').find({}).sort({age:-1}).limit(3);
```

* resultaten filteren \(geavanceerde queries\)
* age &gt; 3

```javascript
cursor =  client.db('Les').collection('pokemon').find({age:{$gt:3}});
```

* age &gt; 3 && age &lt; 7

```javascript
cursor =  client.db('Les').collection('pokemon').find({age:{$gt:3,$lt:7}});
```

**meer info**: [https://docs.mongodb.com/manual/reference/operator/query/](https://docs.mongodb.com/manual/reference/operator/query/)

* combineren van filters
* age &gt; 3 && age &lt; 7 && name == 'pikachu

```javascript
cursor =  client.db('Les').collection('pokemon').find({age:{$gt:3,$lt:7}, name:'pikachu'});
```

* Logical operators

**meer info**: [https://docs.mongodb.com/manual/reference/operator/query-logical/](https://docs.mongodb.com/manual/reference/operator/query-logical/)

* bv. OF: $or
* $or: \[&lt;expressions&gt;\]

```javascript
cursor =  client.db('Les').collection('pokemon').find({$or:[{age:{$gt:3,$lt:7}}, {name:'pikachu'}]});
```

* **let op**: maakt je DB helemaal leeg

```javascript
let result = await client.db('Les').collection('pokemon').deleteMany({});
```

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

