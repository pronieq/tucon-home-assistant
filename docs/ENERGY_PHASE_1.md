# Energie fase 1 — Player 1.19.0 / Cloud 0.31.0

## Oplevering

De Green leest uitsluitend de in Energiebeheer geselecteerde Home Assistant-sensoren. De verzameling draait in de Node-achtergrondserver en is onafhankelijk van een geopende tablet, Studio-preview, dashboardselectie of dashboardversie. Deze fase bevat geen prijsadvies, AI, laadplanner of apparaatbediening.

Cloud: open een installatie en kies **Energiebeheer**. Selecteer de Green, de bronnen en eventueel de tijdzone. Controleer bij het getekende netvermogen of positief afname betekent. Schakel verzamelen in en kies **Opslaan en toepassen**. Er wordt een afzonderlijke energieversie opgeslagen en ondertekend naar de Green gestuurd. De status is pas actief wanneer de Green die versie zelf rapporteert. De eerste afgesloten kwartierwaarde verschijnt doorgaans binnen twintig minuten.

Er is één verzamelende Green per installatie. Overdracht naar een andere Green is in deze fase bewust nog geen gebruikersfunctie. Een opnieuw met een andere device-identiteit gekoppelde Player wist zijn oude lokale energiegegevens, zodat deze niet bij een volgende klant terechtkomen.

## Meetdefinities

- Rollen: getekend netvermogen, afzonderlijk afname-/terugleververmogen, zonnevermogen, cumulatieve afname-/teruglever-/zonnemeterstand.
- Alleen HA-sensoren met de passende `device_class`. Vermogen W/kW wordt W; Wh/kWh/MWh wordt kWh. Meterstanden vereisen `state_class: total` of `total_increasing`.
- Een lokale HA-uitlezing iedere minuut. `observedAt` is het moment van deze uitlezing, niet een gegarandeerd fysiek meettijdstip. `sourceUpdatedAt` bewaart, indien beschikbaar, HA's `last_updated`; een onveranderde waarde wordt hierdoor niet automatisch verouderd verklaard.
- Kwartieren worden op UTC-epochgrenzen berekend. De installatie-tijdzone is alleen voor de presentatie en geeft ook bij zomer-/wintertijd unieke tijdvakken.
- Vermogen: tijdgewogen gemiddelde met de vorige geldige waarde tussen twee opeenvolgende uitlezingen. Geen kWh-afname afleiden uit gemiddeld getekend netvermogen; gebruik afzonderlijke cumulatieve meterstanden.
- Energie: positieve verschilwaarde tussen cumulatieve meterstanden. Bij een daling wordt geen negatief verbruik geboekt: het betrokken kwartier krijgt `reset`. Een cumulatieve teller met periodieke reset kan daardoor een onvolledig kwartier geven.
- Intervallen langer dan 120 seconden, ontbrekende sensoren, onbereikbaarheid en ongeldige metadata worden niet geïnterpoleerd of als nul ingevuld. Historie zonder meetvenster blijft een zichtbaar gat; bestaande vensters krijgen een onvolledige dekking.
- Een energieverschil dat over een kwartiergrens loopt, wordt naar tijdsduur verdeeld. Volledige vensters met zo'n verdeling heten `estimated`. Onvolledige vensters blijven `partial`; toon daarom altijd de dekking naast de waarde.
- Afgesloten kwartieren worden nog 120 seconden vastgehouden om lopende uitlezingen af te ronden. Een bevestigd kwartier wordt nooit overschreven.

## Opslag en verbinding

`/data/energy.sqlite` (of `TUCON_DATA_DIR`) bevat configuratie, laatste uitlezingen, minuutmetingen en kwartierwaarden. SQLite gebruikt WAL. Het bestaande persistente datavolume moet ook voor deze database en zijn WAL-bestand beschikbaar blijven.

De bestaande gepaarde WebSocket gebruikt `energy.status`, `energy.telemetry.batch` en `energy.telemetry.ack`. Batches bevatten maximaal 128 kwartierwaarden en worden iedere 30 seconden aangeboden. Een gemiste bevestiging leidt tot dezelfde batch opnieuw verzenden. Pas na een bevestiging markeert de Green zijn records als verzonden. Cloud slaat kwartieren idempotent op binnen één transactie, met de installatie afgeleid van het aangemelde apparaat. De configuratieversie en iedere bron moeten bij die Green horen.

Minuutmetingen en kwartierwaarden worden lokaal zeven dagen bewaard. Ook niet-verzonden gegevens ouder dan zeven dagen verlopen, om onbeperkte schijfgroei te voorkomen; `droppedBefore` meldt dit expliciet. Een cloudonderbreking langer dan die bewaartermijn kan dus gegevensverlies veroorzaken. Cloud bewaart kwartierwaarden maximaal 400 dagen, met opruiming bij opstarten en ieder uur. De Cloud-pagina toont 1, 7 of 30 dagen.

Cloud gebruikt afzonderlijke PostgreSQL-tabellen `energy_settings`, `energy_configuration_versions`, `energy_intervals` en `energy_status`; meetgegevens komen niet in `tucon_state`. De bestaande installatie-ID wordt logisch gekoppeld; installaties staan momenteel nog in JSONB, zodat een SQL-foreign-key naar een installatietabel niet mogelijk is. Ontwikkelopstellingen zonder DATABASE_URL gebruiken een afzonderlijke SQLite-database.

Lokale alleen-lezen-API voor gekoppelde displays en HA-beheerders: `GET api/energy` en `GET api/energy/history?days=1|7`. Deze fase toont het beheerscherm en de historie in Cloud; het gedeelde tablet-dashboardpakket verandert niet.

## Releasevolgorde

1. Merge en deploy Cloud 0.31.0; nieuwe installaties blijven standaard uitgeschakeld.
2. Merge de Player-PR en maak de release volgens de bestaande containerworkflow. Controleer zowel amd64 als aarch64 en het manifest.
3. Pas daarna de voorbereide `tucon-home-assistant`-metadata voor 1.19.0 mergen. Geen update aanbieden voordat de container beschikbaar is.
4. Update de pilot-Green. Cloud vereist de expliciete `energyTelemetry`-capability vóór configuratie.
5. Selecteer de echte P1-bronnen en controleer meetrichting, units en dekking. Vergelijk twee afgesloten kwartieren met Home Assistant.

Een downgrade van de Player stopt de nieuwe verzameling. De additive Cloud-tabellen en bestaande historie kunnen behouden blijven. Een dashboardrollback heeft geen invloed op de energieconfiguratie. Om verzamelen uit te zetten moet de Green de uitgeschakelde energieversie ontvangen; een offline Green kan nog met zijn laatst geldige instellingen doorwerken.

## Validatie

`npm test` controleert onder meer kwartiergrenzen, meterreset, datagaten, ongeldige eenheden, herstart, andere apparaatidentiteit, revisieconflicten, dubbele verzending en wijziging tijdens een lopende uitlezing. De Cloud-tests gebruiken de echte HTTP-tenantguard voor configuratie en historie. Dezelfde protocolfixture moet in Cloud en Player identiek blijven.

Praktijktest op een echte Home Assistant Green en beide gepubliceerde containerarchitecturen blijft de releasegate; lokale simulatie is geen hardwaretest.
