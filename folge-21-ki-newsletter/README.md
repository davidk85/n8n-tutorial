# Folge 21: KI-Newsletter aus RSS-Feeds

Jeden Montag die wichtigsten Artikel der Woche, von der KI zusammengefasst

▶ Video: folgt

## Was du lernst

- Einen Workflow jede Woche zur gleichen Zeit starten
- Artikel mit RSS Read aus einem Feed holen
- Mit dem Filter nur neue Artikel behalten
- Die Artikel von einer lokalen KI zusammenfassen lassen
- Den Newsletter per Mail verschicken

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`, Einrichtung in Folge 12
- Zum Ausprobieren den Hilfs-Workflow beispiel-feed-kaffeewelt.json importieren und veröffentlichen, oder im Node „RSS Read“ die Adresse eines echten RSS-Feeds eintragen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)

## Datenschutz

Hier verarbeitet n8n nur öffentliche Artikel, keine personenbezogenen Daten. Verschickst du den Newsletter an Kunden statt an dein Team, brauchst du deren Einwilligung (Double-Opt-in). Und fremde Artikel solltest du nur kurz zusammenfassen und verlinken, nicht komplett weitergeben. Keine Rechtsberatung.

## Dateien

- [`beispiel-feed-kaffeewelt.json`](beispiel-feed-kaffeewelt.json) – Workflow „Beispiel-Feed Kaffeewelt“
- [`kaffee-news.json`](kaffee-news.json) – Workflow „Kaffee-News“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Vergleichswert im Filter (Date & Time, is after)**

```
{{ $now.minus({ days: 7 }) }}
```

**Prompt der Basic LLM Chain (Expression)**

```
Schreibe einen kurzen Wochen-Newsletter für das Team der Kaffeerösterei Morgenrot. Fasse jeden Artikel in ein bis zwei Sätzen zusammen und nenne darunter den Link. Nur einfacher Text, ohne Markdown und ohne Sternchen. Die Artikel: {{ JSON.stringify($json.data) }}
```
