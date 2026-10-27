# n8n-Tutorials von ToolVibes

Begleitmaterial zu den n8n-Tutorials auf dem YouTube-Kanal **ToolVibes**: Workflows zum Importieren,
Beispieldateien und alle Befehle aus den Videos zum Kopieren. Jede Folge hat einen eigenen Ordner mit Anleitung.

## Folgen

| Folge | Thema | Level |
|---|---|---|
| 0 | [n8n mit Docker starten](folge-00-docker-start/) | Einsteiger |
| 1 | [Dein erster Webhook-Workflow](folge-01-webhook-basics/) | Einsteiger |
| 2 | [Dein erster KI-Agent in n8n](folge-02-ki-agent/) | Einsteiger |
| 3 | [Webhook absichern mit Header Auth](folge-03-webhook-absichern/) | Einsteiger |
| 4 | [Gib deinem KI-Agenten ein Gedächtnis](folge-04-ki-agent-gedaechtnis/) | Einsteiger |
| 5 | [RAG: KI-Agent mit eigenen Dokumenten](folge-05-rag-dokumente/) | Einsteiger |
| 6 | [Dokumente dauerhaft speichern mit Qdrant](folge-06-qdrant/) | Fortgeschritten |
| 7 | [Ein Chat für deinen KI-Agenten](folge-07-chat-trigger/) | Einsteiger |
| 8 | [Der Chatbot nimmt Kontaktanfragen auf](folge-08-kontaktanfragen/) | Einsteiger |
| 9 | [Verlässliche Antworten vom KI-Chatbot](folge-09-verlaessliche-antworten/) | Einsteiger |
| 10 | [Der KI-Chatbot auf deiner Webseite](folge-10-chat-webseite/) | Einsteiger |

## n8n starten

Du brauchst [Docker Desktop](https://www.docker.com/products/docker-desktop/). Dann im Ordner dieses Repos:

```bash
docker compose up -d
```

Danach http://localhost:5678 öffnen und beim ersten Start ein Konto anlegen. Die Videos nutzen
n8n 2.44.7. Eine andere Version stellst du in `docker-compose.yml` ein.

Das startet n8n und Qdrant (Vektordatenbank ab Folge 6). Nur n8n: `docker compose up -d n8n`.

Stoppen mit `docker compose down`. Deine Workflows und Dokumente bleiben in den Docker-Volumes erhalten.

## Hinweise

- Die Workflow-Dateien enthalten keine Zugangsdaten. Nach dem Import wählst du in den betroffenen Nodes deine eigenen aus.
- Tokens und Beispieldaten in den Videos sind nur Beispiele. Firmen wie die „Kaffeerösterei Morgenrot“ sind erfunden.
- Die Befehle nutzen `localhost:5678`. Läuft dein n8n woanders, setze deine eigene Adresse ein.
