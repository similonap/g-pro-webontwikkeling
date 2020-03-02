# 03. Functies, methods en objects



Browser hebben zeer gedetailleerde instructies nodig om te doen wat we van hen verwachten. Zodoende moeten er soms honderden of duizenden lijnen code geschreven worden. Programmeurs gebruiken hiervoor functions, methods en objects om hun code te organiseren.

Dit hoofdstuk is verdeeld in drie onderdelen: 

1. **Functies en methods**: Functies bestaan ​​uit een reeks instructies die gegroepeerd zijn om zo een specifieke taak uit te voeren. Een methode is hetzelfde als een functie, behalve dat methoden worden gemaakt in \(en onderdeel zijn van\) een object.
2. **Objects**: Programmeurs gebruiken objecten om modellen van te maken met behulp van gegevens, en dat deze objecten zijn opgebouwd uit eigenschappen en methoden. Hier wordt nu aangeleerd hoe je eigen objecten maakt met JavaScript.
3. **Ingebouwde objecten**: De browser wordt geleverd met een set objecten die fungeren als een bibliotheek voor het maken van interactieve webpagina's. Er zullen een aantal ingebouwde objecten geïntroduceerd worden.

## Functies

Met functies kunnen een reeks instructies gegroepeerd worden die tot doel hebben een specifieke taak uit te voeren. Als verschillende delen van een script dezelfde taak herhalen kan deze functie opnieuw gebruikt worden \(in plaats van dezelfde reeks elementen te herhalen\).

Code wordt geordend door instructies te groeperen die nodig zijn om een ​​vraag te beantwoorden of een taak uit te voeren. Bovendien worden de instructies binnen een functie niet altijd uitgevoerd wanneer een webpagina wordt ingeladen. Functies kunnen ook stappen opslaan die nodig zijn om een ​​taak te bereiken. Het script kan vervolgens de functie vragen om al stappen uit te voeren wanneer ze specifiek nodig zijn. Een taak moet bijvoorbeeld enkel uitgevoerd worden als een gebruiker op een specifiek element op de pagina klikt. De functie -die een relevante naam krijgt en beschrijft wat de taak uitvoert-  wordt  dan gevraagd om de taak later uit te voeren door het **oproepen van de functie**.   
De stappen die de functie moet uitvoeren om zijn taak te volbrengen, zijn samengevoegd binnen een codeblok. Een codeblok bestaat uit een of meer instructies tussen accolades. 

Voor sommige functies moet de nodige informatie aangereikt worden om een ​​bepaalde taak te bereiken. Om bijvoorbeeld een oppervlakte te berekenen, moeten de **parameters**  breedte en hoogte gekend zijn. Het antwoord -hier de uitgerekende oppervlakte- is de **retourwaarde** \(return value\).

try it yourself \(return\): [https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref\_state\_return](https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_state_return)

### Aanmaken functie

Om een functie aan te maken heeft die eerst een naam nodig om vervolgens de instructies neer te schrijven die nodig zijn om de taak binnen de accolades tot een goed einde te brengen. Dit is het **declareren van een functie**.

```javascript
function sayHello() {
    console.log('Hello!');
}

// function = keyword functie
// sayHello() = naam functie
// console.log('Hello!'); = blok code (tussen accolades)
```

### Aanroepen functie

Als de functie aangemaakt is, kunnen alle instructies tussen de accolades uitgevoerd worden met slechts één lijn code. Dit is het **aanroepen van een functie**.

```javascript
/*1*/ function sayHello() {
/*3*/     console.log('Hello!');
} 
       // code voor hello...
/*2*/ sayHello();
/*4*/ // code na hello...
```

1. De functie slaagt de instructies op voor een specifieke taak.
2. Wanneer je het script nodig hebt om de taak te vervullen, kan de functie aangeroepen worden.
3. De functie voert het blok met code uit.
4. Wanneer de functie uitgevoerd werd, gaat de code verder waar het eerst werd aangeroepen.

### Aanmaken functie met parameters

Soms heeft een functie specifieke informatie nodig om een taak uit te voeren. Bij het declareren van een functie moeten dan **parameters** meegegeven worden \(binnen haakjes\). De parameters worden binnen de functie gebruikt als variabelen.

```javascript
function getArea(width, height) {
    return width * height;
}
```

### Aanroepen functie met parameters

Bij het aanroepen van een functie met parameters moeten de waarden achter de naam van de functie tussen haakjes komen te staan. Deze waarden zijn **argumenten** en kunnen zowel als **waarden**, als **variabelen** gebruikt worden.

```javascript
// argumenten als waarden
getArea(3, 5);
```

```javascript
// argumenten als variabelen
wallWidth = 3;
wallHeight = 5;
getArea(wallWidth, wallHeight);
```

### Eén waarde als resultaat

```javascript
function calculateArea(width, height) {
    let area = width * height;
    return area;
}
// muur 1 = 15
let wallOne = calculateArea(3, 5);
// muur 2 = 40
let wallTwo = calculateArea(8, 5);
```

### Meerdere waarden als resultaat

Functies kunnen meer dan één waarde geven door het gebruik van arrays. In onderstaand voorbeeld berekent de functie zowel de omtrek als oppervlakte van een volume.

```javascript
function getSize(width, height, depth) {
    let area = width * height;
    let volume = width * height * depth;
    let sizes = [area, volume];
    return sizes;
}
let areaOne = getSize(3, 2, 3)[0];
let volumeOne = getSize(3, 2, 3)[1];
```

### Anonieme functies en functie expressies

Expressies hebben een waarde als resultaat. Ze kunnen gebruikt worden waar waarden verwacht worden. Als een functie gebruikt wordt waar de browser een expressie verwacht, zal deze ook als een expressie behandeld worden.

#### functie declareren \(aanmaken\)

Bij het declareren van een functie wordt er een functie gecreëerd die later kan aangeroepen worden in de code. Om dit te kunnen doen, heeft de functie een naam nodig, en is dus een **naam functie**.

```javascript
function area(width, height) {
    return width * height;
};
let size = area(3, 4);
```

#### functie expressie

Als een functie gebruikt wordt waar de browser een expressie verwacht, zal deze ook als een expressie behandeld worden. In zulke functie expressies ontbreekt de naam meestal en worden zodoende **anonieme functies** genoemd. 

```javascript
// Hier wordt de functie opgeslagen in een variabele, area genaamd.
let area = function(width, height) {
    return width * height;
};
let size = area(3, 4);
```

### Onmiddellijk oproepen van functie expressies

```javascript
// De () net achter de laatste accolade van de blok code zorgt ervoor dat de functie direct wordt opgeroepen.

let area = (function() {
    let width = 3;
    let height = 2;
    return width * height;
}());
```

### Variabel bereik \(scope\)

De locatie waar de variabele gedeclareerd wordt, bepaald waar deze variabele gebruikt kan worden in de code. Als de variabele wordt gedeclareerd binnenin een functie, kan die enkel gebruikt worden binnen deze functie zelf. Dit is het **variabele bereik of scope**.

```javascript
//area = lokaal of bereik functie-niveau
function getArea(width, height) {
    let area = width * height;
    return area;
}
// wallSize = globaal bereik
let wallSize = getArea(3, 2);
console.log(wallSize);
```

### Hoe werken geheugen en variabelen?

In JavaScript wordt data weergegeven door gebruik te maken de combinatie naam & waarde. Om deze data te kunnen ordenen, kan gebruik gemaakt worden van een array of object om een reeks gerelateerde waarden te groeperen.In arrays en objecten wordt de naam ook wel sleutel genoemd.

#### variabelen

Een variabele heeft **één key** \(= de variabele naam\) en **één waarde**.   
****Om de waarde van de variabele te bekomen wordt de naam gebruikt.

```javascript
let hotel = 'Quay';
// De uitkomst is Quay
hotel; 
```

#### arrays

Arrays kunnen meerdere stukjes informatie opslaan. Elk stukje informatie wordt gescheiden door een komma. De volgorde van de waarden is belangrijk, omdat aan items in een array een nummer wordt toegewezen \(een **index** genoemd\). Waarden in een array worden tussen **vierkante haken** geplaatst, gescheiden door komma's:

```javascript
let hotels = [
    'Quay',
    'Park',
    'Beach',
    'Bloomsbury'
]
// De uitkomst is Park
hotels[1];
```

#### individuele objecten

Hier is de volgorde niet van belang \(bij een array wel\), want de gegevens worden door de naam aangeroepen. Objecten met een letterlijke notatie worden aangemaakt wanneer:

* gegevens tussen applicaties moeten opgeslagen of doorgegeven worden
* voor het configureren van objecten omtrent informatie op een pagina

```javascript
let hotel = {
    name: 'Quay',
    rooms: 40
};

// De uitkomst is Quay
hotel.name;
```

#### meerdere objecten

Objecten met een constructor notatie worden aangemaakt wanneer:

* er veel objecten gebruikt worden met vergelijkbare functionaliteit \(bijv. meerdere fotogallerijen of mediaspelers\) binnen een pagina
* een complex object mogelijk niet gebruikt wordt in code

```javascript
// aanmaken van een template
function Hotel(name, rooms) {
    this.name = name;
    this.rooms = rooms;
}

let hotel1 = new Hotel('Quay', 40);
let hotel2 = new Hotel ('Park', 120);

// De uitkomst is Park
hotel2.name;
```

#### conflicten door naamgeving



## Wat is een object?

Objecten groeperen een set van variabelen en functies om een ​​model te maken van iets dat in de reële wereld herkend zou worden. In een object krijgen variabelen en functies nieuwe namen.

**In een object worden variabelen gezien als eigenschappen \(properties\)**. Als een variabele deel uitmaakt van een object, wordt het een eigenschap genoemd. Eigenschappen vertellen ons iets over het object, zoals de naam van een hotel of het aantal kamers. Zo heeft elk individueel hotel mogelijk een andere naam en een ander aantal kamers.

**In een object worden functies gezien als methoden**. Als een functie deel uitmaakt van een object, wordt dit een methode genoemd. Methoden vertegenwoordigen taken die aan het object gekoppeld  zijn. Zo kan er bijvoorbeeld gecontroleerd worden hoeveel kamers er beschikbaar zijn door het aantal geboekte kamers af te trekken van het totale aantal kamers.

### Maken object met eigenschappen & methodes

### &gt; letterlijke notatie: maken object

De letterlijke notatie is de gemakkelijkste en meest populaire manier voor het aanmaken van objecten.

```javascript
// object = hotel
let hotel = {
// properties (eigenschappen): deze zijn variabelen, telkens gescheiden door een komma
    name: 'Quay',
    rooms: 40,
    booked: 25,
    gym: true,
    roomTypes: ['twin', 'double', 'suite'],
// methode: dit is een functie
checkAvailability: function() {
    return this.rooms - this.booked;
    }
};   

let elName = document.getElementById('hotelName');
elName.textContent = hotel.name;

let elRooms = document.getElementById('rooms');
elRooms.textContent = hotel.checkAvailability();
```

#### properties

| key | value |
| :--- | :--- |
| name | string |
| rooms | number |
| booked | number |
| gym | boolean |
| roomTypes | array |

#### methodes

| key | value |
| :--- | :--- |
| checkAvailability | functie |

### &gt; dot-notatie: toegang tot object

Door het gebruik van dot-notatie krijg je toegang tot de properties \(eigenschappen\) en methodes van een object.

```javascript
//object = hotel
// . = member operator
// property = name
// methode naam = checkAvailability()
let hotelName = hotel.name;
let roomsFree = hotel.checkAvailability();
```

Je kan ook toegang krijgen tot de properties van een object \(maar niet de methode\) door gebruik te maken van vierkante haakjes.

```javascript
let hotelName = hotel['name'];
```

### &gt; object constructor notatie: maken object

Er wordt er een nieuw object aangemaakt. De syntax voor het toevoegen en verwijderen, van eigenschappen en methodes van dat object is hetzelfde als bij de letterlijke notatie.

```javascript
let hotel = new Object();
// properties    
hotel.name = 'Quay';
hotel.rooms = 40;
hotel.booked = 25;
// method
hotel.checkAvailability = function() {
    return this.rooms - this.booked;
};
```

### Object updaten

```javascript
//object = hotel
// . = member operator
// property name = name
// = assignment operator
// property value = Park
hotel.name = 'Park';

hotel['name'] = 'Park';

delete hotel.name;
hotel.name = '';
```

### Constructor notatie: maken meerdere objecten

Soms is het handig dat verschillende objecten soortgelijke dingen vertegenwoordigen. Objectconstructoren kunnen een functie gebruiken als sjabloon voor het maken van objecten. Maak hiervoor eerst een sjabloon met de eigenschappen en methoden van het object.

Een functie Hotel zal wordt gebruikt als een sjabloon voor het maken van nieuwe objecten die hotels in het algemeen vertegenwoordigen. Zoals alle functies bevat het instructies. In dit geval worden eigenschappen of methoden toegevoegd aan het object.  
De functie heeft drie parameters. Elke parameter staat voor de waarde van een eigenschap binnen het object. De methoden zijn voor elk object hetzelfde, gemaakt met deze functie.  
Het **sleutelwoord this** wordt gebruikt in plaats van de objectnaam om aan te geven dat de eigenschap of methode behoort tot het object dat _this_ functie maakt.

```javascript
function Hotel(name, rooms, booked) {
// properties
this.name = name;
this.rooms = rooms;
this.booked = booked;
// method
this.checkAvailability = function() {
    return this.rooms - this.booked;
};
```

```javascript
// object = quayHotel, parkHotel
// =  = assignment operator
// new = new keyword
// constructor functie = Hotel('Quay', 40, 25) & Hotel('Park', 120, 77)
// waarden van eigenschappen binnen object = 'Quay', 40, 25 & 'Park', 120, 77
let quayHotel = new Hotel('Quay', 40, 25);
let parkHotel = new Hotel('Park', 120, 77);
```

```javascript
// Create the template for objects that are hotels
function Hotel(name, rooms, booked) {
  this.name = name;
  this.rooms = rooms;
  this.booked = booked;
  this.checkAvailability = function() {
    return this.rooms - this.booked;
  };
}

// Create two hotel objects
let quayHotel = new Hotel('Quay', 40, 25);
let parkHotel = new Hotel('Park', 120, 77);

// Update the HTML for the page
let details1 = quayHotel.name + ' rooms: ';
    details1 += quayHotel.checkAvailability();
let elHotel1 = document.getElementById('hotel1');
elHotel1.textContent = details1;

let details2 = parkHotel.name + ' rooms: ';
    details2 += parkHotel.checkAvailability();
let elHotel2 = document.getElementById('hotel2');
elHotel2.textContent = details2;
```

### Arrays in object & objecten in array

### &gt; arrays in een object

| property | value |
| :--- | :--- |
| room1 | items\[420, 40, 10\] |
| room2 | items\[460, 20, 20\] |
| room3 | items\[230, 0, 0\] |
| room4 | items\[620, 150, 60\] |

```javascript
costs.room1.items[0];
```

### &gt; objects in een array

| index nummer | value |
| :--- | :--- |
| 0 | {accom:420, food:40, phone:10} |
| 1 | {accom:460, food:20, phone:20} |
| 2 | {accom:230, food:0, phone:0} |
| 3 | {accom:620, food:150, phone:60} |

```javascript
costs[2].phone;
```

