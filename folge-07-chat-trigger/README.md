# Folge 7: Ein Chat für deinen KI-Agenten

Mit dem Chat Trigger wird dein Agent zum Chatbot mit eigener Seite

▶ Video: folgt

## Was du lernst

- Den Webhook gegen den Chat Trigger tauschen
- Agent und Simple Memory auf den Chat umstellen
- Den Chat direkt im n8n-Editor testen
- Eine öffentliche Chatseite mit Titel und Begrüßung einrichten
- Wofür Hosted Chat, Embedded Chat und die Anmeldung da sind

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 6](../folge-06-qdrant/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`morgenrot-chat.json`](morgenrot-chat.json) – Workflow „Morgenrot Chat“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Testfrage**

```
Wie lange kann ich mein Kaffee-Abo bei Morgenrot pausieren?
```

**Begrüßung (Initial Message)**

```
Hallo! Ich bin der Assistent der Kaffeerösterei Morgenrot. Frag mich zu Abo, Versand oder Rückgabe.
```

**Titel der Chatseite**

```
Morgenrot Kundenservice
```

**Untertitel**

```
Fragen zu Kaffee, Abo und Versand
```

**Frage im Chat**

```
Ab welchem Bestellwert ist der Versand kostenlos?
```

**Nachfrage**

```
Und was kostet er darunter?
```
