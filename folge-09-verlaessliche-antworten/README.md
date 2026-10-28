# Folge 9: Verlässliche Antworten vom KI-Chatbot

Klarer Systemprompt statt erfundener Antworten, geprüft mit Testfragen

▶ Video: https://youtu.be/HIIIbqsjcec

## Was du lernst

- Woran du erfundene Antworten deines Agenten erkennst
- Einen Systemprompt mit Rolle und klaren Regeln aufbauen
- Den Agenten nur aus seinen Dokumenten antworten lassen
- Fremde Themen freundlich ablehnen lassen
- Mit drei Testfragen prüfen, ob der Prompt wirkt

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 8](../folge-08-kontaktanfragen/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`morgenrot-chat.json`](morgenrot-chat.json) – Workflow „Morgenrot Chat“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Testfrage: steht nicht im Dokument**

```
Habt ihr auch entkoffeinierten Kaffee?
```

**Testfrage: hat nichts mit Kaffee zu tun**

```
Schreib mir ein kurzes Gedicht über Katzen.
```

**Systemprompt (komplett)**

```
Du bist der Kundenservice der Kaffeerösterei Morgenrot. Antworte auf Deutsch, freundlich, per du und in höchstens drei Sätzen.

Regeln:
1. Fragen zu Morgenrot beantwortest du nur mit dem Werkzeug für die Kundeninformationen. Steht die Antwort dort nicht, sag ehrlich, dass du es nicht weißt, und biete eine Kontaktanfrage an. Erfinde nie Produkte, Preise oder Termine.
2. Fragen ohne Bezug zu Morgenrot oder Kaffee lehnst du freundlich ab.
3. Möchte jemand beraten werden oder Kontakt aufnehmen, frag nach Name und E-Mail-Adresse und übernimm das Anliegen aus dem Gespräch. Speichere die Anfrage und sag danach nur, dass sich das Team per E-Mail meldet.
4. Musst du etwas ausrechnen, nutze den Taschenrechner.
```

**Testfrage: steht im Dokument**

```
Wie lange habe ich Zeit, ungeöffnete Ware zurückzugeben?
```
