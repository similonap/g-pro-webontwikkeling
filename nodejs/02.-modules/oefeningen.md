# oefeningen

### Opdracht 1: Gebruik maken van externe modules in kleur

* Gebruik de npm module chalk \([https://www.npmjs.com/package/chalk](https://www.npmjs.com/package/chalk)\) om in mooie kleurtjes Hello World op het scherm te laten verschijnen.  
* Hello moet geschreven met witte letters op rode achtergrond.
* World moet geschreven zijn met gele letters op een blauwe achtergrond.

### Opdracht 2: Eigen module maken

* Schrijf een programma \(index.js\) met een functie hello en argumenten **voor** en **achternaam.**  Deze functie zal 'Hallo &lt;voornaam&gt; &lt;achternaam&gt;!' afprinten.
* Roep deze functie op vanuit hetzelfde bestand.
* Verhuis deze functie naar een aparte module 'helloModule' en exporteer deze. 
* Gebruik nu deze functie in je hoofdbestand. 

Verwachte output:

```text
Hello Andie Similon!
```

### Opdracht 3: Gebruik maken van externe modules en maken van eigen modules

* Maak een node js applicatie die gebruik maakt van de _Pokedex_ module \([https://www.npmjs.com/package/pokedex](https://www.npmjs.com/package/pokedex)\).
* Elke _Pokémon_ heeft een id startende met het getal 1 \(dus niet 0 zoals bij een array\).
* Schrijf een functie **printPokemonBetween\(from, to\)** die de **id** en **naam** uitprint naar de console.
* Roep deze functie aan en print de _Pokémon_ tussen 1 en 10 naar de console.

**Verwachte output**

```text
➜  labo1 node index.js
1: bulbasaur
2: ivysaur
3: venusaur
4: charmander
5: charmeleon
6: charizard
7: squirtle
8: wartortle
9: blastoise
10: caterpie
```

* Verplaats alle code die te maken heeft met het afprinten van _Pokémon_ naar een apart bestand en maak ze beschikbaar als module. Roep deze functies aan in je index.js bestand. De output moet identiek blijven.

### Opdracht 4: Gebruik maken van externe module moment

* Gebruik de npm module moment \([https://www.npmjs.com/package/moment](https://www.npmjs.com/package/moment)\) om een klokje te maken dat elke seconde de nieuwe tijd laat zien. Maak gebruik van de ingebouwde [setInterval](https://www.w3schools.com/jsref/met_win_setinterval.asp) functie.
* Als extra zou je je scherm kunnen leegmaken elke keer hij de tijd laat zien met de volgende regel code: `process.stdout.write('\033c');` \(niet te kennen of begrijpen\)

