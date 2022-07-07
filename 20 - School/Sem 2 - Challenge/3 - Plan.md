# PPDIOO: Plan
___
## GAP-Analyse
**Gewenste Identiteit**
Het doel van EsieRNG is het leveren van willekeurige cijferreeksen die veilig gebruikt kunnen worden in de cryptografie en alledaagse wachtwoorden. Zo hopen wij in de toekomst de veiligheidsincidenten betreft onveilige encryptieversleuteling te verminderen. EsieRNG is vooral gericht op ontwikkelaars die hun data op een veilige manier willen opslaan, bijvoorbeeld d.m.v. onze Salt generator. Natuurlijk kunnen ook niet-ontwikkelaars van onze diensten gebruik maken om bijvoorbeeld veilige wachtwoorden te genereren.
EsieRNG richt zich op privacy en veiligheid. Zo houden wij geen logboek bij van welke cijferreeksen gebruikt worden door welke gebruiker. Naast het zelf implementeren van deze waarden houden we dit ook altijd als doel van het product: We willen ervoor zorgen dat internetgebruikers en ontwikkelaars zo veilig mogelijk hun werkzaamheden kunnen doen en hun gegevens kunnen beveiligen. Dit is ook onze visie voor de lange termijn: ernaar blijven streven om veiligheid een belangrijk speerpunt te houden.

**Huidige Identiteit**
Om te zorgen dat onze gebruikers zonder frustratie onze diensten kunnen gebruiken zorgen we ervoor dat onze informatievoorzieningen altijd up-to-date zijn en makkelijk te begrijpen zijn. Via GitHub moeten problemen kunnen worden gemeld, waardoor de site en de RNG zonder problemen blijven werken en gebruikers feedback kunnen geven.

**Fysieke Identiteit**
EsieRNG is te herkennen door de blauwe kleur. De blauwe kleur associeert men vaak met bescherming en rust, ook straalt het een technische, formele en zakelijke stijl uit (Ridder, 2015).

**Huidige imago**
Om het imago in kaart te brengen heb ik een kleine enquête gehouden over EsieRNG.
Hierbij heb ik vooral gevraagd naar wat er bij iemand opkomt bij het zien van het logo.
De vraag luidt als volgt: Welke sfeer roept het EsieRNG-logo bij u op?
De enquête is ingevuld door 24 mensen. Hieruit blijkt dat de meesten, maar liefst 50%, vinden dat het logo beschermend overkomt. De overige aangevinkte sferen zijn rustgevend en activerend. Hieruit kan geconcludeerd worden dat de beschermende waarde, wat een van de belangrijkste speerpunten van ESIE is, ook wordt overgedragen via het logo.

![[Pasted image 20220707214021.png|400]]
*Figuur 3: Een cirkeldiagram van de enquête over welke sfeer het ESIE logo oproept. Hieruit blijkt dat de meeste mensen vinden dat het logo beschermend overkomt.*

## SWOT
![[Pasted image 20220707214103.png]]
*Figuur 4: SWOT-analyse die interne en externe bedreigingen in kaart brengt*

## Informatiebeveiliging
Omdat de ontwikkelaars een account nodig hebben om de API te kunnen gebruiken, moeten er bepaalde gegevens van de ontwikkelaar opgeslagen worden. Hierbij is het belangrijk dat bij het opslaan van deze gegevens voldaan wordt aan de AVG (Algemene verordening gegevensbescherming), de wetgeving rondom privacy die in de gehele EU geldt. Over het algemeen geldt dat er zo min mogelijk gegevens moeten worden opgeslagen (AVG, n.d.). Oftewel: alleen de dingen die echt nodig zijn om een bepaalde actie uit te voeren, mogen worden verzameld en gebruikt.

Naast de AVG moet ook voldaan worden aan een aantal punten binnen de informatiebeveiliging.
Een voorbeeld hiervan is de BIV-classificatie (Beschikbaarheid, Integriteit, Vertrouwelijkheid), een methode om aan te duiden hoe veilig informatie in systemen wordt aangegeven (Ministerie van Binnenlandse Zaken en Koninkrijksrelaties, 2012). Dit houdt in dat informatie beschikbaar moet zijn, dat de informatie juist en volledig is (en dat er voorzichtig wordt omgegaan met de opgeslagen informatie), en de mogelijkheid om toegang te krijgen tot informatie die afgesloten is voor derden. Deze classificatie wordt vaak afgebeeld in een driehoeksvorm, omdat het als de drie belangrijkste speerpunten binnen de informatiebeveiliging bevat (Chai, 2021).

Een ander systeem binnen de informatiebeveiliging is RBAC (Role-based access control), wat gebaseerd is op dat individuen niet zomaar autorisatie krijgen in systemen, maar dat ze alleen met een bepaalde rol rechten en toegang krijgen. In mijn geval is dit niet heel relevant, omdat de doelgroep van mijn project heel individueel is, en er daarom niet veel sprake is van groep gerelateerde data en informatie.

![[Pasted image 20220707214523.png|300]]
*Figuur 5: De BIV-classificatie afgebeeld in een driehoek. Samen zorgen de drie principes beschikbaarheid, integriteit en vertrouwelijkheid voor informatiebeveiliging. Afbeelding van (Chai, 2021)*

Naast de BIV-classificatie en het RBAC-systeem is het ook belangrijk om je te houden aan ‘best practices’, wat inhoudt dat, hoewel het niet wettelijk verplicht is, er meer wordt gedaan dan alleen het minimale om een systeem veilig te maken (Ministerie van Binnenlandse Zaken en Koninkrijksrelaties, 2012). Een voorbeeld hiervan is de informatiebeveiliging waar het Rijk gebruik van maakt.
In een rapport, gepubliceerd in 2012, wordt dit op de volgende manier afgebeeld:

![[Pasted image 20220707214553.png|400]]
*Figuur 6: het Rijk maakt gebruik van Best Practice: meer doen dan alleen moet om het systeem zo veilig mogelijk te maken. Afbeelding van (Ministerie van Binnenlandse Zaken en Koninkrijksrelaties, 2012)*

## Risicoanalyse

| **Nr.** | **Bedreiging** | **Availability** | **Integrity** | **Confidentiality** | **Kans (1-5)** | **Impact (1-5)** | **Risco (PxI)** |
| ------- | -------------- | ---------------- | ------------- | ------------------- | -------------- | ---------------- | --------------- |
| 1       | Datalek        | Laag             | -             | Hoog                | 2              | 4                | 8               |
| 2       | Weg afgesloten | Hoog             | -             | -                   | 3              | 4                | 12              |
| 3       | Auth0 Storing  | Hoog             | -             | -                   | 1              | 4                | 4               |
| 4       | Vandalisme     | Hoog             | Hoog          | -                   | 4              | 5                | 20                |

**Risico's**
EsieRNG maakt gebruik van een database als een buffer zodat gebruikers altijd toegang hebben tot gegenereerde sleutels en wachtwoorden. Wanneer deze data openbaar komt te liggen moet de gehele database (buffer) gewist worden en moet de data opnieuw gegenereerd worden. Dit zorgt ervoor dat EsieRNG voor een korte tijd (circa 20min) niet bruikbaar is en daarom wordt de availability voor een korte tijd beperk. Wanneer iemand toegang heeft tot de gehele database is het mogelijk dat deze persoon kan voorspellen welke gebruikers welke sleutels en wachtwoorden krijgen en dat is een heel groot probleem voor de gebruikers die EsieRNG gebruiken, hierdoor is de confidentiality impact hoog.

Omdat EsieRNG het verkeer gebruikt om data te genereren kan het voorkomen dat de weg wordt afgezet voor bijvoorbeeld onderhoud en dat is er een periode dat er geen auto’s over de weg rijden. Als dit gebeurt kunnen er in die periode geen data gegenereerd worden omdat er geen beweging op de camera’s te vinden is en hierdoor raakt de buffer snel op en kunnen gebruikers al snel geen gebruik meer maken van EsieRNG.

Auth0 zorgt ervoor dat alleen gebruikers met de juiste API-token de API kunnen gebruiken. Wanneer hier een storing is bij de authenticatie servers kunnen de gebruikers zich niet meer autoriseren via de API-token en kunnen zij geen gebruik maken van de EsieRNG API.

Omdat er een camera met een kastje ergens boven een snelweg hangt kan het voorkomen dat deze gevandaliseerd wordt. Wanneer dit kastje kapot is kan het zijn dat het kastje nog wel data genereerd maar omdat de camera kapot kan zijn wordt deze data gegenereerd op basis van foutieve data. Ook kan het zijn dat het gehele kastje niet meer werkt en dus niet meer de buffer bij kan vullen.

![[ECYgAIb.png]]
![[xCMQpCp.png]]

## Specificaties en Dataopslag
De enige specificatie die het programma moet hebben is voldoende snelheid om een video frame na frame te analyseren op beweging en dat lukt met python. C++ zou een andere optie zijn als het programma uiteindelijk te traag wordt na het toevoegen van nieuwe features. De data wordt opgeslagen in een Google Cloud Database genaamd Firestore. Firestore is een NoSQL database en makkelijk te gebruiken in de meeste moderne programmeertalen.

## Resource Analyse
Het kost EsieRNG weinig tot geen resources om alle diensten te draaien.
De website, API en database worden gehost door verschillende cloud providers en zijn voor ons op het moment gratis. De kosten kunnen uiteindelijk oplopen als de website en API heel veel internetverkeer krijgt. De kosten zitten dan na een systeemupgrade rond de 15 euro per maand totaal. Op dit moment kost alleen het domein esie.nl 7 euro per jaar.
___


