# Folge 22: Sub-Workflows als Bausteine

Einmal bauen, aus jedem Workflow aufrufen

▶ Video: folgt

## Was du lernst

- Einen Sub-Workflow mit festen Eingabefeldern bauen
- Die Eingaben im Sub-Workflow mit Expressions nutzen
- Einen Sub-Workflow mit Execute Sub-workflow aufrufen
- Werte an den Sub-Workflow übergeben
- Verstehen, wann sich ein Baustein lohnt

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Eine Data Table „Kunden“ mit den Spalten name und email (Typ string), nach dem Import im Node „Get row(s)“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)
- Erst den Workflow „Mail-Baustein“ importieren, dann im Workflow „Herbst-Aktion“ im Node „Execute Sub-workflow“ den Mail-Baustein auswählen

## Datenschutz

Werbe-Mails an Kunden brauchen in der Regel eine Einwilligung oder eine bestehende Kundenbeziehung mit Widerspruchsmöglichkeit. Ein zentraler Mail-Baustein hilft übrigens auch hier: Den Abmelde-Hinweis musst du nur an einer Stelle pflegen. Keine Rechtsberatung.

## Dateien

- [`herbst-aktion.json`](herbst-aktion.json) – Workflow „Herbst-Aktion“
- [`mail-baustein.json`](mail-baustein.json) – Workflow „Mail-Baustein“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Text im Mail-Baustein (Expression)**

```
Hallo {{ $json.name }}, {{ $json.nachricht }} Dein Team von Morgenrot
```
