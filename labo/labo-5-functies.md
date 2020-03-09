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

* Schrijf een functie isPalindroom die 
  * 1 argument heeft: een string
  * teruggeeft of de meegegeven string een palindroom is
* voorbeeld input: **radar** verwachte return waarde: **true**
* voorbeeld input: **hond** verwachte return waarde: **false**
* **TIP**: Je hebt al in oefening 1 een handige functie geschreven om hier bij te helpen

### 3. Hondenleeftijd berekenen

* Schrijf een functie genaamd `calculateDogAge`die:
  * 1 argument heeft: de leeftijd van je hond
  * de leeftijd van je hond berekent: 1 mensenjaar is 7 hondenjaren
  * die deze leeftijd terug geeft \(via return\)
* Roep deze functie aan met 3 verschillende waarden en print deze af op je scherm via `console.log` 
* **Uitbreiding 1:** Maak een nieuwe functie `calculateAnimalAge` die naast de leeftijd ook een 2de argument mee aanvaard dat de omzettingsverhouding uitdrukt. Om de functie dan aan te roepen voor een hond van 2 jaar doe je `calculateAnimalAge(2, 7)`
* zorg ervoor dat  calculateDogAge deze functie aanroept zodat je niet twee keer dezelfde code hebt staan.
* **Uitbreiding 2:** Maak een nieuwe functie `calculateAnimalAgeFunctional` die ipv een omzettingsverhouding een functie aanvaard die de omzetting van mensenjaren naar dierenjaren op zich neemt. Om de functie aan te roepen doe je dan `calculateAnimalAgeFunctional(2, age => age * 7)`
* Gebruik deze calculateAnimalAgeFunctional om de leeftijd van mijn hamster Pikachu berekent: de omzettingsverhouding is 1 jaar is 53 hamsterjaren en mijn hamster is een half jaar oud.

