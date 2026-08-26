# Changelog

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
