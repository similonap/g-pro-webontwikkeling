# labo 6: map/reduce/filter

### 1. Maak het project aan

Open Visual Studio Code en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn.

### 3.  Pokemon 

Maan een bestand `pokemon.js` aan met de volgende inhoud:

```javascript
let starterPokemonGen1 = [
    {name: 'Bulbasaur', xp: 30, type: 'grass'}
    {name: 'Charmander', xp: 50, type: 'fire'},
    {name: 'Squirtle', xp: 45, type: 'water}
];
let starterPokemonGen1 = [
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
4. gebruik **console.log** om deze om te laten zien in je terminal venster.

**Combineren \(Reduce + Filter** \)

1. Maak een variabele **sumOfAllXpOfWeakPokemon**. ****Zorg ervoor dat deze de som van de xp waarden van alle **weakPokemon** bevat. _\(Je kan deze verkrijgen door eerst de filter functie te gebruiken en vervolgens de map functie te gebruiken\)_
2. Gebruik **console.log** om deze te laten zien in je terminal venster.



