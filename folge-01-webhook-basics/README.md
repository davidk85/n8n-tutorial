# Folge 1: Dein erster Webhook-Workflow

Daten empfangen, verarbeiten und direkt antworten

▶ Video: https://youtu.be/qDK0XVQvpXY

## Was du lernst

- Webhook-Trigger anlegen (POST, eigener Pfad)
- Testdaten mit curl senden
- Felder per Drag & Drop und Expressions zuordnen
- Antwort des Workflows an den Aufrufer zurückgeben

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)

## Dateien

- [`begruessung-per-webhook.json`](begruessung-per-webhook.json) – Workflow „Begrüßung per Webhook“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Test-Anfrage mit curl (bei n8n Cloud deine eigene URL einsetzen)**

```bash
curl -X POST localhost:5678/webhook-test/begruessung -H 'Content-Type: application/json' -d '{"name": "Anna"}'
```

**Expression für das Feld antwort**

```
Hallo {{ $json.body.name }}! Willkommen bei n8n.
```
