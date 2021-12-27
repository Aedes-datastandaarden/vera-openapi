# vera-openapi



Het gegevensmodel van VERA kent verticale modellen en een horizontaal model. Het horizontale model is de meest rijke verzameling aan klassen en velden per klasse (klassen worden binnen Novius aangeduid met: entiteitstypes en attribuuttypes, dat nemen we hier over). De verticale modellen richten zich op specifieke ketenprocessen en bevatten alleen die klassen en velden die relevant zijn binnen een proces. Ze bevatten een selectie van entiteiten uit de horizontale verzameling, en per klasse vaak weer een selectie aan attributen. ​

De entiteiten uit alle modellen (zowel de verticale als horizontale) zijn verdeeld in Informatiedomeinen. Een Informatiedomein is een clustering op basis van een bedrijfsfunctie. Een bedrijfsfunctie heeft een 1 op 1 relatie met een Afdeling waarbinnen deze bedrijfsfuncie valt en daarmee met een Informatiemodel. Een Informatiemodel bevat dus functies met een sterk onderlinge cohesie.​

![alt text](matrix-proces-informatiedomein.png)

We leveren OpenAPI-specificaties voor zowel de Informatiedomeinen als voor de ketenprocessen. Hiervoor hanteren we onderstaande regels: ​

- We gebruiken OpenApi 3.0 om overerving (OO) op te lossen (oneOf/allOf). Afgeleide klassen zijn alleen opvraagbaar via de basis-entiteit (ook wel aangeduid met superentiteit). ​

- Voor de verticale modellen (ketenprocessen) leveren we per model een API-specificatie.​

- Voor het horizontale model leveren we per Informatiedomein een API-specificatie.​

- Zelfde entiteitstypen kunnen binnen hetzelfde verticale model per resource (bericht) een verschillende definitie hebben.​

- In een API-specificatie voor een ketenproces zijn voor de berichten alle definities van afhankelijke entiteitstypen opgenomen, ongeacht het informatiedomein waartoe ze horen. Entiteiten uit de horizontale modellen zijn als URI opgenomen met uitzondering voor klassen uit Algemeen (Referentiedata en Sturingslabels), die worden wel embbedded opgenomen.

- Voor een API-specificatie van een Informatiedomein geldt dat verwijzingen naar resources uit andere Informatiedomeinen niet embedded opgenomen worden, maar als referentie (URI). Hiervoor geldt het architectuurprincipe dat systemen uit verschillende Informatiedomeinen zich via API’s verbinden.​

- In de API-specificaties worden voor sleutelvelden van een entiteitstype (voorheen kerngegevens) nieuwe entiteitstypen gegenereerd met als naam de daam van de entiteit gevolgd door '-sleutels'.

- Ook Informatiedomein Algemeen heeft een eigen API-specificatie.​

- Enumaraties: de wens is om referentiedata voor soorten van afgeleide klassen als enumeratie op te nemen (bijvoorbeeld: relatie.soort overeenkomst.soort)
- Metadata (limiet aantal entiteiten, verzendende organisatie, tijdstip bericht, etc.) zit niet in de 'payload' maar wordt in de header meegestuurd.


## Definities

![alt text](openapi-per-model.png)

- in de verticale API's worden de entiteiten geprefixt met de naam van de resource

- in de horizontale API's worden entiteiten zonder prefix opgenomen


## Toepassing

Binnen Informatiedomeinen bevinden zich applicaties/systemen met functies die sterk onderling verwand zijn. Dit worden ook wel kernpakketten genoemd. Bijvoorbeeld een relatiebeheerpakket. Voor deze kernpakketten zijn er de horizontale API's.

Voor (sub)systemen die een procesketen implementeren en (eventueel) zijn er de verticale API's. Deze subsystemen agregeren (mogelijk) informatie uit kernpakketten via de horizontale API's.

![alt text](matrix-apis.png)
