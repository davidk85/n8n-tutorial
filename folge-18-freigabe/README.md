# Folge 18: KI schreibt, Mensch gibt frei

Mit Send and Wait geht keine KI-Antwort ohne dein Okay raus

▶ Video: folgt

## Was du lernst

- Mit der Basic LLM Chain einen Antwortentwurf schreiben lassen
- Mit Send and Wait for Response eine Freigabe per Mail einholen
- Zwischen Approve und Decline unterscheiden
- Nur nach einer Freigabe an den Kunden senden
- Den Freigabe-Ablauf im Postfach testen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`, Einrichtung in Folge 12
- Eine Data Table „Kontaktanfragen“ mit den Spalten name, email und anliegen (Typ string), nach dem Import im Node „Get row(s)“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025)
- Der Freigabe-Link in der Mail nutzt die Adresse deiner n8n-Installation. Läuft n8n auf einem Server, muss WEBHOOK_URL auf dessen öffentliche Adresse zeigen.

## Datenschutz

Die KI läuft lokal mit Ollama, die Reklamation verlässt deinen Rechner nicht. Dass ein Mensch die Antwort freigibt, passt auch zur DSGVO, die bei rein automatisierten Entscheidungen mit erheblicher Wirkung zurückhaltend ist (Art. 22). Mehr zu KI und Datenschutz in [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`antwort-mit-freigabe.json`](antwort-mit-freigabe.json) – Workflow „Antwort mit Freigabe“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Prompt der Basic LLM Chain (Expression)**

```
Du arbeitest im Kundenservice der Kaffeerösterei Morgenrot. Schreibe eine kurze, freundliche Antwort auf diese Reklamation und biete Ersatz an. Unterschreibe mit: Dein Team von Morgenrot. Nur der Text der Mail, ohne Betreff und ohne Formatierung. Reklamation von {{ $json.name }}: {{ $json.anliegen }}
```

**Bedingung im IF-Node (Boolean, is true)**

```
{{ $json.data.approved }}
```
