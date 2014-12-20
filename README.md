# Tilskudsberegner til energiforbedringer
================

Energitilskuddet søges ved at indgå aftale med et net- eller distributionsselskab (efter frit valg - dog maks 1) før energirenoveringen bliver startet op. Det er ikke tilladt at indgå en bindende aftale om køb af materialer, udstyr eller om selve udførelse af projektet før der bliver søgt om tilskud. 

Net- og distributionsselskabet skal indberette energibesparelsen til Energistyrelsen som et led i opfyldelse af net- og distributionsselskabernes obligatoriske spareindsats, som de har indgået en aftale om med Klima-, Energi- og Bygningsministeriet. 

Et program til at beregne energitilskud fra Energistyrelsen. Følgende trin gennemgåes:

1. Der tages først udgangspunkt i eksisterende program
2. Første etape med fokus på udskiftning af elsparetiltag ([Elbesparelser](http://sparefeber.dk/spar-paa-elregningen/)), da denne gavner såvel lejer som ejerboliger  
3. Der tages udgangspunkt i Energistyrelsens Standardværdikatalog for energibesparelser fra ([Teknologisk](http://svk.teknologisk.dk/Pages_open/Default.aspx))
4. Planlægning af nyt og forbedret energitilskudsprogram
4. Udvidelse af programmet til støtte af forslag til genindførsel af håndværkerfradraget ([Smart Energi](http://smartenergi.dk/haandvaerkerfradrag/))

## Nuværende energitilskudsprogram

Det er muligt at søge om tilskud til energiforbedringer for såvel private som erhvervskunder.

### Trin 1 (nuværende program)
Når kunden skal søge om tilskuddet, sker det udfra startkriteriet nuværende kilde til opvarming af boligen.

- Fjernvarme
- El
- Gas
- Olie
- Biobrændsel

### Trin 2 (nuværende progam)
Herefter skal der vælges om boligarealet er imellem 80 og 200 kvadratmeter eller andet.

### Trin 3 (nuværende program)
Herunder redirecter Ajax til en af fanerne med følgende valgmuligheder:
- Isolering
  - Gulve/terrændæk
  - Kælderydervægge
  - Tagkonstruktion
  - Ydervægge

- Vinduer/døre
  - Udskiftning af døre
  - Udskiftning af hele vinduespartier
  - Udskiftning af enkeltruder

- Varmesystem
  - Radiator og radiatorventiler

- El & lys
  - LED pærer
  - Tænd/sluk/spareskinner

## Standardværdikatalog for energibesparelser

Værdier fra Standardværdikataloget kan hentes ned via WebService fra

http://svk.teknologisk.dk/WebService_SVK.asmx

#### Funktionsoversigt i Standardværdikatalogets WebService
Et kald til webservicen giver et komplet databaseudtræk. Standardværdikataloget bliver opdateret mindst en gang om året.

*GetEnhedstype*
Returnerer en XML streng som indeholder enhedstyper.

*GetForsyningstype*
Returnerer en XML streng som indeholder forsyningstyper.

*GetLevetid*
Returnerer en XML streng som indeholder levetid.

*GetPrioritetsfaktor*
Returnerer hvilken prioritetsfaktor energibesparelse i kWh skal ganges med for det valgte tiltag (identifier med dets ID). Hvis ID = 0 returneres prioritetsfaktor for hele katalog.

*GetStandardvaerdikatalog*
Returnerer en XML streng, som indeholder hele standardværdikatalog for energibesparelser. Med (parameter = True) eller uden (parameter = False) udgåede tiltag

*GetVersion*
Returnerer den nuværende versionr.

*SetDFF_referenceID*
Bruges ikke

### Hovedoverskrifter i Standardværdikataloget

Standardværdikatalogets hovednodes består af følgende fra .NET WebServicen:

Belysning
Biomasse
Cirkulationspumper
EL-besparelser diverse
Feedback om elforbrug
Fjernvarmeanlæg, afkølings- og energibesparelser
Gaskedler
Klimaskærm - isolering
Klimaskærm - vinduer, ovenlys og døre
Køl-frys
Kontorudstyr
Madlavning
Oliekedler
Solceller
Solvarme
Varmepumper
Vaskeapparater

## Nyt energitilskudsprogram

Der skal udføres en research der tager målgrupper som udgangspunkt - og dernæst tænker dataudtræk fra WebServicen ind. Udarbejdelse af flowdiagrammer og algoritmer er i gang.

Den lineære liste over energiforbedrende foranstaltninger skal abstraheres, så det bliver forståeligt, struktureret og overskueligt set fra brugerens side. Eksempelvis tages udgangspunkt i et hus, hvor der er visuelle illustrationer af forskellige elementer i et hus.

Programmet skal serveres direkte på Energikøb.dk uden at have bestå af forvirrende pop-up-bokse. Brugerflowet skal være langt mere brugervenligt, hvor overflødige knapper som "Tilføj den første besparelse" skal væk. Det grafiske bruger-interface skal ikke have pile, der vender imod urets retning, da dette er counter-intuitivt. Især da udfyldning af spørgeskemaet i forvejen må anses som teknisk og fremmed for brugeren. Der skal lægges mange kræfter i at gøre brugerfladen så let som muligt at benytte.

Det nye tilskudsprogram skal have mere fokus på overskuelighed og brugervenlighed. Som den nuværende, kommer der en forstyrrende pop-op-boks, der fortæller kontaktinfo i det øjeblik man har trykket på Call to Action-knappen. Tingene skal ligeledes foretages on site - og uden udgående links der forstyrrer brugeren i processen.

Det er afgørende for succes med konverteringerne, at brugeren hele flowet igennem, føler sig klog og har styr på og overblik over hvad de skal og hvor i processen. Det skal ligeledes være mere tydeligt hvilke ulemper der reduceres og hvilke fordele der opnåes.

Hvis muligt, skal flowet for testen skal være mere brugercentreret udfra Standardværdikatalogets WebService.

