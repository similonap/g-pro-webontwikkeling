# NoSQL vs relationele DB

## NoSQL database

**MongoDB** is een **NoSQL-database** \(Not Only SQL\), eentje die **SQL vermijdt**. Het SQL-systeem wordt ter ondersteuning gebruikt, maar niet actief bij het verwerken van verzoeken. Dit soort databases kan daarom ingezet worden bij grote hoeveelheden van gegevens.  
In een NoSQL-database wordt aan een rij slechts een enkele kolom gelinkt. Alle entry’s voor een rij worden gegroepeerd in dezelfde kolom, waardoor plaats bespaard wordt. Door het grote volume aan data zijn koppelingen als JOIN \(vrijwel\) onhaalbaar.  
**Data** wordt opgeslagen als **'documents' / JSON.** Het is **dynamische data** waarvan de **structuur aanpasbaar** is en bepaald wordt tijdens de ontwikkeling. NoSQL-databases kunnen gebruikt worden voor **simpele queries**.

```javascript
[
    {
        firstname: 'Sven',
        lastname: 'Charleer',
        email: 'sven.charleer@ap.be'
    },
    {
        firstname: 'Andie',
        lastname: 'Similon',
        email: 'andie.similon@ap.be'
    },
]
```

## relationele DB

Op het eerste gezicht lijkt een relationele database eerder een platte database. Het verschil zit in de tabellen die niet op zichzelf staan. **Data** zit verspreid over **meerdere tabellen** binnen een  database,  waarbij de tabellen aan elkaar gekoppeld kunnen worden met JOIN.   
Een relationele database is een prima oplossing voor **gestructureerde data**, waarbij de **structuur** nadien **moeilijk aanpasbaar** is en daarom op voorhand bepaald dient te worden. Vanwege de opbouw kunnen **ingewikkelde queries** op dit soort databanken losgelaten worden.  
vb. relationele database **MySQL**: Zo kan een bepaalde klas uit een tabel klassen, weer verwijzen naar een uurrooster, dan weer gekoppeld aan klaslokalen en een groep studenten.

| firstName | lastName | email |
| :--- | :--- | :--- |
| Sven | Charleer | sven.charleer@ap.be |
| Andie | Similon | andie.similon@ap.be  |

## NoSQL vs relationele DB

| relationele DB | NoSQL |
| :--- | :--- |
| record in RDB | MongoDB's document \(JSON-object\) |
| tabel in RDB | MongoDB's collection |
| \_id is unieke identifier \(indexed\)\) voor elk document | document wordt binair bijgehouden \(BSON\) |



## playing with data

Create, read, update, delete \(CRUD\)

### choosing your database and collection

* client.db\(&lt;naam van database&gt;\)
* client.db\(...\).collection\(&lt;naam van collection&gt;\)
* collection maakt nieuwe collectie aan indien die niet bestaat \(hoofdlettergevoelig! \)

```javascript
await client.db('Les').collection('pokemon')...
```

## create

**insert van 1 document** `insertOne(...)`

```javascript
const pikachu = {name:'pikachu'};
const result = await client.db('Les').collection('pokemon').insertOne(pikachu);
console.log(`New listing created with the following id: ${result.insertedId}`);
```

* MongoDB maakt zelf een \_id aan
* formaat document staat niet vast \(niet zoals record in RDB\)
* nieuw \_id bij elke insert = verschillende keren JSON-object invoegen

**insert van verschillende documenten** `insertMany(...)`

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
result = await client.db('Les').collection('pokemon').insertMany(pokemon);
console.log(`${result.insertedCount} new listing(s) created with the following id(s):`);
console.log(result.insertedIds);
```

## read

* `findOne()` geeft eerste document van query terug
* parameter {} \(leeg object\) geeft alle resultaten terug \(~= select zonder where\)

```javascript
result = await client.db('Les').collection('pokemon').findOne({});
console.log(result);
```

* `findOne({name:'eevee'})` geeft eerste document van query terug waar name === 'eevee'
* parameter {name:'eevee'} \(object\) ~= select where name = 'eevee'

```javascript
result = await client.db('Les').collection('pokemon').findOne({name:'eevee'});
console.log(result);
```

* `find()` geeft alle documenten van query terug
* geeft cursor terug \(laat toe over resultaten te itereren\)
* gebruik toArray\(\) \(geeft promise terug\) om naar array om te zetten

```javascript
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

## delete

* **let op**: maakt je DB helemaal leeg

```javascript
let result = await client.db('Les').collection('pokemon').deleteMany({});
```

## updateOne\(\)



## updateMany\(\)



## deleteOne\(\)



## deleteMany\(\)

