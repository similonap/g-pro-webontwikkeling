# 04. Decisions en loops

## Decisions

Waarden in scripts kunnen geanalyseerd worden om te bepalen of ze overeenkomen met de verwachte resultaten \(**evaluatie**\). Aan de hand van de resultaten van die evaluaties kan bepaald worden welk pad uw script moet volgen \(**beslissing**\). En er zijn ook veel gelegenheden waarbij dezelfde reeks stappen herhaaldelijk moet uitgevoerd worden \(**loop**\).

### Condities & conditional statements evalueren

Er zijn 2 componenten bij het maken van een beslissing:

1. een expressie is geëvalueerd en geeft als resultaat een waarde
2. een conditional statement \(voldoet aan een voorwaarde\) zegt wat te doen in een bepaalde situatie

```javascript
if (score > 50) {
    console.log('You passed!');
} else {
    console.log('Try again...');
}
```

### Vergelijkingsoperatoren: condities evalueren

|  | vergelijkingsoperator | betekenis | voorbeeld | uitkomst |
| :--- | :--- | :--- | :--- | :--- |
|  | == | is gelijk aan | 'Hello' == 'Goodbye' | false |
|  |  | &gt; waarde vergelijken | 'Hello' == 'Hello' | true |
| voorkeur | === | strikt gelijk aan | '3' === 3 | false |
|  |  | &gt; waarde en data type vergelijken | '3' === '3' | true |
|  | != | is niet gelijk aan | 'Hello' != 'Goodbye' | true |
|  |  | &gt; waarde vergelijken | 'Hello' != 'Hello' | false |
| voorkeur | !== | strikt niet gelijk aan | '3' !== 3 | true |
|  |  | &gt; waarde en data type vergelijken | '3' !== '3' | false |
|  | &gt; | groter dan | 4 &gt; 3 | true |
|  |  |  | 3 &gt; 4 | false |
|  | &gt;= | groter dan of gelijk aan | 4 &gt;=3 | true |
|  |  |  | 3 &gt;= 4 | false |
|  |  |  | 3 &gt;= 3 | true |
|  | &lt; | kleiner dan | 4 &lt; 3 | false |
|  |  |  | 3 &lt; 4 | true |
|  | &lt;= | kleiner dan of gelijk aan | 4 &lt;= 3 | false |
|  |  |  | 3 &lt;= 4 | true |
|  |  |  | 3 &lt;= 3 | true |

try it yourself \(verander var in let!\): [https://www.w3schools.com/jsref/jsref\_operators.asp](https://www.w3schools.com/jsref/jsref_operators.asp)

### Vergelijkingsoperatoren structureren

Bij elke vergelijking zijn er meestal één operator en twee operants. De operants worden geplaatst aan beide kanten van de operator. Deze kunnen zowel waarden als variabelen zijn, veelal gezet tussen ronde haakjes.

```javascript
(score >= pass)
```

### Vergelijkingsoperatoren en expressies

De operant moet niet één waarde of één variabele naam hebben. Het kan evenzeer een expressie zijn \(want elke operant evalueert één enkele waarde\).

```javascript
((score1 + score2) > (highScore1 + highScore2))
```

### Logische operatoren

Vergelijkingsoperatoren geven meestal één enkele waarde terug, true of false. Met logische operatoren kunnen de resultaten van een of meerdere vergelijksoperatoren vergeleken worden.

```javascript
// Do expression 1 and expression 2 both evaluate to true?
// false
((5 < 2) && (2 >= 3))
// Is 5 minder dan 2 => false
// Is 2 groter dan of gelijk aan 3 => false
```

| vergelijkingsoperator | betekenis | voorbeeld | uitkomst |
| :--- | :--- | :--- | :--- |
| && | logisch en | \(\(2 &lt; 5\) && \(3 &gt;= 2\)\) | true |
|  | &gt; test meer dan 1 conditie | true && true | true |
|  |  | true && false | false |
|  |  | false && true | false |
|  |  | false && false | false |
| \|\| | logisch of | \(\(2 &lt; 5\) \|\| \(2 &lt; 1\)\) | true |
|  | &gt; test minstens 1 conditie | true \|\| true | true |
|  |  | true \|\| false | true |
|  |  | false \|\| true | true |
|  |  | false \|\| false  | false |
| ! | niet logisch | !\(2 &lt; 1\) | true |
|  | &gt; neemt 1 boolean-waarde en keert om | !true | false |
|  |  | !false | true |

Logische operatoren evalueren van  **links naar rechts**. Als de eerste conditie genoeg informatie kan verschaffen om een antwoord te formuleren, dan wordt er geen tweede conditie geëvalueerd.

|  |  |
| :--- | :--- |
| false && anything | false |
| true \|\| anything | true |

### If statements

De if-statement evalueert \(en bekijkt\) een conditie. Als de conditie na evaluatie waar \(true\) blijkt, dan worden de instructies in het volgende stuk code uitgevoerd.

```javascript
if (score >= 50) {
    congratulate();
}
```

try it yourself \(verander var in let!\): [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_if](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_if)

### If...else statements

De if...else-stament evalueert een conditie. Als de uitkomst waar is \(true\) dan wordt het eerste stuk code uitgevoerd. Als de conditie een 'false' geeft, wordt de tweede blok code uitgevoerd.

```javascript
if (score >= 50) {
    congratulate();
}
else {
    encourage();
}
```

try it yourself  \(verander var in let!\): [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_if\_else](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_if_else)

### Switch statements

Een switch-statement start met een variabele, namelijk de switch-waarde. Elk geval geeft een mogelijke waarde voor deze variabele en de code die gerund zou moeten worden als de variabele met de waarde overeen komt.

```javascript
switch (level) {

case 'One':
    title = 'Level 1';
    break;

case 'Two':
    title = 'Level 2';
    break;

case 'Tree':
    title = 'Level 3';
    break;
    
default:
    title = 'Test';
    break;
}
```

try it yourself \(verander var in let!\):  
[https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_switch](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_switch)  
[https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_switch3](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_switch3)

## Loops

Loops checken een conditie. Als deze waar of 'true' blijkt, zal een blok code uitgevoerd worden. Hierna zal de conditie herbekeken worden en als de uitkomst terug 'true' geeft, wordt dezelfde blok code terug uitgevoerd. Dit blijft doorgaan tot de uitkomst 'false' geeft.  
Er zijn drie veel voorkomende soorten loops:

1. **for**  loopt een aantal keren door een codeblok  **for / in** loopt door de eigenschappen van een object  **for / of** doorloopt de waarden van een letterlijk object 
2. **while** doorloopt een codeblok terwijl een opgegeven voorwaarde 'true' is 
3. **do / while** loopt ook door een codeblok terwijl een opgegeven voorwaarde 'true' is

```javascript
for (let i =0; i < 10; i++) {
    console.log(i);
}
```

try it yourself \(verander var in let!\):  
**for**: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_for](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_for)  
**for / in**: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_forin](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_forin)  
**for / of**: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_forof](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_forof)  
**while**: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_while](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_while)  
**do / while**: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_dowhile](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_dowhile)

### Loop tellers

Een for-loopt gebruikt een teller als voorwaarde. Hiermee geeft u de code de opdracht een bepaald aantal keren uit te voeren. Hier kunt u zien dat de voorwaarde uit drie verklaringen bestaat:

1. **initialisatie**: Een expressie \(inclusief toewijzingsuitdrukkingen\) of variabele declaratie wordt eenmaal geëvalueerd voordat de lus begint. Meestal wordt een ​​tellervariabele gebruikt om te initialiseren. Deze uitdrukking kan optioneel nieuwe variabelen met let-sleutelwoorden declareren. Variabelen die met let zijn gedeclareerd, zijn lokaal voor de instructie.
2. **conditie**: Een expressie moet geëvalueerd worden vóór elke loop-herhaling. Als deze expressie de waarde true geeft, wordt de instructie uitgevoerd. Deze voorwaardelijke test is optioneel. Indien weggelaten, wordt de voorwaarde altijd geëvalueerd als true. Als de uitdrukking onwaar is, wordt de uitvoering overgeslagen naar de eerste uitdrukking na for.
3. **update**: Een expressie die moet worden geëvalueerd aan het einde van elke loop-herhaling. Dit gebeurt vóór de volgende evaluatie van de aandoening. Dit wordt over het algemeen gebruikt om de tellervariabele bij te werken of te verhogen.

```javascript
let i =0; 
i < 10; 
i++
```

### Key loop concepten

#### Kernwoorden

De volgende kernwoorden worden frequent gebruikt in loops:

* **break**: Dit kernwoord zorgt dat de lus beëindigd wordt en geeft de instructie om naar de volgende code buiten de loop te gaan. \(Dit wordt ook gebruikt binnen functies.\) 
* **continue**: Dit kernwoord vertelt verder te gaan met de huidige iteratie en controleer daarna de conditie opnieuw. \(Als er true komt, wordt de code opnieuw uitgevoerd.\)

#### Loops en arrays

Loops zijn erg handig bij het werken met arrays als je wil dat dezelfde code telkens opnieuw uitgevoerd wordt voor elk item in de array. 

#### Performance issues

Het is belangrijk te weten dat wanneer een browser JavaScript inleest, het stopt al de rest totdat het dat script heeft verwerkt. Als de loop een klein aantal items met verwerken, zal dit geen probleem zijn. Als echter de loop veel items bevat, kan het dat de pagina trager inlaadt. Als de conditie nooit een 'false' terugkrijgt, zit je met een oneindige lus. De code blijft lopen tot het geheugen van de browser wordt leeg gemaakt en het script breekt. 

Elke variabele die gedefinieerd kan worden buiten de loop en die niet verandert binnen de loop, moet daarbuiten worden gedefinieerd. Als het binnen de loop zou staan, zou deze telkens opnieuw berekend worden elke keer dat de loop loopt en worden zo nodeloos middelen gebruikt.

## Extra info voor labo

### parseInt

**parseInt**: parseInt ontleedt een string en retourneert een geheel getal.

meer info: [https://www.w3schools.com/jsref/jsref\_parseint.asp](https://www.w3schools.com/jsref/jsref_parseint.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_parseint](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_parseint)

### switch

**switch**: switch wordt gebruikt om verschillende acties uit te voeren op basis van verschillende omstandigheden. Gebruik `switch` om een ​​van de vele codeblokken te selecteren en uit te voeren.  
Hoe werkt dit? De 'switch' wordt eenmaal geëvalueerd. De waarde van de uitdrukking wordt vergeleken met de waarden van elke `case`. Als er een overeenkomst is, wordt het bijbehorende codeblok uitgevoerd.

meer info: [https://www.w3schools.com/js/js\_switch.asp](https://www.w3schools.com/js/js_switch.asp)  
try it ourself: [https://www.w3schools.com/js/tryit.asp?filename=tryjs\_switch2](https://www.w3schools.com/js/tryit.asp?filename=tryjs_switch2), [https://www.w3schools.com/js/tryit.asp?filename=tryjs\_switch3](https://www.w3schools.com/js/tryit.asp?filename=tryjs_switch3)

### while

**while**: while creëert een lus die wordt uitgevoerd terwijl een opgegeven voorwaarde waar is. De lus blijft lopen zolang de voorwaarde waar is en stopt alleen wanneer de toestand vals wordt.  
Gebruik de instructie `break` om uit een loop te gaan en de instructie `continue` om een ​​waarde in een loop over te slaan.

meer info: [https://www.w3schools.com/jsref/jsref\_while.asp](https://www.w3schools.com/jsref/jsref_while.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_while](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_while), [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_break\_while](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_break_while)

### for

**for**: for maakt een lus die wordt uitgevoerd en blijft lopen zolang een voorwaarde waar is. De lus stopt enkel en alleen wanneer de voorwaarde niet waar en dus 'false' wordt.

meer info: [https://www.w3schools.com/jsref/jsref\_for.asp](https://www.w3schools.com/jsref/jsref_for.asp)  
try it yourself: [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_for\_arr](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_for_arr)

