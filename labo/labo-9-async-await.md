# labo 9: Async/await

### 1. Maak het project aan

Open Visual Studio Code en open een nieuwe folder voor het project. Test dat je in de juiste folder zit door 

```text
pwd
```

te typen in de Terminal. Maak een nieuwe npm-package met bijbehorende package.json door 

```text
npm init
```

te doen. De default waarden zullen hier voldoende zijn.

### **2. Slechte moppen**

Maak een bestand `jokes.js` aan. 

We gebruiken in dit labo de volgende API call

```text
https://icanhazdadjoke.com/search?term=dog&limit=5&page=1
```

belangrijk voor deze opdracht zijn de volgende query parameters:

* **term:** de zoekterm \(dus in ons geval dog\)
* **limit:** het aantal zoekresultaten per pagina. **Voor deze oefening is dit verplicht op 5!**
* **page:** de huidige pagina.

Om de resultaten in JSON te krijgen moet je de fetch call doen met een extra parameter:

```text
fetch('https://icanhazdadjoke.com/search?term=dog&limit=5&page=1', {
   headers: {
     'Accept': 'application/json'
   }
})
```

Gebruik de bovenstaande API call om alle moppen op het scherm te laten zien waar het woord 'dog' in voor komt. Je begint op de eerste pagina, en dan laad je de volgende in, en dan de volgende,... tot er geen moppen meer zijn.

**Opgelet:** In dit labo is het verplicht om de **async/await** werkwijze te gebruiken. 

**Verwachte output:**

```text
Me: If humans lose the ability to hear high frequency volumes as they get older, can my 4 week old son hear a dog whistle?

Doctor: No, humans can never hear that high of a frequency no matter what age they are.

Me: Trick question... dogs can't whistle.
Why did the cowboy have a weiner dog? Somebody told him to get a long little doggy.
I adopted my dog from a blacksmith. As soon as we got home he made a bolt for the door.
“My Dog has no nose.” “How does he smell?” “Awful”
what do you call a dog that can do magic tricks? a labracadabrador
My dog used to chase people on a bike a lot. It got so bad I had to take his bike away.
What did the dog say to the two trees? Bark bark.
I went to the zoo the other day, there was only one dog in it. It was a shitzu.
What kind of dog lives in a particle accelerator? A Fermilabrador Retriever.
At the boxing match, the dad got into the popcorn line and the line for hot dogs, but he wanted to stay out of the punchline.
It was raining cats and dogs the other day. I almost stepped in a poodle.
What did the Zen Buddist say to the hotdog vendor? Make me one with everything.
```

### 3. Een bestand lezen

Maak een bestand `read_file.js` aan met de volgende inhoud. Dit stuk code zal een bestand uitlezen van het file systeem en dit uitprinten op het scherm.

```javascript
var fs = require('fs');
 
fs.readFile('email.txt', 'utf8', function(err, contents) {
    console.log(contents);
});
```

Maak een bestand aan `email.txt` en zet daar in je AP email adres en NIETS anders. bijvoorbeeld:

```text
joske.vermeulen@student.ap.be
```

1. Probeer eerst of deze code werkt!
2. Maak  in `read_file.js` een functie `readFile` aan met een parameter filename die een Promise teruggeeft die het bovenste stuk code gebruikt om een file te lezen. Roep de `resolve` functie aan als de file kan gelezen worden \(dus als `err` leeg is\) en `reject` functie als er een error is. 
3. Roep deze functie aan met als argument het email.txt bestand. Maak gebruik van het **await** keyword.



