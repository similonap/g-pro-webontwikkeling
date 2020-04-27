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



### updateMany\(\)



## delete

### deleteOne\(\)



### deleteMany\(\)

