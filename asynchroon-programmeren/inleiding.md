# inleiding

Hieronder zullen een aantal belangrijke concepten besproken worden met betrekking tot asynchroon programmeren en hoe dit eruit ziet in zowel webbrowsers als JavaScript.

Veelal wordt programmeercode voor een bepaald programma zo geschreven dat deze rechtdoor gaat, waarbij er telkens maar één ding tegelijkertijd gebeurt. Als een functie afhankelijk is van het resultaat van een andere functie, moet deze wachten tot de andere functie voltooid is en totdat gebeurt, wordt het hele programma in wezen gestopt vanuit het perspectief van de gebruiker.  
Daarom krijgen Mac-gebruikers zo nu en dan de ronddraaiende regenboogkleurige cursor of kleine cirkel te zien. Het besturingssysteem geeft met deze cursor aan dat het huidige programma dat gebruikt wordt, moet stoppen en eerst moet wachten tot er iets anders afloopt \(soms helaas een vrije interpretatie van "Het huidige programma loopt vast. Help!"\).

Dit is een frustrerende ervaring en al zeker geen optimaal gebruik van de verwerkingskracht van de computer, waarvan de meeste tegenwoordig over meerdere processorcores beschikken. Het heeft geen enkele zin om te wachten als een andere taak door een andere processorkern kan uitgewerkt worden. Ondertussen kan er ander werk verricht worden, wat de basis is van **asynchroon programmeren**. In het geval van webbrowsers en  webontwikkeling is het aangewezen om API's aan te bieden waarmee dergelijke taken asynchroon kunnen uitgevoerd worden.

