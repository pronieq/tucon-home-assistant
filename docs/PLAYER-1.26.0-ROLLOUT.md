# Player 1.26.0 — test-Green

## Installeren

1. Vernieuw de app-catalogus in Home Assistant.
2. Installeer of update Tucon Local Player naar 1.26.0.
3. Start de app opnieuw en controleer dat Cloud de Green online ziet met versie 1.26.0.

## Acceptatie

- Open de installatiewizard en controleer bestaande keuzes vóór opslaan.
- Kies bronnen voor netafname, teruglevering, zon en gas.
- Voer helperbeheer tweemaal uit. De tweede uitvoering moet hergebruiken en niets dupliceren.
- Kies bij dubbeltarief beide registers en controleer één somhelper plus één dagmeter.
- Controleer dat een W/kW-bron wordt geweigerd als dagenergiebron.
- Koppel zonne- en verbruiksprognoses voor dit en volgend uur en de prijs van het volgende uur.
- Controleer achtereenvolgens Advies, Geen bijzonder advies en Onvoldoende geldige gegevens.
- Onderbreek een bron kort; de laatst bekende dashboardwaarde mag blijven staan, maar Intelligence mag die niet als actueel gebruiken.
- Herstart de Player en controleer behoud van helpers, historie en Intelligence-configuratie.
- Test de dagbriefing op het echte tablet: Nederlandse stem, stoppen, opnieuw afspelen en geen verouderd advies.
- Controleer na lokale middernacht dagtotalen, afvalstatus en uurvensters.

Leg afwijkingen vast. Rol Cloud 0.39.0 pas uit wanneer deze controle geen blokkerende fout oplevert.
