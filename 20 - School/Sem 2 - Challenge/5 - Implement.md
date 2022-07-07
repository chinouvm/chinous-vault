# PPDIOO: Implement
___
## Implementatieplan

**Service-level agreement**
SLA: De gebruiker moet altijd sleutels kunnen laten genereren voor gebruik.
SLO: De generators moeten genoeg data genereren om te zorgen dat de gebruiker altijd sleutels kan genereren.
SLI: De generators hoeven niet constant te genereren omdat na monitoring blijkt dat het lang duurt voordat de buffers leeg zijn.

SLA: Alle diensten die de klant gebruikt moeten een uptime hebben van 99%
SLO: Alle diensten die de klant gebruikt moeten een uptime hebben van 99.4%
SLI: Alle diensten die de klant gebruikt moeten een uptime hebben van 99.3%

**Beveiliging tests en het nastreven van de AVG**
EsieRNG maakt gebruik van het feit dat mensen kunnen inloggen met hun Google Account.
Hierdoor zijn de inloggegevens veilig opgeslagen door Google en hoeft EsieRNG zich daar geen zorgen over te maken. Bij het inloggen via Google krijgt elke gebruiker wel een uniek ID en zo kan EsieRNG bijhouden wie de API gebruikt of misbruikt. Alleen dit wordt opgeslagen om te voldoen aan de AVG, die, zoals eerder beschreven, eist dat alleen de écht nodige gegevens worden opgeslagen.

Om ervoor te zorgen dat EsieRNG voldoet aan de eerder beschreven voorwaarden, voer ik een aantal tests uit.
Ten eerste ga ik ervoor zorgen dat je geen API-token kunt krijgen zonder eerst in te loggen met je Google Account. Zoals ik eerder beschreven heb, hebben de ontwikkelaars dit nodig, maar natuurlijk moet er wel getest om te kijken dat dit daadwerkelijk werkt.
Door ervoor te zorgen dat de ontwikkelaars moeten inloggen, is het duidelijk wie de API gebruikt en wordt het risico van een robot die de API misbruikt kleiner.

Daarnaast test ik dat er alleen Salts en aes128 sleutels gegenereerd kunnen worden met een geldige API-token. Als dit niet het geval geweest zou zijn, zou dit betekenen dat alle endpoints omzeild konden worden en dat een account dus überhaupt niet nodig zou zijn voor het genereren van Salts en aes128.

**Github**
Alle code die geschreven wordt komt op GitHub en heeft zo dus automatisch een versiebeheer. De commits krijgen een goede omschrijving en de gebruiker kan zelf bugs melden of verbeteringen via het GitHub Issue Systeem. Verder worden er geen releases uitgebracht omdat EsieRNG geen programma is wat gedownload hoeft te worden. Tenslotte kan de gebruiker zelf het proces inzien via GitHub Projects waar alle GitHub issues gecategoriseerd worden op prioriteit.

**Systeemintegratietest (SIT)**
Na het ontwikkelen van de API, Website en Generators worden deze getest op verschillende systemen. Het is namelijk belangrijk dat de producten werken op alle apparaten waar een ontwikkelaar mee werkt, zo wordt de website getest op verschillende schermresoluties en de API wordt getest met verschillende programmeertalen.

**Generators**
Bij het maken van de generators is het belangrijk dat het programma niet te langzaam wordt. Als het programma te langzaam wordt dan wordt er niet genoeg data gegeneerd om sleutels te genereren.
Hierbij is het belangrijk om in Python te zorgen dat de stappen de soorten generators in verschillende scripts worden onderverdeeld zodat deze niet allemaal dezelfde onnodige stappen door hoeven te lopen. Als het programma uiteindelijk toch te traag wordt is het nog altijd mogelijk om de generators te maken in C++. C++ heeft het voordeel dat het veel sneller is dan Python, maar het is ook een stukje lastiger.

Als de generators klaar zijn worden ze per script in een docker container op het netlab gehost zodat deze ongehinderd kunnen genereren.
Met het onderverdelen in script bedoel ik dat ik het stuk code wat verantwoordelijk is voor de wachtwoorden en het stuk code wat verantwoordelijk is voor de Salts afgezonderd in aparte Python bestanden zet.

**API**
De API wordt gemaakt met Python FastAPI. Ik wil het graag in Python maken omdat ik graag bekend wil raken met de FastAPI web framework. FastAPI is een modern en snel web framework voor het maken van API’s. FastAPI is niet alleen supersnel maar heeft ook een hele hoop mogelijkheden om je API te beveiliging met bijvoorbeeld een Bearer Token.
Een Bearer token is precies wat ik nodig heb om mijn API goed te beschermen en alleen toegang aan gebruikers te geven die een account hebben op de website.
Een alternatief voor FastAPI & Python is Golang. Als FastAPI niet helemaal goed uitpakt kan ik nog altijd de API schrijven in Golang dus dat is mijn plan B.

De API Bearer Tokens worden gecontroleerd en gegenereerd door Auth0. Zoals eerder vermeld is Auth0 een eenvoudig te implementeren, aanpasbaar authenticatie- en autorisatieplatform. Auth0 zorgt ervoor dat ik tokens kan genereren voor mijn gebruikers en dat deze tokens gecontroleerd worden bij elke API Request.
Als de API dan uiteindelijk klaar is host ik deze op Deta.sh. Deta.sh is een cloud provider en een van de sponsoren van FastAPI dus het hosten van FastAPI applicaties is perfect op Deta.sh.
Deta.sh heeft environment mogelijkheden dus zo kan ik mijn database keys en Auth0 keys veilig opslaan.

**Website**
De website is niet heel gecompliceerd. Het heeft een inlogfunctie via Google, een kleine demo om wachtwoorden te generen en een mogelijkheid om Bearer Tokens te genereren.
Omdat ‘niet heel gecompliceerd’ niet hetzelfde is als lelijk ben ik wel van plan om de website mooi aan te kleden d.m.v. CSS.

De website wordt gebouwd met het React.js framework. Ik gebruik React.js omdat dit framework de grootste community heeft, daarom hoef ik mij geen zorgen te maken als ik ergens tegenaanloop omdat er vast en zeker ergens een oplossing te vinden is gemaakt door community.

Als de website klaar is wordt deze gehost door Netlify. Netlify is een cloud provider gespecialiseerd in het hosten van website gemaakt met een javascript framework zoals React. Netlify biedt de mogelijkheid om een eigen domeinnaam toe te voegen en om environment variables te gebruiken zodat ik op een veilige manier mijn database gegevens kan opslaan.

**Demo**
Om EsieRNG in actie te laten zien, ben ik van plan om een kleine demo te maken in het Netlab.
Deze demo bestaat uit een database en een gameserver die beveiligd wordt via EsieRNG.
Ik maak een klein Python programma dat aan de gebruiker vraagt om een account aan te maken. Deze gegevens worden dan opgeslagen d.m.v. hashing met een Salt gegenereerd door EsieRNG.
De gegevens worden daarna veilig opgeslagen in de database die beveiligd is met een sterk wachtwoord, ook gegenereerd door EsieRNG.
De gameserver draait een paneel genaamd Pterodactyl. Pterodactyl is een open-source game server beheer paneel waarmee ik verschillende soorten gameservers kan aanmaken voor verschillende games. Pterodactyl werkt met administrator accounts en gebruiker accounts en het is belangrijk dat deze accounts goed beveiligd worden met een sterk wachtwoord. Anders kan het voorkomen dat het administrator account overgenomen wordt door iemand die er eigenlijk helemaal niet thuishoort.
___
