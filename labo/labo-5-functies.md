# labo 5: Functies

### 1. Hondenleeftijd berekenen

* Schrijf een functie genaamd `calculateDogAge`die:
  * 1 argument heeft: de leeftijd van je hond
  * de leeftijd van je hond berekent: 1 mensenjaar is 7 hondenjaren
  * die deze leeftijd terug geeft \(via return\)
* Roep deze functie aan met 3 verschillende waarden en print deze af op je scherm via `console.log` 
* **Uitbreiding 1:** Maak een nieuwe functie `calculateAnimalAge` die naast de leeftijd ook een 2de argument mee aanvaard dat de omzettingsverhouding uitdrukt. Om de functie dan aan te roepen voor een hond van 2 jaar doe je `calculateAnimalAge(2, 7)`
* zorg ervoor dat  calculateDogAge deze functie aanroept zodat je niet twee keer dezelfde code hebt staan.
* **Uitbreiding 2:** Maak een nieuwe functie `calculateAnimalAgeFunctional` die ipv een omzettingsverhouding een functie aanvaard die de omzetting van mensenjaren naar dierenjaren op zich neemt. Om de functie aan te roepen doe je dan `calculateAnimalAgeFunctional(2, age => age * 7)`
* Gebruik deze calculateAnimalAgeFunctional om de leeftijd van mijn hamster Pikachu berekent: de omzettingsverhouding is 1 jaar is 53 hamsterjaren en mijn hamster is een half jaar oud.

