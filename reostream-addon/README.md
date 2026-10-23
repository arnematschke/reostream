# reostream als Home Assistant Add-on

Dieses Add-on verpackt das veröffentlichte Multiarch-Image von reostream. Die Weboberfläche wird über Home Assistant Ingress geöffnet. HTTP- und RTSP-Streams werden als Ports des Add-ons bereitgestellt.

## Installation

1. In Home Assistant unter **Einstellungen → Add-ons → Add-on-Store** das Menü öffnen und **Repositories** auswählen.
2. `https://github.com/VoltTech21/reostream` als Repository hinzufügen.
3. **reostream** installieren und starten.
4. Im Add-on-Protokoll den einmaligen Claim-Token ablesen.
5. Über **Web UI öffnen** die Claim-Seite aufrufen und den Token eingeben. Danach das vorgeschlagene Passwort sicher speichern.
6. Kameras in der Weboberfläche hinzufügen. Der Reolink-Baichuan-Port 9000 muss vom Add-on aus erreichbar sein.

Die Konfiguration wird in Home Assistants persistentem Add-on-Datenverzeichnis unter `/data` gespeichert.

## Streams

Die Ports 8560 (HTTP-MPEG-TS) und 8561 (RTSP) sind auf den gleichnamigen Host-Ports veröffentlicht. Verwende in einem LAN-Client die Adresse deines Home-Assistant-Hosts:

- `http://<home-assistant-host>:8560/<kamera>.ts`
- `rtsp://<home-assistant-host>:8561/<kamera>`

Wenn du die Add-on-Ports in der Add-on-Konfiguration änderst, müssen die URLs entsprechend angepasst werden. Ingress stellt die Bedienoberfläche bereit; für Streams wird weiterhin die Host-Adresse mit den veröffentlichten Ports verwendet.

## Hinweise

- Unterstützte Plattformen: Home Assistant OS auf amd64 und aarch64.
- Dieses Add-on bezieht `ghcr.io/volttech21/reostream`; die Veröffentlichung und Multiarch-Images werden vom Hauptrepository gepflegt.
- Zugangsdaten und Kamerakonfigurationen werden vom reostream-Dienst im persistenten `/data` verwaltet, nicht als Add-on-Optionen.
