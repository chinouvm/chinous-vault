# PPDIOO: Design
___
## Technisch Ontwerp
**Generator**
De willekeurige nummer- en letterreeksen worden gegenereerd op basis van een camera die een snelweg filmt en zo de auto’s gebruikt om nullen of enen te generen.
Deze nullen en enen worden gebruikt om verschillende soorten reeksen te genereren.
Voor het wachtwoord worden deze nullen en enen gebruikt om in een loop een willekeurig karakter uit een lijst te pakken en samen te voegen tot een zestienkarakter wachtwoord.
Voor de Salts en encryptie worden de nullen en enen gebruikt om willekeurige getallen te genereren tussen de 0 en 255.

De nullen en enen worden d.m.v. een aantal pseudorandom generators gegenereerd, maar wat de generator nu echt wiskundig correct willekeurig maakt, is het feit dat het aantal pseudorandom generators afhankelijk is van het aantal auto’s in het frame.
Als er vijf auto’s zijn dan worden er vijf pseudorandom reeksen gegenereerd van nullen en enen van een lengte tussen de 8 en de 16. Uiteindelijk wordt van deze vijf reeksen de modus gepakt (het meest voorkomende getal) en dat is het echte willekeurige getal.

*Techologies:*
De generator wordt gemaakt in de programmeertaal [Python](https://www.python.org/). Ik heb voor deze taal gekozen omdat ik graag het detecteren van auto’s in een frame wil doen met de [OpenCV](https://opencv.org/) Library en die is voornamelijk gericht op [Python](https://www.python.org/).

**Database**
Omdat mijn manier van het generen van nullen en enen niet enorm snel is, moet ik een buffer hebben zodat gebruikers altijd wanneer het nodig is een willekeurige getallenreeks kunnen generen. Hiervoor gebruik ik een database. De generator draait continue op de achtergrond en upload zijn gegenereerde reeksen naar de database.
De API en de website halen de data uit de database om zo aan de gebruiker te geven.
Deze database draait op het Google Cloud Platform en is dus al voor een groot deel beveiligd. Zelf zijn er database rules die ervoor zorgen dat de database nog extra beveiligd wordt en deze ga ik daarom dus ook zeker aanpassen naar mijn wens.

**De API**
De API die voornamelijk gebruikt gaat worden door ontwikkelaars haalt de verschillende soorten getallen en letterreeksen uit de database zodat deze overal gebruikt kunnen worden waar de ontwikkelaar dat wil.

*Auth0*
Om de API te beveiligen is het een mogelijkheid om een ‘Bearer’ token toe te voegen. Deze token zorgt ervoor dat alleen mensen met een geldige token toegang hebben tot bepaalde ‘endpoints’ in de API. Auth0 is een eenvoudig te implementeren, aanpasbaar authenticatie- en autorisatieplatform die voor mij de zogenaamde ‘Bearer’ tokens genereert en controleert of deze geldig zijn. Via de Auth0 API kan ik tokens opvragen die ik vervolgens weg kan geven aan gebruikers die verbonden zijn met mijn API. Als extra beveiliging hebben deze tokens ook nog een geldigheidsduur van 30 dagen.

*Technologies*
De (REST) API wordt gemaakt in de programmeertaal Python met de library FastAPI.
Hier heb ik voor gekozen omdat ik FastAPI na ervaring fijner vind werken dan de alternatieven libraries (Flask). Met FastAPI kan ik een veilige, stabiele en snelle API bouwen.
FastAPI is wordt niet alleen door mij gekozen in plaats van Flask en Django. Zo staat FastAPI op plek 247 in de techempower framework benchmarks terwijl Flask op plek 315 staat en Django op plek 359 (Benchmarks, 2021).

**Website**
De website is bedoeld voor de gewone gebruiken en dient eigenlijk als een soort demo van EsieRNG. De website heeft verschillende onderdelen zoals: de wachtwoord generator en API-token generator.

*Technologies*
De website wordt gebouwd met [React](https://reactjs.org/). React is een Javascript framework waarmee je krachtige webapps kan bouwen. De reden dat ik React heb gekozen in plaats van de andere frameworks is omdat ik na flink wat ervaring in het maken van webapps heb gezien dat na een hoop components zoals footers, navbars etc, je directories toch heel erg rommelig zijn. Hierdoor wordt het lastig om de code netjes en leesbaar te houden. React heeft hier manieren voor dat het overzichtelijk blijft zoals ‘Auto-Imports’. Auto-imports zorgt ervoor dat je geen componenten hoeft te importeren en gewoon overal in jouw project kan gebruiken. Een andere reden is dat React een enorm grote community heeft. Deze community maakt enorm veel handige tools en uitbreidingen die ik dan weer kan gebruiken in mijn website, zoals [react-toastify](https://www.npmjs.com/package/react-toastify).

**Demo**
Om te laten zien hoe mijn API en Website gebruikt kan worden om verschillende systemen te beveiligen, maak ik een klein netwerkje.

| **Device/Service** | **IP**         |               |
| ------------------ | -------------- | ------------- |
| Router             | WAN: NETLAB IP | LAN: 10.0.0.1 |
| Database Server    | 10.0.0.2       |               |
| Pterodactyl Server | 10.0.0.3       |               |
| Generators Server  | 10.0.0.4       |               |
|                    |                |               |


![[Pasted image 20220707220658.png|500]]
*Figuur 7: Dataflow Diagram van de verschillende locaties en applicaties.*

***Probleemmanagement flow**
![[Pasted image 20220707220811.png|200]]
Figuur 8: De flow van hoe github issues aangepakt worden

![[Pasted image 20220707220852.png]]
*Figuur 9: Netwerk tekening incl. cloud services.*
