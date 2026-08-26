# Tucon Local Player

Tucon combineert geselecteerde Home Assistant-apparaten en sensoren in één eenvoudig, lokaal bedieningspaneel. De onboarding ontdekt ruimtes en geschikte entiteiten en genereert daarna het dashboard voor het gekozen display.

De Home Assistant App gebruikt de interne Core API. Er hoeft geen Long-Lived Access Token te worden aangemaakt of ingevoerd.

Een installateur koppelt tablets met een eenmalige QR-code. Ieder display krijgt daarna een eigen intrekbare sessie en alleen toegang tot het gepubliceerde dashboard; configuratie en apparaatbeheer blijven binnen Home Assistant Ingress.

Actieve displays melden hun bereikbaarheid, kiosk-app, versie en schermformaat aan Tucon. De ingebouwde verbindingsbewaking herstelt een langdurig vastgelopen dashboard gecontroleerd.
