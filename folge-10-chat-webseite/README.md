# Folge 10: Der KI-Chatbot auf deiner Webseite

Mit Embedded Chat kommt der Chat als Sprechblase auf jede Webseite

▶ Video: https://youtu.be/WzWDTaUeHmA

## Was du lernst

- Den Unterschied zwischen Hosted Chat und Embedded Chat
- Den Chat Trigger auf Embedded Chat umstellen
- Mit Allowed Origins nur deine eigene Webseite zulassen
- Das Chatfenster mit @n8n/chat in eine Webseite einbauen
- Begrüßung, Titel und Farben im Code anpassen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 9](../folge-09-verlaessliche-antworten/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)
- Die Data Table „Kontaktanfragen“ aus Folge 8, nach dem Import im Node „Kontaktanfrage speichern“ auswählen

## Datenschutz

Was Besucher in den Chat schreiben, geht an OpenAI in die USA. Nenne den Chatbot und den KI-Anbieter in deiner Datenschutzerklärung. Seit dem 2. August 2026 verlangt der EU AI Act außerdem, dass der Chatbot sich als KI zu erkennen gibt, zum Beispiel in der Begrüßung. Mehr dazu in [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`morgenrot-chat.json`](morgenrot-chat.json) – Workflow „Morgenrot Chat“
- [`webseite.html`](webseite.html) – Beispielseite mit eingebautem Chat (DEINE-CHAT-URL durch deine Chat URL ersetzen)

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Allowed Origins (CORS) für die Beispielseite**

```
http://localhost:8080
```

**Beispielseite lokal anzeigen (im Ordner mit webseite.html ausführen, dann http://localhost:8080/webseite.html öffnen)**

```
python3 -m http.server 8080
```

**Frage im Chatfenster**

```
Wie lange kann ich mein Kaffee-Abo pausieren?
```
