# TUCON One sprint — integratie en oplevering

## Release-update — 9 september 2026

Player 1.13.0 is [uitgebracht](https://github.com/pronieq/tucon/releases/tag/1.13.0) vanuit de gecombineerde TUCON One- en remote-beheerwijzigingen. De gebruiker heeft de aangepaste preview goedgekeurd. De [releaseworkflow](https://github.com/pronieq/tucon/actions/runs/34328425091) heeft beide images (amd64 en aarch64) en het gezamenlijke manifest voor 1.13.0 succesvol gepubliceerd.

De distributie verwijst naar deze gepubliceerde image. De volgende stap is de pilot-Green bijwerken en lokale werking controleren; daarna volgt de Cloud-release en pas vervolgens activatie van One per installatie.

Onderstaand sprintverslag beschrijft de oorspronkelijke PR-oplevering. De daarin genoemde releasestatus, testtotalen, pakket-hashes en releasevolgorde zijn historisch; voor de actuele uitrol geldt de volgorde hierboven.

## Doel en afbakening

Vaste Tucon One-blokken met een installatiegebonden selectie en geordende homepagefavorieten. Studio en Local Player gebruiken exact hetzelfde dashboardpakket en dezelfde validatie. Bestaande Home Assistant-scenes worden alleen geactiveerd. Er worden geen nieuwe scenes of API-commandoconnectors gemaakt.

Deze sprint eindigt bij afzonderlijke reviewbare PR’s. Er zijn geen doelbranches gepusht, geen andere branches gewijzigd, geen releases getagd en geen productie-uitrol of productiemigratie gestart.

## Basis en gelijktijdige ontwikkeling

| Repository | Doel | Basiscommit | Voorgestelde versie |
| --- | --- | --- | --- |
| pronieq/tucon-dashboard | main | 6b5ed29b16c9c83c88f823fa0560520d993fd84b | pakket 1.1.0 |
| pronieq/tucon-saas | main | 0aa130c06f44f905250ae2470cfe8f12770642cb | Cloud 0.25.0 |
| pronieq/tucon | main | 2d9a64baca609434af70f77dc2d6309e28aafd85 | Player 1.13.0 |
| pronieq/tucon-home-assistant | main | af697de9676cf9b1f2f3440e62f0a3bea486b6c1 | distributie 1.13.0 |

Per repository is een eigen checkout met branch `feat/tucon-one-universal-blocks-20260908-ea74` gebruikt. De bestandsinhoud van de uitgangssnapshots is tegen de GitHub-blobhashes gecontroleerd; GitHub-commits gebruiken de echte bovengenoemde parents. Bestaande lokale werkdirectories zijn niet aangepast.

Bij aanvang zijn alle 104 niet-standaardbranches van Cloud, Player en distributie vergeleken; het dashboard had alleen main. Er stonden geen open PR’s. Er waren geen AGENTS.md-bestanden in de repositorybomen. De laatste controle vóór oplevering vond dezelfde doelcommits en geen gewijzigde andere branchheads of nieuwe andere open PR’s. Een branch zonder PR is dus meegenomen; ongepushte ontwikkeling blijft niet zichtbaar.

Bekende remote-beheertakken en raakvlakken:

| Repository | Branchhead remote-beheer | Raakvlakken met deze sprint |
| --- | --- | --- |
| tucon-saas | feat/remote-management-phase-1-2 @ e929719d597b9fad2a7ca7f1ac3e7cf609d72e3d | server/index.js, server/service.js, server/store.js, packagebestanden, CHANGELOG.md |
| tucon | feat/remote-management-phase-1-2 @ 67fd8da69087ff4a386b767585bee7470e6c6b00 | server/index.js, packagebestanden, homeassistant-app/config.yaml, documentatie |
| tucon-home-assistant | feat/remote-management-phase-1-2 @ 7701116ae0a71a623609d6f7fdd0a5b4d1103ee7 | distributiemanifest en changelog |

De remote-takken hebben ten opzichte van main een afwijkende Git-historie; dit bewijst niet dat al hun inhoud nog ontbreekt. Main bevat inmiddels remote-beheer en nieuwere verbindingsfixes. Er is niets uit die branches overgenomen. Nieuwe One-logica staat hoofdzakelijk in nieuwe modules. Remote proxy, gateway, authenticatie, workflows en branchinstellingen blijven buiten deze sprint.

De gedeelde aansluitingen, publicatiecommandonaam `configuration.apply`, configuratieversie 5, discoverymetadata, package-integriteit en releasevolgorde moeten opnieuw samen worden gecontroleerd zodra het andere traject wijzigt. Een tekstueel schone merge alleen is onvoldoende.

## Configuratie en gedrag

- Contract `tucon-one-v1.0.0`, configuratieversie 5, gedeeld pakket 1.1.0.
- Maximaal 2 slotfavorieten, 2 lampen/lichtgroepen, 4 bestaande scenes; de andere collecties hebben 1 primaire favoriet. Details bevatten alle opgenomen items.
- Stabiele bronverwijzingen voorkomen verkeerde doelen bij gelijke namen en gewijzigde volgorde. Verdwenen geselecteerde bronnen blijven bewaard; nieuw ontdekte bronnen worden niet automatisch geselecteerd.
- HA-bediening gebruikt actuele ondersteunde mogelijkheden per entiteit. API-waarden geven geen schrijfrecht. Geheimen blijven in de bestaande serverruntime.
- Dagverbruik vereist energie, passende eenheden en een bewezen/expliciet geconfigureerde dagperiode. Een onbekende meetperiode levert geen verzonnen dagwaarde op.
- Studio preview is alleen-lezen. De Local Player gebruikt bevestigde bronwaarden; een geaccepteerde opdracht wordt niet als fysieke toestand geïnterpreteerd.
- Migratie wordt als een afzonderlijk concept opgeslagen; de bestaande configuratieversie blijft bestaan. Niet-passende koppelingen krijgen een melding. Bestaande briefing, scherminstellingen, plattegronden en nieuwskaarten worden behouden. Aanvullende bestaande weergaven zijn bereikbaar via Meer; bediening daar vereist opname in One.
- Publicatie naar een Player ouder dan 1.13.0 wordt geblokkeerd. De Player valideert zelf versie/contract en bewaart een lokale backup. Cloud accepteert alleen een passend versie-ID en contract als activatiebevestiging. Een eerdere bewaarde versie kan worden geheractiveerd.
- Een afgewezen JSON-conceptopslag kan volgende opslag niet meer blijvend blokkeren. Per installatie wacht maximaal één publicatie op bevestiging; verlopen opdrachten worden niet als geslaagde activatie verwerkt.

## Verificatie

| Controle | Resultaat |
| --- | --- |
| Dashboardpakket: bestaande interactietests + contract + nieuwe componenttests | 26 geslaagd |
| Cloud: bestaande tests + publicatie, bronisolatie, tenantguard, JSON-opslagherstel | 44 geslaagd |
| Player: bestaande tests + One-activatie, lokale bediening zonder Cloud en rollback | 62 geslaagd |
| Productiebuild gedeeld React-pakket en ingebedde Studio-browserbuild | geslaagd |
| Dashboard-demo en Player-productiebuild | geslaagd |
| Syntaxcontroles en lockfilecontrole via npm ci --dry-run | geslaagd |
| Release-tag/Player-manifestcontrole voor 1.13.0 | geslaagd |

Nieuwe tests dekken 1 en 6 sloten, afwijkende volgorde en verdwenen doelen, 12 lampen met één onbereikbaar item, 8 scenes en vier favorieten, behoud bij herdetectie en heropenen, Sonos/Denon/beperkte featureprofielen, verkeerde meeteenheden en perioden, stale API-waarden, read-only preview, per-item opdrachten, exact bevestigde publicatie en heractivatie van een eerdere versie.

De tests gebruiken geïsoleerde in-memory of tijdelijke gegevens. De fysiek aangesloten Green, Sonos en Denon zijn niet benaderd. De browser-skill kon verbinden met het browserobject maar reageerde vervolgens niet op de lokale preview of herstelcontrole; daardoor zijn visuele tabletcontroles niet als geslaagd aangemerkt. Componenttests vervangen geen visuele inspectie.

De beide vendor-tarballs hebben SHA-256 `63a86c9f7acc52d7fb3a03e242bc81bb36ce695d8f9b219b510a3d7db680b8ca`; de lockfiles bevatten de bijbehorende SHA-512-integriteit. CSS, React-weergave en brondefinities komen uit één pakket. De npm-afhankelijkheden zijn lokaal vanuit de bestaande cache/installaties gebruikt; volledige schone installaties en Docker-images horen ook bij CI/releasevalidatie.

## Samenvoeging, release en activatie

1. Controleer alle doelbranches en het andere ontwikkelingstraject opnieuw. Voeg zo nodig de actuele main in de eigen branches samen, behoud beide wijzigingen en herhaal de geraakte tests.
2. Review en integreer eerst het gedeelde dashboardpakket. Controleer dat beide host-PR’s exact dezelfde geteste tarball bevatten. De private GitHub-repository hoeft tijdens Docker-build of gebruik niet bereikbaar te zijn.
3. Integreer Cloud 0.25.0 en Player 1.13.0 met de compatibiliteitscontrole intact. Bestaande v4-configuraties blijven werken; activeer One nog niet op oude Players.
4. Na een afzonderlijke release-opdracht: bouw en verifieer Player 1.13.0 voor amd64 en aarch64, inclusief manifest. Publiceer het distributiemanifest pas wanneer de bijbehorende container daadwerkelijk beschikbaar is. Dit voorkomt een HA-update naar een ontbrekende image.
5. Update eerst een pilot-Green, controleer discovery en lokale bediening. Open Studio, controleer het migratieconcept en stel de favorieten expliciet in. Publiceer pas daarna per installatie en wacht op een exacte activatiebevestiging.
6. Bij problemen: heractiveer de bewaarde configuratie via Studio; controleer de ontvangstbevestiging en de daadwerkelijke tabletweergave. De vorige lokale configuratie blijft daarnaast beschikbaar als rollbackbackup.

## Concrete resterende praktijktest

- Bekijk 1280×800, 1920×1200 en 1024×600, plus de werkelijk gebruikte tabletorientatie. Controleer lange namen, één slot, volle collecties, de woning/kantoorafbeelding en de vier scenes. Alleen details mogen door hun collectie scrollen; controleer ook touchbediening en leesbaarheid bij schaling.
- Vergelijk Studio en tablet met dezelfde configuratie en dezelfde live waarden. Controleer dat Studio geen fysieke opdrachten verstuurt.
- Controleer op een echte Green een zelfgekozen slot, een fout per apparaat, alle twaalf opgenomen lampen, en een bestaande Hue/HA-scene. Controleer in het bronsysteem dat de scene-inhoud niet is gewijzigd.
- Controleer afzonderlijk Sonos en Denon: play/pause, volume, vorige/volgende, beperkte profielen en bronselectie.
- Onderbreek alleen de Cloudverbinding en controleer lokale HA-bediening. Controleer verouderde API-waarden, herstel, activatiebevestiging en terugzetten op de echte installatie.

Er wordt geen geslaagde fysieke, Docker- of visuele test geclaimd zolang die niet is uitgevoerd. De PR’s blijven concepten totdat de resterende visuele controle is afgerond.
