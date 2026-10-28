# Folge 8: Der Chatbot nimmt Kontaktanfragen auf

Mit einer Data Table als Werkzeug speichert der Agent Anfragen selbst

▶ Video: https://youtu.be/_38KBTYmRqo

## Was du lernst

- Eine Data Table in n8n anlegen
- Die Tabelle dem Agenten als Werkzeug geben
- Felder mit „Defined by agent“ vom Modell füllen lassen
- Dem Agenten im Systemprompt sagen, wann er das Werkzeug nutzt
- Eine Kontaktanfrage im Chat aufnehmen und in der Tabelle prüfen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 7](../folge-07-chat-trigger/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)
- Eine Data Table „Kontaktanfragen“ mit den Spalten name, email und anliegen (Typ string), nach dem Import im Node „Kontaktanfrage speichern“ auswählen

## Datenschutz

Die Anfragen enthalten Namen und E-Mail-Adressen, also personenbezogene Daten. Der Chatverlauf geht dabei an OpenAI in die USA. Was die DSGVO dafür verlangt und wie du weniger Daten an die KI gibst, zeigt [Folge 12](../folge-12-dsgvo/). Keine Rechtsberatung.

## Dateien

- [`morgenrot-chat.json`](morgenrot-chat.json) – Workflow „Morgenrot Chat“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Spalten der Tabelle (Typ string)**

```
name, email, anliegen
```

**Beschreibung für das Werkzeug**

```
Speichert eine Kontaktanfrage mit Name, E-Mail-Adresse und Anliegen.
```

**Ergänzung im Systemprompt**

```
Möchte jemand beraten werden oder Kontakt aufnehmen, frag nach Name und E-Mail-Adresse. Das Anliegen übernimmst du aus dem Gespräch. Dann speicherst du die Anfrage und bestätigst sie.
```

**Frage im Chat**

```
Ich möchte für unser Büro regelmäßig größere Mengen Kaffee bestellen. Kann mich jemand beraten?
```

**Antwort mit Kontaktdaten**

```
Anna Beispiel, anna@example.com
```
