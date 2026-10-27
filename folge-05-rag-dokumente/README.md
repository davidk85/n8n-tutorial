# Folge 5: RAG: KI-Agent mit eigenen Dokumenten

Dokumente hochladen, im Vector Store speichern und gezielt abfragen

▶ Video: folgt

## Was du lernst

- Was RAG ist und wofür man einen Vector Store braucht
- Ein Upload-Formular mit dem n8n Form Trigger bauen
- Dokumente mit Embeddings OpenAI in den Simple Vector Store schreiben
- Den Vector Store als Werkzeug an den KI-Agenten hängen
- Den Agenten Fragen zum eigenen Dokument beantworten lassen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 4](../folge-04-ki-agent-gedaechtnis/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`dokumente-einlesen.json`](dokumente-einlesen.json) – Workflow „Dokumente einlesen“
- [`ki-agent-per-webhook.json`](ki-agent-per-webhook.json) – Workflow „KI-Agent per Webhook“
- [`morgenrot-kundeninfo.pdf`](morgenrot-kundeninfo.pdf) – Beispieldokument zum Hochladen (erfundene Kaffeerösterei)

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Frage an den Agenten**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "anna", "frage": "Wie lange kann ich mein Kaffee-Abo bei Morgenrot pausieren?"}'
```

**Formular zum Hochladen (erst nach dem Veröffentlichen erreichbar)**

```
http://localhost:5678/form/dokumente
```

**Beschreibung für das Werkzeug**

```
Kundeninformationen der Kaffeerösterei Morgenrot: Öffnungszeiten, Versand, Abo, Rückgabe und Maschinen.
```

**Zweite Frage zum Dokument**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "anna", "frage": "Ab wann ist der Versand kostenlos?"}'
```
