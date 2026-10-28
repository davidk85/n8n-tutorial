# Folge 23: n8n in Docker sicher updaten

Backup, Update, Kontrolle und der Check für n8n 3.0

▶ Video: folgt

## Was du lernst

- Die laufende n8n-Version herausfinden
- Workflows mit dem n8n-CLI exportieren
- Das komplette Docker-Volume sichern
- n8n mit docker compose auf eine neue Version anheben
- Mit dem Migration Report prüfen, ob die Instanz bereit für n8n 3.0 ist

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- n8n mit der docker-compose.yml aus dem Wurzelordner dieses Repos (Folge 0), die Befehle laufen im Ordner n8n-tutorial
- Der Name des Volumes (n8n-tutorial_n8n_data) hängt vom Ordnernamen ab, prüfen mit `docker volume ls`

## Datenschutz

Ein Backup enthält alles: Workflows, Ausführungen mit Kundendaten und die Zugangsdaten samt Schlüssel. Bewahre es deshalb verschlüsselt auf, nicht unverschlüsselt in der Cloud, und lösche alte Backups nach einer festen Frist. Keine Rechtsberatung.

## Zum Kopieren

**Alle Workflows exportieren**

```bash
docker compose exec n8n n8n export:workflow --all --separate --output=/home/node/.n8n/backup/
```

**Export aus dem Container holen**

```bash
docker compose cp n8n:/home/node/.n8n/backup ./backup
```

**Befehl aus dem Video**

```
ls backup
```

**n8n anhalten**

```bash
docker compose stop n8n
```

**Volume als Archiv sichern**

```bash
docker run --rm -v n8n-tutorial_n8n_data:/daten -v "$PWD":/backup alpine:3.20 tar czf /backup/n8n-volume.tar.gz -C /daten .
```

**Befehl aus dem Video**

```
ls -lh n8n-volume.tar.gz
```

**Backup wieder einspielen (n8n vorher mit docker compose stop n8n anhalten)**

```bash
docker run --rm -v n8n-tutorial_n8n_data:/daten -v "$PWD":/backup alpine:3.20 sh -c "cd /daten && tar xzf /backup/n8n-volume.tar.gz"
```

**Neue Version festlegen**

```
echo "N8N_VERSION=2.45.5" | tee .env
```

**Neue Version laden**

```bash
docker compose pull n8n
```

**n8n mit der neuen Version starten**

```bash
docker compose up -d n8n
```

## Quellen und weiterführende Seiten

- [n8n Release Notes auf GitHub](https://github.com/n8n-io/n8n/releases)
- [n8n-Dokumentation: Docker-Installation aktualisieren](https://docs.n8n.io/hosting/installation/docker/)
- [n8n-Dokumentation: CLI-Befehle (export, import)](https://docs.n8n.io/hosting/cli-commands/)
