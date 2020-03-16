# labo 5: functies

### 1. Maak het project aan

Open Visual Studio en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn.

### 2. Strings omdraaien

* Maak een bestand `1_reverse_string.js` aan 
* Schrijf een functie `reverseString`die een string omdraait
* voorbeeld input:  **hello**; verwachte return waarde: **olleh**
* **TIP:** een string kan je omdraaien met 
  * **x.split\(""\).reverse\(\).join\(""\)**
    * Dit zal eerst de string omzetten naar een array via split\(""\)
    * vervolgens kan een ingebouwde reverse functie deze array omdraaien
    * join zorgt er weer voor dat de array naar een string wordt omgezet.
  * **of met een for lus die van achteraan de string gaat naar het begin van de string.**

### 3. Palindroom

* Maak een bestand `2_is_palindroom.js`aan.
* Schrijf een functie `isPalindroom` die 
  * 1 argument heeft: een string
  * teruggeeft of de meegegeven string een palindroom is
* voorbeeld input: **radar** verwachte return waarde: **true**
* voorbeeld input: **hond** verwachte return waarde: **false**
* **TIP**: Je hebt al in oefening 1 een handige functie geschreven om hier bij te helpen

Wat is een palindroom? [http://www.leukespreuk.nl/special\_palindromen.htm](http://www.leukespreuk.nl/special_palindromen.htm)

### 3. **setTimeout**

* Maak een bestand `3_setimeout.js` aan.
* setTimeout is een ingebouwde functie in javascript die een bepaalde functie aanroept na het aantal meegegeven milli seconden.
* Voorbeeld gebruik:

  ```text
  let callback = () => {
      console.log('Na 1 seconde zie je dit!');
  }

  setTimeout(callback, 1000);
  ```

* Probeer dit een keer uit!
* Pas de functie aan zodat ze pas na 5 seconden word aangeroepen.

### 4. klokje met setInterval

* Maak een bestand `4_setinterval.js`aan.
* **setInterval** is een ingebouwde functie die een bepaalde functie om de zoveel tijd zal uitvoeren.
* Maak een klokje dat de tijd om de seconde op het scherm afprint.

```text
15:03:28
15:03:29
15:03:30
...
```

### 5. Hieperdepiep... Hoera!

* Maak een bestand `5_hieperdepiep.js`aan.
* Schrijf hier een functie `hieperdepiep` die
  * 2 argumenten aanvaard:
    * 1ste argument: de leeftijd van de persoon
    * 2de argument: een callback functie  \(artikel: [Wat is een callback-functie?](https://codeburst.io/javascript-what-the-heck-is-a-callback-aba4da2deced)\)
  * Voor het eerste jaar toon: 'Hieperdepiep Hoera' Voor het 2de jaar toon: 'Hieperdepieperdepiep Hoera' Voor het 3de jaar toon: 'Hieperdepieperdepieperdepiep Hoera' ... enz
  * nadat er voor elk jaar Hieperdepiep Hoera is gezegd moet de meegegeven callback uitgevoerd worden
* Voorbeeld output voor `hierpdepiep(5, () => { console.log('Happy Birthday'); });`

```text
Hieperdepiep Hoera
Hieperdepieperdepiep Hoera
Hieperdepieperdepieperdepiep Hoera
Hieperdepieperdepieperdepieperdepiep Hoera
Hieperdepieperdepieperdepieperdepieperdepiep Hoera
Happy Birthday
```

### 6. Hondenleeftijd berekenen

* Maak een bestand `6_hondenleeftijd.js` aan.
* Schrijf hier een functie genaamd `calculateDogAge`die:
  * 1 argument heeft: de leeftijd van je hond
  * de leeftijd van je hond berekent: 1 mensenjaar is 7 hondenjaren
  * die deze leeftijd terug geeft \(via return\)
* Roep deze functie aan met 3 verschillende waarden en print deze af op je scherm via `console.log` 
* **Uitbreiding 1:** Maak een nieuwe functie `calculateAnimalAge` die naast de leeftijd ook een 2de argument mee aanvaard dat de omzettingsverhouding uitdrukt. Om de functie dan aan te roepen voor een hond van 2 jaar doe je `calculateAnimalAge(2, 7)`
* zorg ervoor dat  calculateDogAge deze functie aanroept zodat je niet twee keer dezelfde code hebt staan.
* **Uitbreiding 2:** Maak een nieuwe functie `calculateAnimalAgeFunctional` die 
  * 1 argument heeft: de omzettingsverhouding
  * als return waarde de functie `(age) => { return calculateAnimalAge(age, conversionRatio); }`  teruggeeft.
  * Gebruik deze variabele om de functie calculateHamsterAge te definiëren en gebruik deze om de leeftijd van een hamster van een half jaar te berekenen.

### Extra Oefeningen

#### Konami Code

* Maak een bestand `extra_konami.js` met de volgende inhoud: 

```text
const readline = require('readline');

readline.emitKeypressEvents(process.stdin);
process.stdin.setRawMode(true);

process.stdin.on('keypress', (str, key) => {
    
})
```

* Deze code zorgt ervoor dat er een callback wordt opgeroepen bij het intoetsen van een toets op je keyboard. 
* Zorg ervoor dat je het programma kan stoppen door X in te toetsen.
  * Je kan het programma stoppen door `process.exit()` uit te voeren. 
* Zorg ervoor dat je het programma kan stoppen door de KONAMI code in te geven.  \(wikipedia\) \(of ↑↑↓↓←→←→BA\)

