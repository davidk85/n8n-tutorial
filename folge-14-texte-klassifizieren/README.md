# Folge 14: Texte mit KI sortieren

Der Text Classifier ordnet jede Anfrage selbst einem Thema zu

▶ Video: folgt

## Was du lernst

- Den Text Classifier mit eigenen Kategorien einrichten
- Kategorien so beschreiben, dass die KI sie sicher erkennt
- Ein lokales Sprachmodell mit Ollama anhängen
- Jede Kategorie als eigenen Ausgang weiterverarbeiten
- Das Ergebnis mit Update row(s) in die Data Table schreiben

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`, Einrichtung in Folge 12
- Eine Data Table „Kontaktanfragen“ mit den Spalten name, email, anliegen und thema (Typ string), nach dem Import in den Nodes „Get row(s)“ und „Update row(s)“ auswählen

## Datenschutz

Die Anfragen enthalten Namen und Kontaktdaten, deshalb läuft die KI hier lokal mit Ollama: Nichts verlässt deinen Rechner. Nimmst du stattdessen einen Cloud-Anbieter außerhalb der EU, lies vorher [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`anfragen-sortieren.json`](anfragen-sortieren.json) – Workflow „Anfragen sortieren“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.
