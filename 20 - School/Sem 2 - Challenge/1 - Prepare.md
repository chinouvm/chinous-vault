# PPDIOO: Prepare
___
## Functioneel Ontwerp
### Inleiding
In het programmeren wordt vaak gebruik gemaakt van random getallen om bijvoorbeeld sleutels te generen voor bepaalde apps. Deze sleutels zijn vaak niet veilig omdat ze met een zogenaamde ‘pseudorandom algoritme’ gemaakt zijn. De sleutels zijn daarom een stuk minder veilig omdat ze d.m.v. wiskunde voorspeld kunnen worden.
Dit fenomeen wordt ook waargenomen door de ‘random password generators’ die bijvoorbeeld zijn ingebouwd in de meeste operating systems en/of browsers.
Om dit te ontwijken bestaan er zogeheten ‘true random generators’ die dus op een willekeurige manier op basis van externe factoren nummers generen. 
Mijn challenge is daarom ook om een tool te maken die developers en normale gebruikers kunnen gebruiken in het generen van getallen- en letterreeksen.


| **Must have**                                                                                                                                                                                                       | **Should have**                                                                                        | **Would have**                                                     | **Won't Have** |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------ | -------------- |
| Er moet altijd voldoende data gegenereerd zijn zodat de gebruiker altijd zijn/haar sleutels kan verkrijgen, De API endpoints moeten beveiligd zijn zodat alleen gebruikers met een account de API kunnen gebruiken. | De gebruiker kan verschillende API endpoints gebruiken om verschillende soorten sleutels te genereren. | API Sleutels verlopen niet na 30 dagen maar zijn account gebonden. | Gebruikers kunnen via REST een API-sleutel opvragen.               |


### Het plan
Mijn challenge bestaat uit twee hoofdonderdelen: een API (**A**pplication **P**rogramming **I**nterface) en een Website.

**De API:** De API is bedoeld voor developers die een random getallen en/of letterreeks nodig hebben. Dit kan zijn voor wachtwoorden, hashing en bijvoorbeeld encryptie sleutels.
Deze API wordt dan gebruikt in hun eigen programma.

**De website:** De website is echt bedoeld voor de normale gebruiker die geen echte kennis heeft over IT en app development.
Op deze website kunnen gebruikers wachtwoorden genereren die gemaakt zijn door mijn ‘true random generator’, deze wachtwoorden zijn een stuk veiliger dan normaal gegenereerde wachtwoorden. Oftewel, wachtwoorden die door een pseudorandom algoritme zijn gegenereerd.
Op de website moeten developers met een account inloggen om toegang te krijgen tot de API, want deze is beveiligd.

![[Pasted image 20220707211332.png|500]]
*Figuur 1 : Servicemodel met daarin de verschillende generators en waar deze hun data naartoe sturen.*

### Demo
Verder heeft mijn challenge ook een demo waarbij ik een klein systeem maak dat beveiligd wordt met mijn number generator. Denk hierbij aan een database server die random wachtwoorden heeft of programma die Salts gebruikt bij het hashen van wachtwoorden.

![[Pasted image 20220707212839.png|400]]
*Figuur 2: Conceptueel netwerkontwerp voor de demo.*
___
