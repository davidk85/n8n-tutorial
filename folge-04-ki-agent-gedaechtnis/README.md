# Folge 4: Gib deinem KI-Agenten ein Gedächtnis

Simple Memory und Session-ID: Der Agent merkt sich jedes Gespräch

▶ Video: https://youtu.be/yFSruTeIPzI

## Was du lernst

- Warum ein KI-Agent ohne Memory alles vergisst
- Simple Memory an den AI-Agent-Node anschließen
- Session-ID per Expression aus dem Webhook-Body holen
- Gedächtnis per curl testen
- Getrennte Gespräche pro Session-ID
- Wann Postgres oder Redis Chat Memory besser sind

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 2](../folge-02-ki-agent/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`ki-agent-per-webhook.json`](ki-agent-per-webhook.json) – Workflow „KI-Agent per Webhook“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Ohne Session-ID vorstellen**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"frage": "Hallo, ich heiße Anna."}'
```

**Ohne Session-ID nachfragen**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"frage": "Wie heiße ich?"}'
```

**Session-ID als Expression (Feld Key)**

```
{{ $json.body.sessionId }}
```

**Mit Session-ID vorstellen**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "anna", "frage": "Hallo, ich heiße Anna."}'
```

**In derselben Session nachfragen**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "anna", "frage": "Wie heiße ich?"}'
```

**Andere Session-ID (eigenes Gedächtnis)**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "ben", "frage": "Wie heiße ich?"}'
```
