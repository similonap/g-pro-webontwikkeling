# Opgave avondonderwijs

## Overzicht



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
npm install --save mongodb node-fetch express ejs
```

### 2. Maak het bestand aan

Maak een bestand `index.js`met de volgende inhoud:

```javascript
const {MongoClient} = require('mongodb');
const fetch = require('node-fetch');
const express = require('express');
const app = express();
const ejs = require('ejs');

app.set('view engine', 'ejs');
app.use(express.static(__dirname + '/public'));

const CONNECTION_URI = 'mongodb+srv://student:studentwebdev@cluster0-ljvvp.mongodb.net/test?retryWrites=true&w=majority';
const DATABASE = 'sample_mflix';
const MOVIE_COLLECTION= 'movies';


const loadAllPokemonData = async() => {
    // zie opgave
}

const getMyPokemon = (allPokemon) =>{
    // zie opgave
}

const getMyPokemonSummary = (allPokemon) => {
   // zie opgave
}


const loadDBData = async(client) => {
  // zie opgave
}



(async () => {
    let client = new MongoClient(CONNECTION_URI, { useUnifiedTopology: true });;
    await client.connect();

    const allPokemon = await loadAllPokemonData();
    
    // maak route voor "mypokemon"
    
    // maak route voor "mypokemonsummary"
    
    // maak route voor "moviedata"
   


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

### 3. Laad Pokemon in via API

Vul de `loadAllPokemonData` functie in. Deze functie moet de eerste 20 pokemon inladen via de pokeapi. Gebruik hiervoor de node-fetch library. Je kan de pokemon inladen via   
[`https://pokeapi.co/api/v2/pokemon/`](https://pokeapi.co/api/v2/pokemon/)`<nummer van de pokemon>`. De functie maakt een array van deze Pokemon en geeft ze terug als return value

### 4. De getMyPokemon functie

Vul de `getMyPokemon` functie in:

* `getMyPokemon` filtert de **20 Pokemon**: enkel Pokemon die **groter zijn dan 10**
* `getMyPokemon` geeft een array terug, maar niet in het originele JSON formaat van de API. Elk element in de array mag maar 2 velden hebben
  * het veld `name`, die de naam van de pokemon bevat
  * het veld `sprite`, die de sprite \(afbeelding\) van de pokemon bevat 
* Tip: gebruik filter en map

### 5. De myPokemon route

De `myPokemon` route gebruikt de data `getMyPokemon`. Zorg dat de route mooi de naam en de afbeelding van elke Pokemon toont

Tip: gebruik EJS. Er zijn 7 Pokemon.

### 6. De getMyPokemonSummary functie

Vul de `getMyPokemonSummary` functie in:

* de functie geeft een object terug in de vorm van: `{totalWeight:0, totalHeight:0, avgWeight:0, avgHeight:0}`
* de functie berekent dus het **totale gewicht**, **totale grootte**, **gemiddeld gewicht** en **gemiddelde grootte** van de **20** Pokemon **die groter zijn dan 10**
* Tip: gebruik filter en reduce.

### 7. De myPokemonSummary route

De `myPokemonSummary`  route gebruikt de data `getMyPokemonSummary`. Zorg dat de route een overzicht geeft van de summary, bv.:

### _Pokemon Summary_

_The total height of my Pokemon is 101   
The total weight of my Pokemon is 3965   
The average height of my Pokemon is 14.428571428571429   
The average weight of my Pokemon is 566.4285714285714_

### 8. De loadDBData functie

Vul de `loadDBData` functie in.

* de connectie string naar de database is al ingevuld. Dit geeft je read-access tot een movie database. De connectie wordt al gemaakt. Je moet gebruik maken van de database variable `DATABASE` en collection `MOVIE_COLLECTION`.
* deze functie heeft als return waarde alle films waarvan de **IMDB rating groter is dan 9.3**

### 9. De moviedata route

Deze route gebruikt de data van de `loadDBData` functie. Zorg dat deze route het JSON resultaat teruggeeft van deze functie.

