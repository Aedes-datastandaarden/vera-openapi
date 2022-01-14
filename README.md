# VERA-openapi

#### Inhoud

- [Inleiding](#Inleiding)
- [Viewers](#Viewers)
- [Toelichting](#Toelichting)
- [Definities](#Definities)
- [Toepassing](#Toepassing)

## Inleiding
De mappen **Informatiedomeinen** en **Ketenprocessen** bevatten alle OpenAPI-specificaties (YAML).
Alle overige bestanden in deze repo (in de root en in map 'docs') zijn enkel bedoeld voor documentatie en horen niet bij de opleverset.
Op deze pagina staat een toelichting op de totstandkoming en toepassing van de API's.
> :warning: **LET OP:** deze publicatie is geen officiële release, maar een aanloop naar VERA 4.0. 
Er kunnen derhalve geen rechten aan ontleend worden. Opmerkingen zijn hartelijk welkom. Graag hiervoor een 'Issue' aanmaken (zie 2e menu links-boven).

## Viewers
Hieronder staan links naar SwaggerUI views op de API's. 
Er zijn API's voor de gevensmodellen horend bij **Informatiedomeinen** en **Ketenprocessen**.
Zie ook de toeliching hieronder.
> :bulb: **Tip:** in Markdown worden links niet in een nieuwe pagina geopend. Als je een view opent, navigeer dan terug om weer op deze pagina te komen.

### Ketenprocessen
- [Casemanagement](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/BDO.html)
- [Beheer Financiële gegevens](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/BFG.html)
- [Beheer Overeenkomstgegevens](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/BOG.html)
- [Beheer Relatiegegevens](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/BRG.html)
- [Beheer Vastgoedgegevens](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/BVG.html)
- [Incasso](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/INC.html)
- [Kwaliteitsmanagement](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/KMT.html)
- [Onderhouden Eenheden](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/OHD.html)
- [Verhuren Eenheden](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/VHE.html)
- [Woonruimteverdeling](https://vereniging-corponet.github.io/vera-openapi/Ketenprocessen/WRV.html)


## Toelichting
VERA heeft een alles omvattend gegevensmodel en gegevensmodellen per Ketenproces. De gegevensmodellen per Ketenproces bevatten alleen die entiteiten - en per entiteit alleen die attributen - uit het alles omvattende model, die een rol spelen binnen de procescontext.
De entiteiten uit alle modellen zijn onderverdeeld in Informatiedomeinen. Een Informatiemodel bevat functies met een sterk onderlinge cohesie.​

![alt text](matrix-proces-informatiedomein.png)

We leveren OpenAPI-specificaties op voor zowel de Informatiedomeinen als voor de Ketenprocessen. Hiervoor hanteren we onderstaande regels: ​

- We gebruiken OpenApi 3.0 om overerving (OO) op te lossen (oneOf/allOf). Afgeleide klassen zijn alleen opvraagbaar via de basis-entiteit (ook wel aangeduid met superentiteit). ​

- Voor de Ketenprocessen leveren we per model een API-specificatie.​

- Voor het alles omvattende model leveren we per Informatiedomein een API-specificatie.​

- Zelfde entiteitstypen kunnen binnen hetzelfde Ketenprocesmodel per bericht een andere definitie hebben.​

- In een API-specificatie voor een Ketenproces zijn voor de berichten alle definities van afhankelijke entiteitstypen opgenomen, ongeacht het Informatiedomein waartoe ze horen. Entiteiten uit het alles omvattende model zijn als URI opgenomen, met uitzondering voor entiteiten uit informatiedomein Algemeen (Referentiedata, Sturingslabels, etc.), die worden wel embbedded opgenomen.

- Voor een API-specificatie van een Informatiedomein geldt dat verwijzingen naar resources uit andere Informatiedomeinen niet embedded opgenomen worden, maar als referentie (URI). Hiervoor geldt het architectuurprincipe dat systemen uit verschillende Informatiedomeinen zich via API’s verbinden.​

- In de API-specificaties worden voor sleutelvelden van een entiteitstype (de kerngegevens) nieuwe entiteitstypen gegenereerd met als naam de naam van de entiteit gevolgd door '-sleutels'.

- Ook Informatiedomein Algemeen heeft een eigen API-specificatie.​

- Enumaraties: de wens is om referentiedata voor soorten van afgeleide klassen als enumeratie op te nemen (bijvoorbeeld: relatie.soort overeenkomst.soort)
- Metadata (limiet aantal entiteiten in response, verzendende organisatie, tijdstip bericht, etc.) zit niet in de 'payload' maar wordt in de header meegestuurd.


## Definities

![alt text](openapi-per-model.png)

- in de Ketenproces-API's worden de entiteiten geprefixt met de naam van de resource
- in de Informatiedomein-API's worden entiteiten zonder prefix opgenomen


## Toepassing

Volgens de definitie bevinden systemen met functies die sterk onderling verwand zijn zich binnen een Informatiedomein. Deze systemen worden ook wel kernpakketten genoemd. Bijvoorbeeld een Relatiebeheerpakket. Hiervoor zijn de API's bedoeld van de Informatiedomeinen.

De Ketenproces-API's zijn voor (sub)systemen die een ketenproces implementeren. Deze subsystemen agregeren (mogelijk) informatie uit kernpakketten via een Informatiedomein-API's.

![alt text](matrix-apis.png)


### Informatiedomeinen
- [Algemeen](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Algemeen.html)
- [Dossier](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Dossier.html)
- [Financien](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Financien.html)
- [Kwaliteit](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Kwaliteit.html)
- [Onderhoud](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Onderhoud.html)
- [Overeenkomsten](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Overeenkomsten.html)
- [Projectontwikkeling](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Projectontwikkeling.html)
- [Relaties](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Relaties.html)
- [Vastgoed](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Vastgoed.html)
- [Woonruimteverdeling](https://vereniging-corponet.github.io/vera-openapi/Informatiedomeinen/Woonruimteverdeling.html)


