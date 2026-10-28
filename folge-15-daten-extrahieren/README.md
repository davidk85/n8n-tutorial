# Folge 15: Daten aus Text ziehen mit KI

Der Information Extractor macht aus Nachrichten saubere Datensätze

▶ Video: folgt

## Was du lernst

- Den Information Extractor mit eigenen Feldern einrichten
- Felder mit Typ und Beschreibung festlegen
- Ein lokales Sprachmodell mit Ollama anhängen
- Die Felder mit Insert row in eine Data Table schreiben

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`, Einrichtung in Folge 12
- Zwei Data Tables: „Bestellmails“ mit den Spalten absender und nachricht, „Bestellungen“ mit kunde, produkt (Text), menge_kg (Zahl) und lieferdatum (Text); nach dem Import in den Data-Table-Nodes auswählen

## Datenschutz

Bestellungen enthalten Namen und Kontaktdaten, deshalb läuft die KI hier lokal mit Ollama. Nimmst du einen Cloud-Anbieter außerhalb der EU, lies vorher [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`bestellungen-auslesen.json`](bestellungen-auslesen.json) – Workflow „Bestellungen auslesen“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.
