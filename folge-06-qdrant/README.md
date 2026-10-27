# Folge 6: Dokumente dauerhaft speichern mit Qdrant

Ein Vector Store, der einen Neustart übersteht

▶ Video: folgt

## Was du lernst

- Warum der Simple Vector Store nach einem Neustart leer ist
- Qdrant per Docker Compose neben n8n starten
- Zugangsdaten für Qdrant in n8n anlegen
- Den Vector Store austauschen, ohne den Workflow neu zu bauen
- Gespeicherte Abschnitte im Qdrant-Dashboard ansehen
- Prüfen, dass die Daten einen Neustart überstehen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 5](../folge-05-rag-dokumente/) – diese Folge baut darauf auf
- Ein API-Schlüssel von OpenAI (in n8n unter Credentials als „OpenAI“ anlegen)

## Dateien

- [`dokumente-einlesen.json`](dokumente-einlesen.json) – Workflow „Dokumente einlesen“
- [`ki-agent-per-webhook.json`](ki-agent-per-webhook.json) – Workflow „KI-Agent per Webhook“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Befehl aus dem Video**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "anna", "frage": "Wie lange kann ich mein Kaffee-Abo bei Morgenrot pausieren?"}'
```

**Befehl aus dem Video**

```bash
docker compose up -d qdrant
```

**Qdrant-Dashboard**

```
http://localhost:6333/dashboard
```

**Qdrant URL in den Zugangsdaten (wenn n8n und Qdrant im selben docker-compose laufen)**

```
http://qdrant:6333
```

**Formular zum Hochladen**

```
http://localhost:5678/form/dokumente
```

**Beschreibung für das Werkzeug**

```
Kundeninformationen der Kaffeerösterei Morgenrot: Öffnungszeiten, Versand, Abo, Rückgabe und Maschinen.
```

**Frage an den Agenten**

```bash
curl -X POST localhost:5678/webhook/frage -H 'Content-Type: application/json' -d '{"sessionId": "ben", "frage": "Wie lange kann ich mein Kaffee-Abo bei Morgenrot pausieren?"}'
```

**Befehl aus dem Video**

```bash
docker compose restart n8n
```
