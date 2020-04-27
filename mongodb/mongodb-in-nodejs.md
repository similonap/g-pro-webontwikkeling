# MongoDB in NodeJS

## MongoDB in NodeJS

{% embed url="https://www.youtube.com/watch?v=ayNI9Q84v8g" %}

```javascript
npm install mongodb
```

### client initialiseren

De MongoDB-module exporteert `MongoClient`, en dat is wat gebruikt zal worden om een verbinding te maken met een MongoDB-database. 

```javascript
const {MongoClient} = require('mongodb');
```

Er moet een constante aangemaakt worden voor de verbindings-URI. Vergeet in de verbindingsreeks niet om `<username>`,`<password>`en `your-cluster-url` \(**lokale mongodb**\) bij te werken of bij een **externe mongodb** \(voor labo: [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)\)

```javascript
// connectie URI: update <username>, <password> en <your-cluster-url>
// meer info op https://docs.mongodb.com/ecosystem/drivers/node/
const uri = "mongodb+srv://<username>:<password>@<your-clusterurl>/test?retryWrites=true&w=majority";
```

Nu de constante URI werd gedeclareerd, kan een exemplaar van MongoClient gemaakt worden.

```javascript
//uri is link naar mongo-database
const client = new MongoClient(uri);
```

### connecting to MongoDB

* connect\(\)

```javascript
await client.connect();
```

* geeft promise terug
* dus te plaatsen in een async-functie met een try/catch

### listing databases

* van zodra connect\(\) klaar is

```javascript
let list = await client.db().admin().listDatabases();
```

* geeft promise terug
* lijst van databases

### closing connection

* close\(\)
* client.close\(\) in finally!

```javascript
try {
    // connect to the MongoDB cluster
    await client.connect();
    // make the appropriate DB calls
    ...
    } catch (e) {
        console.error(e);
    } finally {
        await client.close();
    }
```



## 

