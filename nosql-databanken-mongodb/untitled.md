# MongoDB

## NoSQL vs relationele DB

### NoSQL database

**MongoDB** is een **NoSQL-database** \(Not Only SQL\), eentje die **SQL vermijdt**. Het SQL-systeem wordt ter ondersteuning gebruikt, maar niet actief bij het verwerken van verzoeken. Dit soort databases kan daarom ingezet worden bij grote hoeveelheden van gegevens.  
In een NoSQL-database wordt aan een rij slechts een enkele kolom gelinkt. Alle entry’s voor een rij worden gegroepeerd in dezelfde kolom, waardoor plaats bespaard wordt. Door het grote volume aan data zijn koppelingen als JOIN \(vrijwel\) onhaalbaar.  
**Data** wordt opgeslagen als **'documents' / JSON.** Het is **dynamische data** waarvan de **structuur aanpasbaar** is en bepaald wordt tijdens de ontwikkeling. NoSQL-databases kunnen gebruikt worden voor **simpele queries**.

```javascript
[
    {
        firstname: 'Sven',
        lastname: 'Charleer',
        email: 'sven.charleer@ap.be'
    },
    {
        firstname: 'Andie',
        lastname: 'Similon',
        email: 'andie.similon@ap.be'
    },
]
```

### relationele DB

Op het eerste gezicht lijkt een relationele database eerder een platte database. Het verschil zit in de tabellen die niet op zichzelf staan. **Data** zit verspreid over **meerdere tabellen** binnen een  database,  waarbij de tabellen aan elkaar gekoppeld kunnen worden met JOIN.   
Een relationele database is een prima oplossing voor **gestructureerde data**, waarbij de **structuur** nadien **moeilijk aanpasbaar** is en daarom op voorhand bepaald dient te worden. Vanwege de opbouw kunnen **ingewikkelde queries** op dit soort databanken losgelaten worden.  
vb. relationele database **MySQL**: Zo kan een bepaalde klas uit een tabel klassen, weer verwijzen naar een uurrooster, dan weer gekoppeld aan klaslokalen en een groep studenten.

| firstName | lastName | email |
| :--- | :--- | :--- |
| Sven | Charleer | sven.charleer@ap.be |
| Andie | Similon | andie.similon@ap.be  |

### NoSQL vs relationele DB

| relationele DB | NoSQL |
| :--- | :--- |
| record in RDB | MongoDB's document \(JSON-object\) |
| tabel in RDB | MongoDB's collection |
| \_id is unieke identifier \(indexed\)\) voor elk document | document wordt binair bijgehouden \(BSON\) |

## using MongoDB in NodeJS

{% embed url="https://www.youtube.com/watch?v=ayNI9Q84v8g" %}





  
  


### connecting to MongoDB





### listing databases





### closing connection





## playing with data



  


### choosing your database and collection





## create





## read



## update

 

## delete





