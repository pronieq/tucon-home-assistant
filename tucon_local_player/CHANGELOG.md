# 1.12.2

- Routeert de volledige Home Assistant-frontend rechtstreeks via de interne Home Assistant-DNS.
- Valt automatisch terug op de korte interne hostnaam wanneer de canonieke DNS niet bereikbaar is.
- Laat Home Assistant de browserauthenticatie afhandelen en zet geen Supervisor-token op frontendverzoeken.

# 1.12.1

- Herstelt remote Home Assistant-toegang op Home Assistant OS via de ondersteunde Supervisor/Core-route.
- Stuurt het tijdelijke Supervisor-token alleen intern mee; het token verlaat de Green niet.
- Toont de Supervisor-status weer via de juiste API-endpoint.

# 1.12.0

- Voegt veilige systeemmonitoring voor Home Assistant, Supervisor en HA OS toe.
- Ondersteunt tijdelijke remote Home Assistant-sessies via de bestaande uitgaande TUCON Cloud-verbinding.
- Vereist geen port-forwarding en bewaart geen Home Assistant-wachtwoorden in TUCON Cloud.

# 1.11.1

- Herstelt de aanklikbaarheid van Overzicht, Energie, Verlichting en Auto op tablets en kioskbrowsers.
- Laat aanrakingen door de transparante header naar het dashboardmenu gaan.
- Houdt het logo en de headerknoppen gewoon bedienbaar.

# 1.11.0

- Voegt echte dashboardschermen toe voor Overzicht, Energie, Verlichting en Auto.
- Laat actieve schermen, volgorde, bronnen en verlichtingsruimtes instellen via Dashboard Studio.
- Voegt een subtiele slide-overgang toe bij het wisselen van scherm.
- Toont datum, dagdeel en naam in een verbeterde begroetingshiërarchie.
- Verplaatst de project- of woningnaam naar de vaste woningkaart.
- Migreert bestaande dashboards veilig naar het verplichte scherm Overzicht.

# 1.10.1

- Voegt lokale Nederlandse Piper-spraak toe voor Fully Kiosk en andere tabletbrowsers zonder Web Speech.
- Speelt de dagbriefing als gewone HTML5-audio af, zonder Fully Plus of externe TTS-dienst.
- Behoudt browser-TTS op apparaten die dit ondersteunen.
- Beveiligt en cachet gegenereerde audio om dubbele synthese en onnodige wachttijd te voorkomen.

# 1.10.0

- Voegt een configureerbare dagbriefing toe naast de begroeting op het tablet.
- Leest begroeting, datum, weer en geselecteerde verlichting voor.
- Ondersteunt een Nederlandse stem, spreeksnelheid, vrije volgorde en play/stopbediening.
- Slaat ontbrekende of offline onderdelen automatisch over.

# 1.9.0

- Toont altijd een vast woning- of kantoorgebouw in het linker dashboardblok.
- Laat per installatie kiezen welke energie- en klimaatwaarden zichtbaar zijn.
- Verbergt niet-beschikbare waarden of toont een streepje volgens de Studio-instelling.
- Levert de nieuwe lichte 3D-afbeeldingen mee voor de tabletweergave.

# 1.8.0

- Maakt Dashboard Studio een volledige live editor met dezelfde dashboardcompositie als de tablet.
- Stuurt iedere tien seconden een begrensde, read-only snapshot van actuele Home Assistant-gegevens naar TUCON Cloud.
- Toont onder meer actuele entiteitswaarden, Sonos-status, weerverwachting, integratiewaarden en Feedreader-berichten in de Studio.
- Markeert het gedeelde renderercontract zodat Studio en Player aantoonbaar dezelfde compositie gebruiken.
- Houdt bediening in de Studio uitgeschakeld; klikken selecteert uitsluitend een dashboardblok.

# 1.7.0

- Voegt één adaptief weerblok toe in grote, normale en compacte formaten.
- Toont in de grote variant maximaal zes dagen verwachting via `weather.get_forecasts`.
- Gebruikt eigen illustraties voor zon, nacht, bewolking, regen, onweer, sneeuw, hagel, mist en wind.
- Laat Studio en tablet dezelfde formaat- en conditieregels gebruiken.

# 1.6.2

- Laat het Feedreader-nieuwsblok in ieder leeg dashboardvak behalve Woning plaatsen.
- Toont maximaal vijf koppen in brede vakken en drie koppen in normale of compacte vakken.
- Voorkomt de fout “Geen passend leeg vak beschikbaar” bij vrijwel volle dashboards.

# 1.6.1

- Voegt een vast nieuwsblok toe met drie tot vijf berichten uit Home Assistant Feedreader.
- Synchroniseert Feedreader event-entiteiten naar TUCON Cloud.
- Bewaart recente nieuwsberichten lokaal op de Green en werkt het tablet realtime bij.
- Bevat de release-metadatafix uit de vervallen 1.6.0-releasepoging.

# 1.5.1

- Herstelt het ontbrekende Sonos-audioblok in het vaste brede audioslot.
- Resolveert v4-slots rechtstreeks via het opgeslagen kaart-ID.
- Houdt de audiokaart zichtbaar wanneer Home Assistant tijdelijk geen mediaspelerstatus levert.

# 1.5.0

- Vervangt het oude dashboard door Dashboard Platform v4 zonder legacy-fallbacks.
- Gebruikt exact negen canonieke Signature-slots met blijvende placeholders.
- Ondersteunt niet-toegewezen Home Assistant-entiteiten zonder kaarten te verliezen.
- Weigert een publicatie volledig wanneer een kaart, binding of slot afwijkt.
- Bevestigt na activatie het exacte renderercontract, alle kaart-ID’s en alle slots aan TUCON Cloud.

# 1.4.0

- Introduceert Dashboard Platform v3 met vaste Signature-slots en blijvende placeholders.
- Voegt vaste woning/P1-, weer-, audio- en verlichtingsblokken met meerdere databronnen toe.
- Behoudt identiteit, blokinstellingen, databindingen en exacte posities bij publicatie vanuit TUCON Cloud.
- Verwerkt realtime updates voor alle gekoppelde sensoren in samengestelde blokken.
- Voorkomt lokale overschrijving van centraal beheerde Cloud-configuraties.

# 1.3.1

- Corrigeert het dashboard naar exact één hoge kaart links, drie gelijke bovenkaarten, twee gelijke middenkaarten en drie gelijke onderkaarten.
- Toont voor ieder niet-gevuld vak een vaste gestippelde placeholder, zodat nooit gaten in de indeling ontstaan.

# 1.3.0

- Maakt het tabletdashboard exact gelijk aan de vaste negen-vakkenindeling van Dashboard Studio.
- Behoudt iedere gepubliceerde tegel in hetzelfde opgeslagen slot.
- Migreert oudere Signature-configuraties veilig naar de nieuwe compositie.
- Optimaliseert grote, brede en compacte kaarten voor het 16:9-tabletscherm.

# 1.2.1

- Activeert de TUCON Signature-stijl standaard voor bestaande v2-dashboards.
- Maakt automatisch een vaste professionele indeling wanneer Studio-slotmetadata ontbreekt.
- Verwijdert de dubbele tekst naast het TUCON-logo.

# 1.2.0

- Volledig vernieuwd TUCON Signature-tabletdashboard volgens het ontwerp uit Dashboard Studio.
- Vaste professionele indeling voor woning, briefing, klimaat, mobiliteit, weer, media, verlichting, gordijnen en kleine apparaten.
- Blauwgroene glass-stijl met lime accenten en een afzonderlijke portrait fallback.
- Bestaande realtime bediening, offline werking, plattegronden en partnerbranding blijven behouden.

# 1.1.1

- Herstelt het publiceren en lokaal bewaren van plattegronden en markers vanuit TUCON Cloud.
- Laadt en bedient ook Home Assistant-devices die uitsluitend op een plattegrond zijn geplaatst.
- Herstelt de weergave van partnerlogo's in co-brandingmodus.

# 1.1.0

- Voegt een interactieve Plattegrond-view toe aan het TUCON-dashboard.
- Ondersteunt meerdere verdiepingen vanuit de via TUCON Cloud gepubliceerde configuratie.
- Toont Home Assistant-devices op schaalbare, relatieve posities.
- Laat verlichting, schakelaars, scènes en zonwering rechtstreeks vanaf de plattegrond bedienen.
- Toont actuele statusinformatie en houdt de plattegrond offline beschikbaar.

# 1.0.0

- Ondersteuning voor TUCON Dashboard Studio-configuratieschema v2.
- Gemengde Home Assistant- en Cloud API-tegels.
- Offline actieve configuratie en rollbackversie.
- Centrale huisstijl, kaartformaten en navigatie.

# 0.9.1

- Herstelt het ontbrekende TUCON-logo in het lokale tablet-dashboard.
- Neemt de publieke dashboardassets voortaan expliciet mee in de containerbuild.

# 0.9.0

- Hybride HTTP/JSON-integraties met uitvoering via TUCON Cloud of lokaal via de Green.
- Veilige API-headers, visuele JSON-mapping en periodieke waardeverversing.
- API-informatietegels op het tablet met laatst bekende waarden bij storingen.
- Integratiestatus en fouten worden centraal zichtbaar in TUCON Cloud.

# 0.8.4

- Behoudt aangepaste dashboardtitels voor ruimtes bij publicatie vanuit TUCON Cloud.
- De Home Assistant-ruimtenaam wordt alleen gebruikt wanneer geen eigen dashboardtitel is ingevuld.

# 0.8.3

- Herstelt de ontbrekende aansluiting tussen Home Assistant-discovery en de SaaS-connector.
- Synchroniseert de veilige discoverymetadata direct nadat de Green met TUCON Cloud is verbonden.

# 0.8.2

- Herstelt een ongeldige escaped newline in het server-entrypoint.
- De servercode wordt voortaan vóór iedere release syntactisch gecontroleerd.

# 0.8.1

- Gebruikt de actuele SaaS-URL uit de appconfiguratie boven een opgeslagen pilot-URL.
- Start discovery-synchronisatie direct na een succesvolle SaaS-authenticatie.

# 0.8.0

- Veilige synchronisatie van discoverymetadata voor de SaaS-configuratie-editor.
- Actieve configuratie en één rollbackversie blijven lokaal beschikbaar voor offline werking.
- SaaS-configuraties worden vóór activering opnieuw lokaal gevalideerd.

# Changelog

## 0.7.0

- Dashboardconfiguraties ophalen, versioneren en publiceren vanuit TUCON Cloud.
- Iedere cloudconfiguratie wordt lokaal opnieuw gecontroleerd tegen Home Assistant.
- De vorige configuratie wordt automatisch bewaard en bij fouten teruggezet.
- Publicatieresultaat en actieve cloudversie worden veilig aan TUCON Cloud teruggemeld.

## 0.6.0

- SaaS-koppeling rechtstreeks vanuit TUCON beheer, zonder browserconsole.
- Live verbindingsstatus en opnieuw koppelen vanuit één scherm.


## 0.5.0

- Veilige uitgaande WSS-verbinding met TUCON SaaS, zonder open routerpoort.
- Eenmalige SaaS-koppelcode en unieke Ed25519-identiteit per Home Assistant Green.
- Heartbeat en online/offline-status voor centraal beheer.
- Alleen expliciet toegestane, digitaal ondertekende SaaS-opdrachten.
- Lokale bediening blijft beschikbaar zonder internet of SaaS.


## 0.4.0

- Nieuw Tucon-productdashboard, gebaseerd op het aangeleverde ontwerp en geoptimaliseerd voor vaste tablets.
- Zesdelige installateurs-onboarding voor hub, project, display, apparaten, vormgeving en publicatie.
- Configureerbare begroetingsnaam, projectnaam, accentkleur en dashboardmodules.
- Tucon-branding of co-branding met een installatiepartner; de basis voor volledige white-labeling is voorbereid.
- Navigatie en dashboardsamenstelling worden gegenereerd vanuit de lokaal opgeslagen configuratie en Home Assistant-ruimtes.

## 0.3.1

- Houdt het laatst bekende dashboard zichtbaar wanneer de lokale hub onbereikbaar is.
- Voorkomt dat een display tijdens netwerkuitval naar een browserfoutpagina herlaadt.
- Controleert eerst of de Tucon-backend weer bereikbaar is voordat automatisch herstel plaatsvindt.
- Toont een duidelijke herstelmelding tijdens de onderbreking.

## 0.3.0

- Kiosk-onboarding met aanbevolen Fully Kiosk-profiel en exacte Start URL.
- Heartbeat per display met online-status, clientversie, schermformaat en oriëntatie.
- Periodieke verbindingscontrole en gecontroleerd automatisch herstel na een vastgelopen verbinding.
- Realtime keepalive-events en bescherming tegen herlaadlussen.
- Uitgebreid displaybeheer voor installateurs.

## 0.2.1

- Herstelt schrijfrechten op het door Home Assistant gekoppelde `/data`-volume.
- Tucon verlaagt na de beperkte eigenaarschapscontrole direct terug naar de niet-root `node`-gebruiker.

## 0.2.0

- Veilige, eenmalige tablet-pairing met QR-code en zescijferige code.
- Eigen HttpOnly-sessie per display; tokens worden alleen gehasht opgeslagen.
- Beheer en intrekken van gekoppelde displays via Home Assistant Ingress.
- Afzonderlijke interne Ingress-poort en beveiligde lokale tabletpoort.
- Begrenzing van foutieve koppelingspogingen.

## 0.1.0

- Eerste experimentele Tucon Local Player.
- Automatische Home Assistant-koppeling via Supervisor.
- Ingress-interface en persistente lokale configuratie.
- Ondersteuning voor `amd64` en `aarch64`.
