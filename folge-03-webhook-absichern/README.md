# Folge 3: Webhook absichern mit Header Auth

Nur wer den richtigen Token kennt, darf deinen Workflow starten

▶ Video: folgt

## Was du lernst

- Warum ein offener Webhook ein Risiko ist
- Header Auth mit eigenem Token einrichten
- Änderungen neu veröffentlichen (Publish)
- Anfragen mit und ohne Token testen
- Basic Auth, JWT, IP-Allowlist und HTTPS im Überblick

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 1](../folge-01-webhook-basics/) – diese Folge baut darauf auf

## Dateien

- [`begruessung-per-webhook.json`](begruessung-per-webhook.json) – Workflow „Begrüßung per Webhook“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Anfrage ohne Token (wird nach dem Absichern abgelehnt)**

```bash
curl -X POST localhost:5678/webhook/begruessung -H 'Content-Type: application/json' -d '{"name": "Anna"}'
```

**Sicheren Token erzeugen (Terminal)**

```bash
openssl rand -hex 32
```

**Anfrage mit Token (deinen eigenen Token einsetzen)**

```bash
curl -X POST localhost:5678/webhook/begruessung -H 'Content-Type: application/json' -H 'X-API-Key: 7f3c9a1e5b2d4f60a8c1e9b3d5f7a2c4' -d '{"name": "Anna"}'
```
