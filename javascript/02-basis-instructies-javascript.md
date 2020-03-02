# 02. Basis instructies Javascript

## Instructies 

JavaScript bestaat uit een opeenvolging van instructies ook wel **statements** genoemd. **Deze eindigen steeds met een puntkomma \(`;`\)** \(zoals ook in het Nederlands een zin eindigt met een punt\).

Verder wordt er gebruik gemaakt van accolades om code te groeperen in blokken. De `if`statements in onderstaand voorbeeld gaan bepalen welke blok code er zal uitgevoerd worden. We komen terug op `if` in hoofdstuk 4 van JavaScript. 

```javascript
let today = new Date();
let hourNow = today.getHours();
let greeting;
if (hourNow > 18) { 
    greeting = 'Goedeavond'; 
}
else if (hourNow > 12) {
    greeting = 'Goedemiddag'; 
}
else if (hourNow > 0) {
    greeting = 'Goedemorgen'; 
}
else {
    greeting = 'Welkom'; 
}
console.log(greeting);
```

## Commentaar

In JavaScript kan commentaar toegevoegd worden ter verduidelijking van de code. Code die zichzelf uitwijst behoeft dus geen commentaar. Zet commentaar waar nodig, maar overdrijf niet.

In JavaScript heb je twee manieren om commentaar te plaatsen:

1. `//`: **single-line commentaar**: De commentaar past op de huidige regel. Commentaar kan opsplitst worden in meerdere lijnen, indien telkens voorafgegaan door twee schuine strepen.
2. `/*  */`: **multi-line commentaar**: Commentaar die doorloopt over meerdere regels begint met slash gevolgd door een asterisk `/*` en eindigen met een asterisk gevolgd door een slash `*/`

```javascript
// Dit is commentaar op 1 lijn
/*
   Dit is commentaar
   verspreid over meerdere lijnen
*/
```

## Variabelen

Variabelen zijn plekken waar je script tijdelijke informatie kan plaatsen. Als je bijvoorbeeld de oppervlakte van een muur wil berekenen, zal je eerst de hoogte en de breedte van die muur ergens moeten onthouden, alvorens je kan starten met het berekenen van de oppervlakte. Het onthouden van deze getallen binnen het script doe je door middel van variabelen. 

## Data types

Je kan meerdere types gegevens in een variabele bewaren: 

* **string data type**: te gebruiken bij tekst
* **numeric data type**: te gebruiken bij getallen
* **boolean data type**: te gebruiken bij antwoord 'ja' of 'neen'
* **object data type**: te gebruiken voor de overige zaken

meer info: [https://www.w3schools.com/java/java\_data\_types.asp](https://www.w3schools.com/java/java_data_types.asp)

Een variabele heeft een

* **naam**: de naam van de variabele
* **adres**: de plaats \(= geheugenadres\) van de variabele
* **waarde**: de waarde van een bepaald gegevenstype
* een **bereik** \(**scope**\): bepaalt tot waar een variabele in de code "zichtbaar" is en dus gebruikt kan worden.
* een **levensduur**: is de tijd dat de variabele geassocieerd blijft met een bepaald geheugenadres. Deze levensduur begint op het moment dat de variabele gemaakt wordt en eindigt op het moment dat hij verwijderd wordt door het programma zelf of uitdrukkelijk door de programmeur in de code. De levensduur van een variabele betekent niet hetzelfde als het bereik van een variabele.

meer info: [https://www.w3schools.com/js/js\_variables.asp](https://www.w3schools.com/js/js_variables.asp)

### Naam

* hoofdlettergevoelig;
* combinatie van letters, cijfers, onderlijningsteken, maar mag niet beginnen met een cijfer;
* maak gebruik van UperCamelCase en lowerCamelCase \([https://nl.wikipedia.org/wiki/CamelCase](https://nl.wikipedia.org/wiki/CamelCase)\)

### Scope

De scope van een variabele is het gebied van de code waarin je de variabele kan gebruiken. De scope van de variabele hangt af van het type van de variabele. In javascript heb je 2 types

* var \(function scoped variabelen\)
* let \(block scoped variabelen\)

{% hint style="info" %}
Hoe je `var` en `let`best gebruikt lees je in [Kyle Simpson, For and against 'let', October 27, 2014](https://davidwalsh.name/for-and-against-let). Ook voor de implicaties wanneer je closures gebruikt.
{% endhint %}

video: [Variabele scope](http://www.screencast.com/t/6KcGnjy3Za1)

#### var

Variabelen die door `var` worden gedeclareerd hebben functiebereik en worden naar boven gehesen \(hoisted to the top\). Het betekent dat een variabele kan worden gebruikt voordat die gedeclareerd is. Wat maakt dat je zeer lelijke code kan schrijven.

{% hint style="warning" %}
Wanneer JavaScript in een programma een nieuwe functie uitvoert, worden alle variabelen, gedeclareerd met `var`, verplaatst \(of verheven, of gehesen\) naar de top van de functie. Dit is een belangrijk concept om in gedachten te houden. Daarenboven wordt alleen de declaratie opgehesen, wat betekent dat alleen de aanwezigheid van de variabele wordt verplaatst naar de top. Alle toewijzingen blijven waar ze zijn. In het Engels heet dat _variable hoisting_.
{% endhint %}

```javascript
// Goed gebruik van var
var a;
a = 2;

var b = 3;

// Voorbeelden van slechte code mogelijk met var
// Dit kan:
d = 2;
var d;
// Dit ook:
b = 2;
if (true) {
    var b;
}

// Dit kan niet
function eenFunctie() {
    var c;
}
c = 5;
```

#### let

Het `let` statement declareert een lokale variabele met blokbereik en initialiseert die eventueel met een waarde. Variabelen gedeclareerd met `let` worden niet naar de top gehesen en kunnen niet gebruikt worden, voordat ze gedeclareerd zijn.

```javascript
// Dit kan
let a;
a = 2;
// Dit kan ook
let b;
if (true) {
    b = 2;
}

// Dit kan niet
c = 3;
let c;

// Dit ook niet
if (true) {
    let d;
}
d = 4;
```

#### Declaratie en gebruik van var en let

Met `var` en `let` kun je:

```javascript
// declareren
let getal;
// initialiseren
getal = 10;
// declareren en initialiseren
/// met 1 variabele
let getal0 = 10;
/// met meerdere variabelen
let getal1, getal2 = 4, naam1, naam2 = 'Jan', naam = 'Anna', getal = 1;
```

## Constanten

JavaScript \(ES6\) kent ook het keyword `const` dat wordt gebruikt voor constanten. Het is de gewoonte om de naam van een constante met hoofdletters te schrijven.

#### Constant Reference, geen Value

Het wordt vaak verkeerd geïnterpreteerd als een "constante waarde". Maar in ES6 is `const` een verwijzing naar een constante verwijzing naar een waarde \(hetzelfde geldt in de meeste talen\). Met andere woorden, de pointer die de naam van de variabele gebruikt, kan niet veranderd worden in het geheugen, maar datgene waarnaar de variabele verwijst wel.

In de onderstaande code creëren we een nieuwe variabele met een constante verwijzing naar een array. We kunnen waarden toe voegen aan de array en aangezien dit niet de referentie wijzigt, lukt dat:

```javascript
const namen = [];
namen.push ( "Jetmir");
console.log (namen);
```

Maar als we proberen om de variabele referentie naar de nieuwe array te wijzigen - zelfs één met dezelfde inhoud- krijgen we een SyntaxError \( "Assignment constant variabele"\):

```javascript
const namen = [];
namen = []; // Error!
```

Als je een `const` die verwijst naar een waarde van het primitieve gegevenstype, zoals een `string` of `number`, dan valt er niets veranderen aan die waarde. Alle methoden op `String` en `Number` retourneren nieuwe waarden \(kopieën van objecten\).

Let er tenslotte op dat `const` dezelfde nieuwe scoping regels volgt net als `let`!  
meer info: [https://www.w3schools.com/js/js\_const.asp](https://www.w3schools.com/js/js_const.asp)

## Arrays

#### Beschrijving

De standaard definitie voor een array is een lineaire verzameling van elementen. De individuele elementen in die verzameling kunnen worden opgevraagd met een indexcijfer. De indexcijfers zijn gehele getallen die meestal gebruikt worden om de offset van het element tegenover het startpunt van de array te berekenen. De meeste programmeertalen beschikken over dat soort arrays. JavaScript heeft echter een ander type array.

Een array is in JavaScript eigenlijk een gespecialiseerde soort JavaScript-object. De indexcijfers, integers, zijn eigenlijk de namen van de eigenschappen. Ze stellen offsets voor, maar het zijn geen offsets. De gehele getallen, die worden gebruikt voor indices, worden intern geconverteerd naar tekenreeksen om als namen van eigenschappen van JavaScript-objecten te kunnen gebruiken.

Je kunt een JavaScript array voorstellen als een tabel. In de eerste kolom staat de sleutel, namelijk de index, en in de tweede kolom staat de waarde:

| Sleutel | Waarde |
| :--- | :--- |
| 0 | appel |
| 1 | peer |
| 2 | sinaasappel |
| 3 | ananas |
| "Naam" | citroen |
| "vijf" | mango |

Dat brengt wel met zich mee dat JavaScript-arrays niet zo efficiënt als de 'klassieke' arrays van andere programmeertalen.

### Declareren en initialiseren

Na de fundamentele primitieve gegevenstypen in JavaScript, is het tijd om naar een meer krachtige gegevensstructuur — de array over te stappen.

Wat is een array? Het is gewoon een lijst \(een reeks\) van waarden. In plaats van één enkele variabele om één waarde op te slaan, kun je een array variabele gebruiken voor het opslaan van een willekeurig aantal waarden. Die waarden vormen de elementen van de array.

Een array variabele declareer je als volgt:

```javascript
// declareren
let first_array = [];
```

Je kunt een array declareren en initialiseren tegelijkertijd:

```javascript
// declareren en initialiseren
let second_array = [1, 2, 3];
```

**Array\(\)** is een ingebouwde functie die als een **constructor** functie kan gebruiken om arrays te maken:

```javascript
let a = new Array();
```

Dat is hetzelfde als:

```javascript
let a = [];
```

Vermits arrays gemaakt kunnen worden met een constructor functie zijn het eigenlijk objecten. Je kunt dit nagaan met de typeof operator:

```javascript
let a = new Array(5);
typeof a;
// geeft als resultaat: "object"
```

Vermits arrays objecten zijn, erven ze de eigenschappen en dus ook de methoden over van het moeder Object:

```javascript
let a = new Array('Jan');

a.toString();
// resultaat: "Jan"
a.valueOf();
/* resultaat:
   [
      0: "Jan",
      length: 1
   ]
*/
```

Arrays zijn wel objecten, maar van een speciale soort:

* de namen van hun eigenschappen worden automatisch toegekend. Het zijn getallen die index voorstellen te beginnen met 0;
* ze hebben een length eigenschappen die het aantal elementen in de array retourneert;
* ze hebben meer methoden dan een gewoon object.

### Element ophalen

Hoe krijg je toegang tot de waarden die zijn opgeslagen in een array? De elementen in een array worden geïndexeerd met opeenvolgende nummers vanaf nul. Het eerste element is index \(of positie\) 0, de tweede heeft indexnummer 1, enzovoort. Hier is de drie-element array uit het vorige voorbeeld:

| Sleutel/ Index | Waarde |
| :--- | :--- |
| 0 | 1 |
| 1 | 2 |
| 2 | 3 |

Om een array-element op te halen, geef je de index van dat element tussen vierkante haken mee. Dus, een `[0]` geeft je het eerste element van de array a, een `[1]` geeft het tweede, enzovoort:

```javascript
a[0];
// resultaat: 1
a[1];
// resultaat: 2
```

### Element wijzigen

Met de index kun je een element ook wijzigen. Om het tweede element \(index 2\) in de second\_aray te wijzigen:

```javascript
second_array[1] = 11;
```

### Element toevoegen

Om een nieuw element toe te voegen gebruik je een nog niet gebruikte index:

```javascript
second_array[3] = 15;
```

Hiermee voeg je een vierde element aan de bestaande array toe.

Als je een gat laat tussen de opeenvolgende indexen zullen die tussenliggende posities `undefined` retourneren als je ze ophaalt.

Het doet er niet toe hoe de array werd gemaakt, de manier van elementen toevoegen is hetzelfde:

```javascript
a[0] = 1;
a[1] = 2;
a[2] = 'David';
a;
/* resultaat:
   [
      0: 1,
      1: 2,
      2: "David",
      length: 3
   ]
*/
```

Er is een uitzondering op deze regel. Als slechts 1 argument meegeeft aan de constructor functie wordt beschouwd als de lengte van de array:

```javascript
let a = new Array(5);
a;
/* resultaat:
   [
      0: undefined,
      1: undefined,
      2: undefined,
      3: undefined,
      4: undefined,
      length: 5
   ]
*/
```

### Element deleten

Om een element te verwijderen gebruik je de `delete` operator. Na het verwijderen van een element uit de array blijft de lengte van de array onveranderd. Je krijgt een gat in je array. Als je het element opvraagt met de overeenkomstige index krijg je `undefined`.

```javascript
typeof second_array[2];
// resultaat: "number"
delete second_array[2];
typeof second_array[2];
// resultaat: "undefined"
```

### De lengte eigenschap

De `length` eigenschap bevat het aantal elementen in de array. Je kunt de `length` eigenschap instellen. Er worden dan extra plaatsen in de array voorzien, maar de waarde ervan is `undefined`.

Alle array objecten hebben een `length` eigenschap.

```javascript
let a = new Array('Jan');
a.length;
// resultaat: 1
```

Je kunt de lengte zelf instellen:

```javascript
a.length = 2;
a.length;
// resultaat: 2
```

Een tweede element wordt toegevoegd, maar er is geen waarde aan toegekend.

```javascript
a[1];
// resultaat: undefined
```

Je kunt er een waarde aan toe kennen:

```javascript
a[1] = 'Piet';
a[1];
// resultaat: "Piet"
```

Je kunt een array ook inkorten door de lengte kleiner te maken:

```javascript
a.length = 1;
a;
/* resultaat:
   [
      0: "Jan",
      length: 1
   ]
*/
```

### Voorbeelden

{% hint style="info" %}
Als je de onderstaande codepen opent op de codepen website, kun je de javascript console openen om de output van het script te bekijken. 
{% endhint %}

{% embed url="https://codepen.io/wouterpeetermans/pen/GRRNGEq?editors=0011" %}

```javascript
var fruit = [];
fruit[0] = "appel";
fruit[3] = "peer";
fruit[5] = "ananas";
fruit["plopperdeplop"] = function() { //moet nog niet gekend zijn
  return "banaan";
};
console.log('Aantal elementen in fruit array: ' + fruit.length);
console.log('Plopperdeplop:' + fruit["plopperdeplop"]);
console.log(fruit[0]);
console.log(fruit[1]);
console.log(fruit[2]);
console.log(fruit[3]);
console.log(fruit[4]);
console.log(fruit[5]);
console.log(fruit[6]);
```

## Expressies

Met constanten en variabelen kun je expressies bouwen. Een expressie is een uitdrukking waarmee je de waarde van een variabele kan veranderen of meerdere variabelen combineren om tot 1 waarde te komen.

Het gegevenstype van een expressie hangt af van de gegevenstypes van de constanten en variabelen waaruit ze is opgebouwd.

Als we constanten en variabelen van het type getal gebruiken in een expressie, zal die expressie zelf ook van het type getal zijn. Als we een getal-variabele maken met `x = 1`, dan zal de expressie `x + 1` het resultaat 2 opleveren. We kunnen dat resultaat toekennen aan een variabele y met `y = x + 1`, waarna y een getal-variabele is geworden die de waarde 2 bevat.

Iets vergelijkbaars geldt voor strings. Als we schrijven: `x = "Hello, "` en vervolgens `y = x + "world"`, dan is y een string-variabele geworden met als waarde `"Hello, world"`.

Gebruiken we echter getallen en strings door elkaar heen, dan zijn de resultaten wat minder voor de hand liggend: JavaScript zet in zo'n geval namelijk eerst de getallen om naar strings. Als we een string-variabele maken met: `x = "1"`, dan zal de expressie `x + 1` als resultaat niet het getal 2, maar de string `"11"` opleveren!

Als je boolean-waarden en strings of getallen door elkaar gebruikt in een expressie, levert dat het volgende op: true wordt in een getal-expressie omgezet naar het getal 1, en in een string-expressie naar de string `true`. Voor false zijn dat respectievelijk het getal 0 en de string `false`.

## Operatoren

Operatoren bepalen welke acties we op variabelen en waarden willen uitvoeren.

### Wiskundige operatoren

{% hint style="info" %}
In de tabel hieronder geld: `getal = 10;`
{% endhint %}

| **operator** | **omschrijving** | **voorbeeld** | **uitkomst** |
| :--- | :--- | :--- | :--- |
| + | optellen | resultaat = getal + 5 | resultaat = 15 |
| - | aftrekken | resultaat = getal - 5 | resultaat = 5 |
| \* | vermenigvuldigen | resultaat = getal \* 5 | resultaat = 50 |
| / | delen | resultaat = getal / 5 | resultaat = 2 |
| % | modulo, de rest van een deling | resultaat = getal % 3 | resultaat = 1 |
| ++ | vermeerderen met 1 | getal ++ | getal = 11 |
| -- | verminderen met 1 | getal -- | getal = 9 |

Het is soms nodig om te testen of een getal even of oneven is. Met de modulo operator kun je dat gemakkelijk doen. Alle oneven getallen geven als resultaat 1 als je ze deelt door 2, terwijl alle even nummers 0 retourneren.

### De string + operator

Om strings aan elkaar te plakken gebruik je de + operator \(lees string + operator\).

```javascript
let voornaam = 'Barack';
let familienaam = 'Obama';
let naam = voornaam + '  ' + familienaam;
```

### Toekenningsoperatoren

In het Engels heet dat een _assignment operator._  
Er bestaan twee soorten toekenningsoperatoren.

1. Enkelvoudige toekenningsoperator Met de toekenningsoperator ken je een waarde toe aan een variabele. Je gebruikt die operator om een variabele te initialiseren.  let `naam = 'Barack Obama';`
2. Samengestelde toekenningsoperatoren  
    Samengestelde toekenningsoperatoren zijn een samentrekking van een wiskundige bewerking of een string bewerking met een toekenning.  
    Bijvoorbeeld `getal = getal + 1` kan samengetrokken worden tot `getal += 1`. Met een string variabele kan je dat ook doen: `naam = naam + ' de president van Amerika'` wordt samengetrokken tot `naam += ' de president van Amerika'`.

   | **operator** | **voorbeeld** | **samentrekking van** | **uitkomst** |
   | :--- | :--- | :--- | :--- |
   | += | getal += 5 | getal = getal + 5 | getal = 15 |
   | -= | getal -= 5 | getal = getal - 5 | getal = 5 |
   | \*= | getal \*= 5 | getal = getal \* 5 | getal = 50 |
   | /= | getal /= 5 | getal = getal / 5 | getal = 2 |
   | %= | getal %= 3 | getal = getal % 3 | getal = 1 |

### Vergelijkingsoperatoren

| **operator** | **betekenis** |
| :--- | :--- |
| == | is gelijk aan |
| === | betekent is gelijk aan als ook het gegevenstype van beide operanden gelijk is; er treedt dus geen gegevenstype-conversie op bij de vergelijking |
| != | is verschillend van |
| !== | betekent is verschillend van; als het gegevenstype van beide operanden niet gelijk is levert de expressie altijd een `false` op; er treedt geen gegevenstype-conversie op bij de vergelijking |
| &gt; | is groter dan |
| &lt; | is kleiner dan |
| &gt;= | is groter dan of gelijk aan |
| &lt;= | is kleiner dan of gelijk aan |

### Logische operatoren

Er zijn drie logische operatoren die werken met booleaanse waarden:

| operator | betekenis |
| :--- | :--- |
| ! | logische NIET |
| && | logische EN |
| \|\| | logische OF |

### Volgorde van bewerkingen

In de wiskunde gelden dezelfde regels:  
Bij logische operatoren heeft de **`!`** de hoogste prioriteit, dan de `&&` en tenslotte de `||`.

Tip: Gebruik altijd haakjes, zodat je de volgorde zelf controleert en niet afhankelijk bent van de JavaScript-engine.

### Luie evaluatie

Als je verschillende logische operaties na elkaar plaatst, stop JavaScript met evalueren vanaf het moment dat de uitkomst duidelijk wordt. De rest van de expressie wordt niet meer geëvalueerd: `true || false || true || false || true;`

```javascript
true
```

Omdat dat allemaal OF-operaties zijn en dus dezelfde prioriteit hebben, is het resultaat true als minstens 1 van de waarden waar is. Dus het volstaat de eerste operand te evalueren om de te weten wat het uiteindelijke resultaat zal zijn. De JavaScript-engine besluit lui te zijn en vermijdt onnodig werk door code die geen invloed meer kan hebben op het resultaat niet te evalueren.

{% hint style="info" %}
Voor veel meer details over operatoren zie Mozilla Developer Network \(MDN\) "[Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)".
{% endhint %}



