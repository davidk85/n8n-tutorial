# Folge 17: Schleifen in n8n verstehen

Warum du meist keine brauchst, und wie Loop Over Items Pausen macht

▶ Video: folgt

## Was du lernst

- Verstehen, dass jeder Node alle Items einzeln abarbeitet
- Mit Expressions in jedem Item eigene Werte nutzen
- Items mit Loop Over Items in Pakete teilen
- Mit dem Wait-Node Pausen zwischen den Paketen machen
- Den Lauf einer Schleife in den Logs nachvollziehen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Eine Data Table „Kunden“ mit den Spalten name und email (Typ string), nach dem Import im Node „Get row(s)“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)

## Datenschutz

Werbe-Mails an Kunden brauchen in der Regel eine Einwilligung oder eine bestehende Kundenbeziehung mit Widerspruchsmöglichkeit. Die Adressen hier sind erfunden. Keine Rechtsberatung.

## Dateien

- [`kundenmail.json`](kundenmail.json) – Workflow „Kundenmail“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Feld „betreff“ im Node Edit Fields**

```
Neue Herbströstung für dich, {{ $json.name }}
```

**Text der Mail (Expression)**

```
Hallo {{ $json.name }}, unsere Herbströstung ist da. Schau gern im Laden vorbei!
```
