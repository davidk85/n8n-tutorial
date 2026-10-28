# Folge 2: Dein erster KI-Agent in n8n

Fragen per Webhook annehmen und mit OpenAI beantworten

▶ Video: https://youtu.be/-8IJMSfUPRg

## Was du lernst

- Webhook als Eingang für einen KI-Agenten nutzen
- AI-Agent-Node mit eigenem Prompt und System Message einrichten
- OpenAI Chat Model verbinden
- Dem Agenten ein Werkzeug geben (Calculator)
- Den Agenten per curl testen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`ki-agent-per-webhook.json`](ki-agent-per-webhook.json) – Workflow „KI-Agent per Webhook“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Testfrage mit curl (bei n8n Cloud deine eigene URL einsetzen)**

```bash
curl -X POST localhost:5678/webhook-test/frage -H 'Content-Type: application/json' -d '{"frage": "Wie viele Sekunden hat ein Schaltjahr?"}'
```

**Prompt (User Message) als Expression**

```
{{ $json.body.frage }}
```

**System Message**

```
Du bist ein freundlicher Assistent. Antworte auf Deutsch in höchstens zwei Sätzen. Nutze für Berechnungen immer den Taschenrechner.
```
