# Folge 16: Fehler abfangen in n8n

Nochmal versuchen, und wenn es trotzdem scheitert, eine Mail bekommen

▶ Video: folgt

## Was du lernst

- Einen fehlgeschlagenen Node erkennen und die Fehlermeldung lesen
- Mit Retry On Fail automatisch nachversuchen
- Einen Fehler-Workflow mit dem Error Trigger bauen
- Den Fehler-Workflow in den Einstellungen eines Workflows festlegen
- Einen veröffentlichten Workflow über die Production-URL testen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)
- Nach dem Import im Workflow „Preise abrufen“ unter Settings den Error Workflow „Fehler-Alarm“ auswählen

## Dateien

- [`fehler-alarm.json`](fehler-alarm.json) – Workflow „Fehler-Alarm“
- [`preise-abrufen.json`](preise-abrufen.json) – Workflow „Preise abrufen“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Befehl aus dem Video**

```bash
curl localhost:5678/webhook-test/preise
```

**Betreff der Alarm-Mail (Expression)**

```
Fehler in {{ $json.workflow.name }}
```

**Text der Alarm-Mail (Expression)**

```
Fehler im Node {{ $json.execution.lastNodeExecuted }}: {{ $json.execution.error.message }} Zum Lauf: {{ $json.execution.url }}
```

**Befehl aus dem Video**

```bash
curl localhost:5678/webhook/preise
```
