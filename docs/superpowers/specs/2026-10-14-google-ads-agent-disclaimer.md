# Google Ads Agent Disclaimer — Design Spec

## Ziel
Eine öffentliche, deutschsprachige und statische Website für den internen Google-Ads-Agenten des Marrakesch Shops. Sie erklärt Funktion, Datenquellen und menschliche Freigabe und stellt Startseite, Datenschutzhinweise und Nutzungsbedingungen bereit.

## Fakten und Grenzen
- Betreiber: Marrakesch Orient & Mediterran Interior inh. Mahmoud Maataoui e.K.; vom Nutzer als identisch mit dem Shop-Impressum bestätigt.
- Domain: https://marrakeschshop.os-agentruntime.de
- Google Ads MCP: Berichte lesen und Änderungsvorschauen erstellen; menschliche Freigabe im Dashboard ist erforderlich, Agenten wenden nicht selbst an.
- Merchant Center, Search Console und Google Analytics Data API sind lesende Integrationen.
- Dashboard speichert Vorschauen, Läufe, Messwert-Snapshots und Verlauf in einer SQLite-Datenbank auf dem Server; keine automatische Aufbewahrungsfrist im Dashboard-Code gefunden.
- Claude Code übermittelt die zur Analyse nötigen Eingaben an Anthropic. Die genaue Dienst-/Kontokonfiguration und Aufbewahrung muss anhand der genutzten Anthropic-Vertragsbedingungen geprüft werden.
- Domain-Hosting des Servers ist Netcup (IP-Registrierung), der physische Serverstandort und Infrastruktur-Aufbewahrungsfristen müssen noch bestätigt werden.
- Kein Website-Tracking, keine Formulare, keine eingebetteten Drittanbieter-Ressourcen.
- Die Website selbst kann die Google-Markenprüfung oder Basic Access nicht garantieren.

## Seiten
1. Startseite: Zweck, interner Einsatz, Datenquellen und Freigabeablauf.
2. Datenschutzhinweise: Verantwortlicher, Website-Verbindungsdaten, APIs, Claude/Anthropic-Verarbeitung, Dashboard-Speicherung, Empfänger, Rechte und klar markierte noch zu bestätigende Anbieter-/Fristangaben.
3. Nutzungsbedingungen: interner Analyse- und Vorschlagsdienst; Vorschläge sind keine automatische Änderung; Freigabe durch Menschen; keine Performancegarantie. Enthält ein unmittelbar erreichbares Impressum.

## Gestaltung
Leinenweiß #F4F0E7, tiefes Petrol #153B3A, Ocker #C28A3B, Schriftfarbe #202522, gedämpftes Grün #78958A. Zurückhaltende Georgia-Überschriften und System-Sans-Serif im Fließtext; linksbündige, schmale Lesespalte. Ein Freigabeprotokoll-Motiv stellt den tatsächlichen Dreischritt Analyse → Vorschau → menschliche Freigabe dar. Keine Animation, externen Fonts oder dekorativen Dashboards.

## Betrieb
Statische Dateien werden von einem eigenen Caddy-Container im bestehenden öffentlichen Proxy-Netz ausgeliefert. Die öffentliche Caddy-Instanz terminiert TLS für die neue Domain und leitet intern zum statischen Container. Keine Änderungen am Claude-Compose-Projekt oder Neustarts bestehender Anwendungscontainer.
