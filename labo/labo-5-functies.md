# labo 5: Functies

### 1. Strings omdraaien

* schrijf een functie `reverseString`die een string omdraait
* voorbeeld input:  **hello**; verwachte return waarde: **olleh**
* **TIP:** een string kan je omdraaien met 
  * **x.split\(""\).reverse\(\).join\(""\)**
    * Dit zal eerst de string omzetten naar een array via split\(""\)
    * vervolgens kan een ingebouwde reverse functie deze array omdraaien
    * join zorgt er weer voor dat de array naar een string wordt omgezet.
  * **of met een for lus die van achteraan de string gaat naar het begin van de string.**

### 2. Palindroom

* Schrijf een functie `isPalindroom` die 
  * 1 argument heeft: een string
  * teruggeeft of de meegegeven string een palindroom is
* voorbeeld input: **radar** verwachte return waarde: **true**
* voorbeeld input: **hond** verwachte return waarde: **false**
* **TIP**: Je hebt al in oefening 1 een handige functie geschreven om hier bij te helpen

### 4. **setTimeout**

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

### 5. klokje met setInterval

* **setInterval** is een ingebouwde functie die een bepaalde functie om de zoveel tijd zal uitvoeren.
* Maak een klokje dat de tijd om de seconde op het scherm afprint.
* **Gebruik hiervoor het Date object.**
  * Hoe uren verkrijgen? new Date\(\).getHours\(\);  Hoe minuten verkijgen? new Date\(\).getMinutes\(\); ...

### 6. Hieperdepiep... Hoera!

* Schrijf een functie `hieperdepiep` die
  * 2 argumenten aanvaard:
    * 1ste argument: de leeftijd van de persoon
    * 2de argument: een callback functie
  * eerst voor elk jaar van de leeftijd van de persoon 'Hieperdepiep hoera' op het scherm toont
  * nadat er voor elk jaar Hieperdepiep Hoera is gezegd moet de meegegeven callback uitgevoerd worden
* Voorbeeld output voor `hierpdepiep(5, () => { console.log('Happy Birthday'); });`

```text
Hieperdepiep Hoera
Hieperdepiep Hoera
Hieperdepiep Hoera
Hieperdepiep Hoera
Hieperdepiep Hoera
Happy Birthday
```

### 7. Hondenleeftijd berekenen

* Schrijf een functie genaamd `calculateDogAge`die:
  * 1 argument heeft: de leeftijd van je hond
  * de leeftijd van je hond berekent: 1 mensenjaar is 7 hondenjaren
  * die deze leeftijd terug geeft \(via return\)
* Roep deze functie aan met 3 verschillende waarden en print deze af op je scherm via `console.log` 
* **Uitbreiding 1:** Maak een nieuwe functie `calculateAnimalAge` die naast de leeftijd ook een 2de argument mee aanvaard dat de omzettingsverhouding uitdrukt. Om de functie dan aan te roepen voor een hond van 2 jaar doe je `calculateAnimalAge(2, 7)`
* zorg ervoor dat  calculateDogAge deze functie aanroept zodat je niet twee keer dezelfde code hebt staan.
* **Uitbreiding 2:** Maak een nieuwe functie `calculateAnimalAgeFunctional` die ipv een omzettingsverhouding een functie aanvaard die de omzetting van mensenjaren naar dierenjaren op zich neemt. Om de functie aan te roepen doe je dan `calculateAnimalAgeFunctional(2, age => age * 7)`
* Gebruik deze calculateAnimalAgeFunctional om de leeftijd van mijn hamster Pikachu berekent: de omzettingsverhouding is 1 jaar is 53 hamsterjaren en mijn hamster is een half jaar oud.

