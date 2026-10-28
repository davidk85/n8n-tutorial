# Folge 11: Jeden Morgen ein Tagesbericht per Mail

Mit dem Schedule Trigger startet ein Workflow nach Zeitplan

▶ Video: folgt

## Was du lernst

- Einen Workflow mit dem Schedule Trigger jeden Morgen starten
- Mit einer Bedingung nur die Zeilen der letzten 24 Stunden holen
- Mehrere Items mit Aggregate zu einer Liste zusammenfassen
- Mit der Basic LLM Chain einen Bericht schreiben lassen
- Eine E-Mail per SMTP verschicken
- Einen Lauf in den Logs nachvollziehen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)
- Eine Data Table „Kontaktanfragen“ mit den Spalten name, email und anliegen (Typ string), nach dem Import im Node „Get row(s)“ auswählen
- Ein SMTP-Zugang: zum Testen Mailpit aus der docker-compose.yml (Host mailpit, Port 1025, SSL aus, Postfach unter http://localhost:8025), sonst die SMTP-Daten deines Mail-Anbieters

## Dateien

- [`tagesbericht.json`](tagesbericht.json) – Workflow „Tagesbericht“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Bedingung im Node „Get row(s)“ (createdAt, Greater Than)**

```
{{ $now.minus({ days: 1 }) }}
```

**Prompt der Basic LLM Chain (Expression)**

```
Schreibe den Tagesbericht für das Team der Kaffeerösterei Morgenrot. Fasse jede neue Kontaktanfrage in einem Satz zusammen, mit Name und E-Mail-Adresse. Nenne kein Datum. Nur Text, ohne Formatierung. Die Anfragen: {{ JSON.stringify($json.data) }}
```

**SMTP-Zugang zum Testen (Mailpit aus der docker-compose.yml)**

```
Host: mailpit · Port: 1025 · SSL/TLS: aus · User und Password leer
```

**Absender, Empfänger und Betreff**

```
bericht@morgenrot.example · team@morgenrot.example · Tagesbericht: neue Kontaktanfragen
```
