# Folge 20: Dein eigenes Bestellformular

Formular, Bestätigungsmail und Danke-Seite, ohne Google Forms

▶ Video: folgt

## Was du lernst

- Ein Formular mit dem Form Trigger bauen
- Felder für Text, E-Mail, Auswahlliste und Zahl anlegen
- Bestellungen mit Insert row speichern
- Eine Bestätigung per Mail schicken
- Eine Danke-Seite mit Form Ending zeigen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Eine Data Table „Bestellungen“ mit den Spalten name, email, sorte (Text) und kilo (Zahl), nach dem Import im Node „Insert row“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)

## Datenschutz

Ein Formular, das Namen und E-Mail-Adressen sammelt, braucht einen Hinweis auf deine Datenschutzerklärung, zum Beispiel in der Form Description. Dafür, dass die Daten auf deinem eigenen Server bleiben, ist n8n aber eine gute Wahl. Keine Rechtsberatung.

## Dateien

- [`bestellformular.json`](bestellformular.json) – Workflow „Bestellformular“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Werte in Insert row (je Spalte, hier name)**

```
{{ $json.Name }}
```

**Text der Bestätigung (Expression)**

```
Hallo {{ $json.name }}, wir haben deine Bestellung erhalten: {{ $json.kilo }} kg {{ $json.sorte }}. Dein Team von Morgenrot
```
