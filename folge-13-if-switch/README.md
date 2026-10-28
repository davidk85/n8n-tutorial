# Folge 13: IF und Switch: Anfragen verteilen

Mit Bedingungen entscheidet dein Workflow selbst, wohin es geht

▶ Video: folgt

## Was du lernst

- Mit dem IF-Node eine Ja-oder-Nein-Frage stellen
- Den true- und den false-Zweig verstehen
- Mit dem Switch-Node auf mehrere Wege verteilen
- Einen Fallback-Ausgang für alles andere anlegen
- Einen Node kopieren und neu verbinden
- Den Lauf mit Item-Zahlen an jedem Zweig nachvollziehen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Eine Data Table „Kontaktanfragen“ mit den Spalten name, email, thema und anliegen (Typ string), nach dem Import im Node „Get row(s)“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)

## Datenschutz

Hier geht nichts an eine KI. Die Anfragen bleiben in deinem n8n und gehen per Mail an interne Adressen. Verschickst du über einen externen Mail-Anbieter, ist er Auftragsverarbeiter, mehr dazu in [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`anfragen-verteilen.json`](anfragen-verteilen.json) – Workflow „Anfragen verteilen“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Betreff (Expression)**

```
Neue Anfrage: {{ $json.thema }}
```

**Text der Mail (Expression)**

```
Von {{ $json.name }}, {{ $json.email }}: {{ $json.anliegen }}
```
