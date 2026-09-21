# Local Player 1.25.0 — test-Green acceptatie

Installeer deze versie uitsluitend eerst op de TUCON test-Green. Controleer vóór Cloud 0.38.0:

1. Bestaande configuratie, koppelingen, voertuigen en historie blijven behouden.
2. Dashboard start na update en na een volledige Green-herstart.
3. Een geldige nul blijft zichtbaar.
4. Onderbreek een gekoppelde sensor kort: de kaart knippert niet en toont daarna rustig het laatste meetmoment.
5. Herstel de sensor: de melding verdwijnt zonder indelingssprong.
6. Wissel tijdelijk van bron: een waarde van de vorige bron wordt niet hergebruikt.
7. Maak een poort of slot onbereikbaar: bediening wordt direct geblokkeerd en de oude toestand geldt niet als bevestiging.
8. Controleer na dagwisseling dat een dagtotaal van gisteren niet als vandaag wordt getoond.
9. Controleer weericonen, PMD-weergave en de animatie/het label Vandaag.
10. Controleer Studio-voorvertoning en Player op dezelfde tabletverhouding.

Leg per stap geslaagd/mislukt en eventuele foutmelding vast. Merge en deploy Cloud PR #64 pas na een volledig geslaagde ronde.
