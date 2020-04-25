# labo 10: mongodb

### 1. Maak het project aan

Open Visual Studio Code en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm-package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn. Installeer vervolgens de nodige npm libraries voor dit project:

```text
npm install --save mongodb node-fetch express
```

### 2. Maak het oefeningen bestand en test het

Maak een bestand `index.js`met de volgende inhoud. Let goed op de naam

```javascript
const {MongoClient} = require('mongodb');
const fetch = require('node-fetch');
const express = require('express');
const app = express();

const loadAllPokemonIntoDatabase = async(client) => {
    
}

const getAllPokemon = async(client) => {
    return [];
}

const getPokemonById = async(client, id) => {
    return undefined;
}

const getPokemonWithMinimumWeight = async(client, weight) => {
    return [];
}

const getPokemonWithMaximumHeight = async(client, height) => {
    return [];
}

(async () => {
    let client = undefined;

    await loadAllPokemonIntoDatabase(client);
    app.get('/pokemon', async(req,res) => {
        if (req.query.weight) {
            let pokemon = await getPokemonWithMinimumWeight(client, Number.parseInt(req.query.weight));
            res.send(pokemon);
        } else if (req.query.height) {
            let pokemon = await getPokemonWithMaximumHeight(client, Number.parseInt(req.query.height));
            res.send(pokemon);
        } else {
            let pokemon = await getAllPokemon(client);
            res.send(pokemon);
        }
    });

    app.get('/pokemon/:id', async(req,res) => {
        let pokemon = await getPokemonById(client, Number.parseInt(req.params.id));
        if (pokemon) {
            res.send(pokemon);
        } else {
            res.status(404);
            res.send({message: 'pokemon not found.'});
        }
    });

    app.listen(3000, () => {
        console.log('Server started on port 3000');
    });

    process.on('SIGINT', async() => {
        try {
            await client.close();
        } catch (e) {
        }
        process.exit();
    });
})();
```

Vooraleer aan het labo te beginnen. Kijk na of het programma kan opgestart worden door 

```text
node index.js
```

uit te voeren. Als je naar de url `http://localhost:3000/pokemon/1` gaat via je browser \(of via postman\) zou je de volgende response moeten krijgen:

```text
{"message":"pokemon not found."}
```

### 3. Maak een MongoDB Atlas account aan

Ga naar [https://cloud.mongodb.com/](https://cloud.mongodb.com/) en maak een account aan. Na het maken van een account log in via je nieuwe account. Maak vervolgens een nieuwe **Shared Cluster** \(is volledig gratis\) aan**.**  Kies als regio: **eu-west-1** in ireland of **eu-central-1** in frankfurt en geef je cluster een naam. Klik vervolgens op **Create Cluster**

**Het aanmaken van je cluster kan tot 5 minuten duren! Hou hier rekening mee**

### 4. Stel je security settings in

Ga terug naar het overzicht van de clusters en klik op **connect** en bij **Whitelist a connection IP address** kies je Add different ip address. Geef daar `0.0.0.0` in. 

Vervolgens maak je een nieuwe mongodb gebruiker aan in **Create a MongoDB User.** Zorg ervoor dat het paswoord kan gedeeld worden met ons zodat we ook toegang tot de database hebben. 

Ga dan verder door op **Choose a connection method** te klikken en klik op Connect your application en kies dan Node.js met versie 3.0 or later

Kopieer de **connection string** en hou deze zeker bij.   
\(**tip**: plaats deze in een constante variabele in je index.js bestand, je gaat deze nog nodig hebben\)

### **5**. Maak een nieuwe collection aan

Klik op Collections en vervolgens op Add my own data. Maak een nieuwe database aan met de naam **WebOntwikkeling** en als Collection Name: **Pokemon**

Als je al een database in je account hebt kan je gewoon ook op 'Add Database' drukken.

### 6. 

