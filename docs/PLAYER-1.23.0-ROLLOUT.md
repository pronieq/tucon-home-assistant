# Player 1.23.0 — distributie

1. Merge dashboard #15 in pronieq/tucon-dashboard en Player #57 in pronieq/tucon.
2. Wacht op de workflow Publish Tucon Local Player: builds voor amd64 en aarch64, multi-architecture manifest en pilotrelease moeten slagen. Controleer dat ghcr.io/pronieq/tucon-local-player:1.23.0 beide architecturen bevat en bij de samengevoegde broncode hoort. De PR-test Verify alleen is niet voldoende.
3. Maak deze concept-PR pas daarna gereed en merge de distributie. Vernieuw de add-onwinkel en installeer 1.23.0 op de test-Green. Controleer opstarten, HA-verbinding en bediening.
4. Zet voor De Bommel de bestaande VRM-instellingen afzonderlijk in de permanente Player-datamap; volg docs/VICTRON-BRIEFING.md in pronieq/tucon. Geen geheimen in GitHub.
5. Pas na geslaagde Player-pilot: merge Cloud #62 in pronieq/tucon-saas en rol 0.36.0 uit. Schakel briefing in Studio in, kies De Bommel alleen voor die woning, sla op en publiceer.
6. Controleer weer, stroomkwartier, afval, optionele bootgegevens en Nederlandse Piper-audio op de echte tablet.

Bewaar vooraf de vorige configuratie en containerreferentie. Bij problemen terug naar Player 1.22.2. Promoveer latest niet vóór een geslaagde pilot.

Deze repository bouwt geen images. De distributie-PR blijft concept zolang de Player-build ontbreekt.
