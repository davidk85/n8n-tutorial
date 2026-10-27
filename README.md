# n8n-Tutorials von ToolVibes

Begleitmaterial zu den n8n-Tutorials auf dem YouTube-Kanal **ToolVibes**: Workflows zum Importieren,
Beispieldateien und alle Befehle aus den Videos zum Kopieren. Jede Folge hat einen eigenen Ordner mit Anleitung.

## Folgen

| Folge | Thema | Level |
|---|---|---|
| 1 | [Dein erster Webhook-Workflow](folge-01-webhook-basics/) | Einsteiger |
| 2 | [Dein erster KI-Agent in n8n](folge-02-ki-agent/) | Einsteiger |
| 3 | [Webhook absichern mit Header Auth](folge-03-webhook-absichern/) | Einsteiger |
| 4 | [Gib deinem KI-Agenten ein Gedächtnis](folge-04-ki-agent-gedaechtnis/) | Einsteiger |
| 5 | [RAG: KI-Agent mit eigenen Dokumenten](folge-05-rag-dokumente/) | Einsteiger |

## n8n starten

Du brauchst [Docker Desktop](https://www.docker.com/products/docker-desktop/). Dann im Ordner dieses Repos:

```bash
docker compose up -d
```

Danach http://localhost:5678 öffnen und beim ersten Start ein Konto anlegen. Die Videos nutzen
n8n 2.44.7. Eine andere Version stellst du in `docker-compose.yml` ein.

Stoppen mit `docker compose down`. Deine Workflows bleiben im Docker-Volume `n8n_data` erhalten.

## Hinweise

- Die Workflow-Dateien enthalten keine Zugangsdaten. Nach dem Import wählst du in den betroffenen Nodes deine eigenen aus.
- Tokens und Beispieldaten in den Videos sind nur Beispiele. Firmen wie die „Kaffeerösterei Morgenrot“ sind erfunden.
- Die Befehle nutzen `localhost:5678`. Läuft dein n8n woanders, setze deine eigene Adresse ein.
