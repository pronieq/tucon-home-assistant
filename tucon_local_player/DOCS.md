# Installatie en gebruik

1. Installeer **Tucon Local Player** vanuit de Tucon App-repository.
2. Start de app.
3. Open **Web UI**. Home Assistant verzorgt de toegang via Ingress.
4. Doorloop de zes stappen: hub, project, display, apparaten, vormgeving en publiceren.
5. Sla de configuratie op. Deze blijft lokaal bewaard in de persistente `/data`-map van de app.

## Een tablet koppelen

1. Open Tucon via **Web UI** in Home Assistant.
2. Kies **Tablet koppelen** en maak een eenmalige koppelcode.
3. Scan de QR-code met de tablet, of open de ingestelde Tablet-URL op de tablet en voer de zes cijfers in.
4. Geef het display een herkenbare naam en kies de gebruikte kiosk-app.
5. Neem na het koppelen de getoonde **Start URL** over in de kiosk-app.
6. Schakel fullscreen, automatisch starten en scherm aanhouden in.

De code verloopt na tien minuten en werkt één keer. De tablet ontvangt daarna een eigen HttpOnly-apparaatsessie. Via **Tablet koppelen** kan de installateur eerder gekoppelde displays bekijken en de toegang onmiddellijk intrekken.

**Fully Kiosk Browser** is het aanbevolen profiel voor Android-tablets. Tucon blijft ook werken in andere browsers en kiosk-apps. Elk actief display meldt periodiek zijn bereikbaarheid, app, Tucon-versie, schermformaat en oriëntatie. Het beheerscherm toont deze gegevens en kan de actuele bereikbaarheid opnieuw controleren. Bij netwerkverlies blijft het laatst bekende dashboard zichtbaar. Tucon herlaadt pas wanneer de lokale backend aantoonbaar weer bereikbaar is; een cooldown voorkomt herlaadlussen.

Tucon gebruikt twee gescheiden poorten:

- `8787` is uitsluitend de interne Home Assistant Ingress-ingang;
- `8788` is de beveiligde lokale tablet-ingang.

Pas de optie **Tablet-URL** aan als `homeassistant.local` op het netwerk niet werkt, bijvoorbeeld naar het vaste lokale IP-adres van de Home Assistant-module.

## TUCON SaaS koppelen

1. Maak in TUCON SaaS een installatie en tijdelijke koppelcode.
2. Open TUCON via **Web UI** in Home Assistant.
3. Open in het TUCON-dashboard als beheerder **SaaS**.
4. Vul de SaaS-URL, naam van de Green en zescijferige koppelcode in.
5. Controleer in hetzelfde scherm of de status **Online verbonden** wordt.

De app opent zelf een uitgaande, versleutelde verbinding. Er hoeft geen poort in de router open en alle lokale bediening blijft zonder internet werken.

## Privacy en opslag

- Tucon verwerkt Home Assistant-data lokaal.
- Het automatisch verstrekte Supervisor-token wordt alleen in het procesgeheugen gebruikt en niet opgeslagen.
- Dashboardconfiguratie, gehashte apparaattokens en de offline snapshot staan in `/data`.
- Het oorspronkelijke apparaattoken staat alleen in een HttpOnly-cookie op de gekoppelde tablet.

## Dashboard en vormgeving

De onboarding laat de installateur een begroetingsnaam, projectnaam, displayformaat, oriëntatie, motionniveau, accentkleur en gewenste modules kiezen. Ook kunnen Tucon-branding en co-branding met de installatiepartner worden ingesteld. Een live voorvertoning toont vóór publicatie hoe de identiteit en belangrijkste keuzes op het display verschijnen.

Het gepubliceerde dashboard maakt de navigatie en ruimtekaarten automatisch uit deze configuratie en de geselecteerde Home Assistant-entiteiten. De huidige versie vormt tevens de technische basis voor uitgebreidere white-labelthema's in een latere release.

## Ondersteunde platformen

- Home Assistant OS op `amd64` en `aarch64`.
- Home Assistant-entiteiten: media player, lamp, schakelaar, sensor, binary sensor, klimaat, cover en scene.

## Problemen oplossen

Controleer bij verbindingsproblemen eerst het app-logboek. Herstart daarna Tucon. Verwijder `/data` niet: daarin staan de onboardingconfiguratie en offline snapshot.
