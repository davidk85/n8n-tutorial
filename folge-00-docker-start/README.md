# Folge 0: n8n mit Docker starten

Docker Desktop auf Windows oder Mac einrichten und n8n lokal starten

▶ Video: folgt

## Was du lernst

- Was Image, Container und Volume bedeuten
- Docker Desktop auf Mac und Windows installieren
- n8n mit docker compose starten
- Das n8n-Konto beim ersten Start anlegen
- n8n stoppen und aktualisieren

## Voraussetzungen

- Ein Windows-PC (10 oder 11) oder ein Mac, auf dem du Programme installieren darfst

## Zum Kopieren

**Docker Desktop herunterladen**

```
https://www.docker.com/products/docker-desktop/
```

**Docker prüfen**

```bash
docker --version
```

**Docker Compose prüfen**

```bash
docker compose version
```

**Begleit-Repo herunterladen**

```bash
git clone https://github.com/davidk85/n8n-tutorial.git
```

**In den Ordner wechseln**

```bash
cd n8n-tutorial
```

**n8n starten**

```bash
docker compose up -d
```

**n8n im Browser öffnen**

```
http://localhost:5678
```

**n8n stoppen (die Daten bleiben erhalten)**

```bash
docker compose down
```

**n8n aktualisieren (neue Images laden, dann starten)**

```bash
docker compose pull
```
