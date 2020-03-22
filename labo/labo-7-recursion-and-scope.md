# labo 7: recursion and scope

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

### **2. Scope + Recursie: Som**

maak een bestand `sum.js` met de volgende inhoud:

```javascript
let sum = (n) => {
    sum = 0;
    for (i=0;i<=n;i++) {
        sum += i;
    }
    return sum;
}
```

**Opdracht:** Geef de output van de volgende statements zonder deze echt uit te voeren

```text
console.log(sum(2));
```

```text
console.log(i);
```

```text
console.log(sum(2));
```

**Let op:** De laatste wordt een 2de keer uitgevoerd. Dit is **geen vergissing**!

**Opdracht:** Herschrijf nu deze functie door gebruik te maken van recursie.

### **3.** Recursie: Spaces

Maak een bestand `spaces.js` met de volgende inhoud: 

```javascript
const spaces = (n) => {
    let spaces = '';
    for (let i=0;i<n;i++) {
        spaces += ' ';
    }
    return spaces;
}
```

De bovenstaande functie neemt een argument n aan en geeft als return waarde een string terug met n aantal spaties.

**Voorbeeld gebruik:**

```javascript
console.log(spaces(5) + 'Hey');
     Hey
console.log(spaces(10) + 'Hey');
          Hey
```

**Opdracht:** Herschrijf deze functie zodat ze recursie gebruikt.

### 4. Recursie: faculteit

Maak een bestand `faculteit.js` met de volgende inhoud: 

```javascript
const faculteit = (n) => {
    if (n === 0 || n === 1) {
        return 1;
    }
    for (let i=n-1;i>0;i--) {
        n=n*i;
    }
    return n;
}
```

De bovenstaande functie berekent de faculteit van het getal n.   
Kijk op https://www.wisfaq.nl/showfaq3.asp?id=19971 als je niet weet wat een faculteit is.

**Voorbeeld gebruik:**

```javascript
console.log(factorial(1));
1
console.log(factorial(5));
120
```

**Opdracht:** Herschrijf deze functie zodat ze recursie gebruikt.

### 5. Recursie: som van een array

Maak een bestand `arraysum.js` met de volgende inhoud: 

```javascript
const sum = (arr) => {
    let s = 0;
    for (let i=0;i<arr.length;i++) {
        s += arr[i];
    }
    return s;
}
```

De bovenstaande functie geeft de som van een array met getallen

**Voorbeeld gebruik:**

```javascript
let array = [1, 2, 3, 4, 5, 6]
console.log(sum(array));
21
```

**Opdracht:** 

* Herschrijf deze functie zodat ze recursie gebruikt.
* **Extra:** herschrijf deze functie gebruikmakende van de reduce functie uit vorig labo




