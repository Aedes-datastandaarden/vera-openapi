# VERA-OpenAPI

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

## Viewers
Hieronder staan links naar SwaggerUI views op de API's. 
Er zijn API's voor de gevensmodellen horend bij **Informatiedomeinen** en **Ketenprocessen**.
Zie ook de toeliching hieronder.
> :bulb: **Tip:** in Markdown worden links niet in een nieuwe pagina geopend. Als je een view opent, navigeer dan terug om weer op deze pagina te komen.

### Ketenprocessen
- [Casemanagement](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/BDO.html)
- [Beheer Financiële gegevens](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/BFG.html)
- [Beheer Overeenkomstgegevens](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/BOG.html)
- [Beheer Relatiegegevens](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/BRG.html)
- [Beheer Vastgoedgegevens](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/BVG.html)
- [Incasso](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/INC.html)
- [Kwaliteitsmanagement](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/KMT.html)
- [Onderhouden Eenheden](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/OHD.html)
- [Verhuren Eenheden](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/VHE.html)
- [Woonruimteverdeling](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Ketenprocessen/WRV.html)


## Toelichting
VERA heeft een alles omvattend gegevensmodel en gegevensmodellen per Ketenproces. De gegevensmodellen per Ketenproces bevatten alleen die entiteiten - en per entiteit alleen die attributen - uit het alles omvattende model, die een rol spelen binnen de procescontext.
De entiteiten uit alle modellen zijn onderverdeeld in Informatiedomeinen. Een Informatiemodel bevat functies met een sterk onderlinge cohesie.​

![alt text](matrix-proces-informatiedomein.png)

We leveren OpenAPI-specificaties op voor zowel de Informatiedomeinen als voor de Ketenprocessen. Hiervoor hanteren we onderstaande regels: ​

- We gebruiken OpenApi 3.0 om overerving (OO) op te lossen (oneOf/allOf). Afgeleide klassen zijn alleen opvraagbaar via de basis-entiteit (ook wel aangeduid met superentiteit). ​

- Voor de Ketenprocessen leveren we per model een API-specificatie.​

- Voor het alles omvattende model leveren we per Informatiedomein een API-specificatie.​Hierin zijn alle entiteiten een bericht.

- Zelfde entiteitstypen kunnen binnen hetzelfde Ketenprocesmodel per bericht een andere definitie hebben.​

- In de API-specificatie van een Ketenproces worden alle afhankelijkheden opgenomen, ongeacht het Informatiedomein waartoe ze horen, met uitzondering van entiteiten uit Informatiedomein-API's die zonder restrictie gebruikt worden. Die worden als referentie (URI) opgenomen en moeten dus met aparte calls opgehaald worden. Uitzondering hierop vormen de entiteiten uit Informatiedomein Algemeen (Referentiedata, Sturingslabels, etc.), die worden wel opgenomen in iedere API.

- Voor een API-specificatie van een Informatiedomein geldt dat verwijzingen naar resources uit andere Informatiedomeinen niet embedded opgenomen worden, maar als referentie (URI). Hiervoor geldt het architectuurprincipe dat systemen uit verschillende Informatiedomeinen zich via API’s verbinden.​

- In de API-specificaties worden voor sleutelvelden van een entiteitstype (de kerngegevens) nieuwe entiteitstypen gegenereerd met als naam de naam van de entiteit gevolgd door '-sleutels'.

- Ook Informatiedomein Algemeen heeft een eigen API-specificatie.​

- Enumaraties: de wens is om referentiedata voor soorten van afgeleide klassen als enumeratie op te nemen (bijvoorbeeld: relatie.soort, overeenkomst.soort)

- Metadata (limiet aantal entiteiten in response, verzendende organisatie, tijdstip bericht, etc.) zit niet in de 'payload' maar wordt in de header meegestuurd.


## Definities

![alt text](openapi-per-model.png)

- in de API's worden entiteiten geprefixt met de naam van de resource


## Toepassing

Volgens de definitie bevinden systemen met functies die sterk onderling verwand zijn zich binnen een Informatiedomein. Deze systemen worden ook wel kernpakketten genoemd. Bijvoorbeeld een Relatiebeheerpakket. Hiervoor zijn de API's bedoeld van de Informatiedomeinen.

De Ketenproces-API's zijn voor (sub)systemen die een ketenproces implementeren. Deze subsystemen agregeren (mogelijk) informatie uit kernpakketten via een Informatiedomein-API's.

![alt text](matrix-apis.png)


### Informatiedomeinen
- [Algemeen](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Algemeen.html)
- [Dossier](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Dossier.html)
- [Financien](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Financien.html)
- [Kwaliteit](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Kwaliteit.html)
- [Onderhoud](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Onderhoud.html)
- [Overeenkomsten](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Overeenkomsten.html)
- [Projectontwikkeling](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Projectontwikkeling.html)
- [Relaties](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Relaties.html)
- [Vastgoed](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Vastgoed.html)
- [Woonruimteverdeling](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vereniging-corponet/vera-openapi/hotfix/docs/Informatiedomeinen/Woonruimteverdeling.html)


