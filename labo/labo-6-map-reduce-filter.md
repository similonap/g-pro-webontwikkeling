# labo 6: map/reduce/filter

### 1. Maak het project aan

Open Visual Studio Code en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm-package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn.

### 2. Rest Operator

Maak een bestand `rest.js` aan met de volgende inhoud:

```javascript
let numbers1 = [1,2,3];
let numbers2 = [4,5,6];
let numbers3 = [7,8,9];
```

Maak een variabele **allNumbers** die een array van alle getallen bevat en laat deze zien in het terminal venster.

### 3. Omzetten naar hoofdletters

Maak een bestand `capitalize.js` aan met de volgende inhoud:

```javascript
let names = ['joske','franske','donald','achmed']
```

Maak een variabele **capitalNames** die een array van alle bovenstaande namen bevat maar in hoofdletters. Gebruik hiervoor ook de functie [toUpperCase\(\)](https://www.w3schools.com/jsref/jsref_touppercase.asp). Laat deze zien in het terminal venster.

### 4.  Pokemon 

Maan een bestand `pokemon.js` aan met de volgende inhoud:

```javascript
let starterPokemonGen1 = [
    {name: 'Bulbasaur', xp: 30, type: 'grass'}
    {name: 'Charmander', xp: 50, type: 'fire'},
    {name: 'Squirtle', xp: 45, type: 'water}
];
let starterPokemonGen2 = [
    {name: 'Chikorita', xp: 30, type: 'grass'}
    {name: 'Cyndaquil', xp: 50, type: 'fire'},
    {name: 'Totodile', xp: 45, type: 'water'}
];
```

**Opmerking**: In dit bovenstaande voorbeeld geeft xp weer hoe sterk deze pokemon is. Dit is natuurlijk in de realiteit niet het geval.

**Spread**

1. Maak een variabele **starters.** Zorg ervoor dat ****die de pokemon van beide arrays bevat.  _\(Gebruik hiervoor de spread operator voor arrays\)_
2. Gebruik **console.log** om de starters pokemon in je terminal venster te laten zien.

**Map**

1. Maak een variabele **names.** Zorg ervoor dat deze een array van de namen van de starters pokemon bevat.  _\(Gebruik hiervoor de **map** functie voor arrays\)_
2. Gebruik **console.log** om deze array van namen in je terminal venster te laten zien.

**Filter**

1. Maak een variabele **weakPokemon**. Zorg ervoor dat deze een array van de starters pokemon bevat waarvan de xp waarde kleiner is dan 40 _\(Gebruik hiervoor de filter functie voor arrays\)_
2. Gebruik **console.log** om deze array van weak pokemon in je terminal vester te laten zien.

**Combineren \(Map+Filter\)**

1. Maak een variabele **weakPokemonNames**. Zorg ervoor dat deze een array van namen van pokemon bevat waarvan de xp waarde kleiner is dan 40.  _\(Je kan deze verkrijgen door eerst de filter functie te gebruiken en vervolgens de map functie te gebruiken.\)_
2. Gebruik **console.log** om deze array van de namen van weak pokemon in je terminal venster te laten zien.

**Reduce**

1. Maak een variable **sumOfAllXp.** Zorg ervoor dat deze de som van de xp waarden van alle pokemon bevat. _\(Gebruik hiervoor de reduce functie voor arrays\)_
2. Gebruik **console.log** om deze om te laten zien in je terminal venster.
3. Maak een variabele **strongestPokemon**. Zorg ervoor dat deze de pokemon bevat met de hoogste xp waarde.
4. Gebruik **console.log** om deze om te laten zien in je terminal venster.

**Combineren \(Reduce + Filter** \)

1. Maak een variabele **sumOfAllXpOfWeakPokemon**. ****Zorg ervoor dat deze de som van de xp waarden van alle **weakPokemon** bevat. _\(Je kan deze verkrijgen door eerst de filter functie te gebruiken en vervolgens de map functie te gebruiken\)_
2. Gebruik **console.log** om deze te laten zien in je terminal venster.

**Sorteren**

1. Maak een variabele **sortedStarters**. Zorg ervoor dat deze een array bevat die pokemon bevat die gesorteerd zijn van lage xp naar hoge xp.
2. Gebruik **console.log** om deze te laten zien in je terminal venster.
3. **Extra:** Zorg ervoor dat als twee pokemon gelijke xp hebben dat deze dan alfabetisch gesorteerd worden op naam.

\*\*\*\*



