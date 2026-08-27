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
