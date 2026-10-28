# Folge 19: Rechnungen automatisch auslesen

PDF hochladen, die KI liest Betrag und Fälligkeit, n8n trägt sie ein

▶ Video: folgt

## Was du lernst

- Ein Formular mit Datei-Upload bauen
- Mit Extract from File den Text aus einer PDF holen
- Mit dem Information Extractor Rechnungsdaten auslesen
- Ein lokales Sprachmodell mit Ollama nutzen
- Die Daten mit Insert row in eine Data Table schreiben

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`, Einrichtung in Folge 12
- Eine Data Table „Rechnungen“ mit den Spalten lieferant, rechnungsnummer, rechnungsdatum, faellig_am (Text) und betrag_brutto (Zahl), nach dem Import im Node „Insert row“ auswählen
- Die Beispielrechnung rechnung-gruenkaffee.pdf aus diesem Ordner

## Datenschutz

Rechnungen enthalten Firmen- und oft auch Personendaten, Bankverbindungen und Beträge. Deshalb läuft die KI hier lokal mit Ollama. Für echte Buchhaltung gelten außerdem Aufbewahrungspflichten, die PDF selbst solltest du also zusätzlich revisionssicher ablegen. Mehr zu KI und Datenschutz in [Folge 12](../folge-12-dsgvo/). Keine Rechts- oder Steuerberatung.

## Dateien

- [`rechnungen-auslesen.json`](rechnungen-auslesen.json) – Workflow „Rechnungen auslesen“
- [`rechnung-gruenkaffee.pdf`](rechnung-gruenkaffee.pdf) – Beispielrechnung zum Hochladen (erfundene Firmen und Daten)

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Text im Information Extractor (Expression)**

```
{{ $json.text }}
```

**Werte in Insert row (je Spalte, hier lieferant)**

```
{{ $json.output.lieferant }}
```
