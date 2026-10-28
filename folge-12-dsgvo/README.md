# Folge 12: KI-Workflows und die DSGVO

Nummern statt Namen, Platzhalter und ein lokales KI-Modell

▶ Video: folgt

> Wichtig: Das ist keine Rechtsberatung. Das Video gibt den Wissensstand von Oktober 2026 wieder, Gesetze und ihre Auslegung ändern sich. Für deinen konkreten Fall frag deine Datenschutzbeauftragte oder einen Anwalt.

## Was du lernst

- Erkennen, welche personenbezogenen Daten ein Workflow an die KI schickt
- Was die DSGVO bei KI-Anbietern außerhalb der EU verlangt (Überblick)
- Mit Edit Fields Nummern statt Namen an die KI geben
- Mit Guardrails E-Mail-Adressen und Telefonnummern im Text ersetzen
- Ein lokales Sprachmodell mit Ollama in n8n nutzen
- Namen nach der KI wieder einsetzen

## Voraussetzungen

- Ein laufendes n8n, zum Beispiel lokal mit Docker: [n8n starten](../README.md#n8n-starten)
- Der Workflow aus [Folge 11](../folge-11-tagesbericht/) – diese Folge baut darauf auf
- Ollama auf deinem Rechner (https://ollama.com/download) mit dem Modell ministral-3:3b: `ollama pull ministral-3:3b`
- n8n in Docker erreicht Ollama unter http://host.docker.internal:11434 (die docker-compose.yml im Wurzelordner ist dafür eingerichtet)
- Die Data Table „Kontaktanfragen“ und der SMTP-Zugang aus Folge 11

## Dateien

- [`tagesbericht.json`](tagesbericht.json) – Workflow „Tagesbericht“

## Workflow importieren

1. JSON-Datei öffnen und den gesamten Inhalt kopieren (auf GitHub: Button „Copy raw file“).
2. In n8n einen neuen, leeren Workflow öffnen und mit Strg+V (Mac: Cmd+V) einfügen.
3. Nodes mit Zugangsdaten öffnen und deine eigenen auswählen – die Dateien enthalten keine.
4. Speichern und oben rechts mit „Publish“ veröffentlichen, damit die Production-URLs funktionieren.

## Zum Kopieren

**Feld „anfrage“ im Node Edit Fields**

```
Anfrage {{ $json.id }}: {{ $json.anliegen }}
```

**Text To Check im Guardrails-Node (Expression)**

```
{{ JSON.stringify($json.data) }}
```

**Neuer Prompt der Basic LLM Chain (Expression)**

```
Schreibe den Tagesbericht für das Team der Kaffeerösterei Morgenrot. Fasse jede Anfrage in einem Satz zusammen und beginne mit ihrer Nummer, zum Beispiel: Anfrage 3: … Nenne kein Datum. Nur Text, ohne Formatierung. Die Anfragen: {{ $json.guardrailsInput }}
```

**Modell in Ollama laden**

```bash
ollama pull ministral-3:3b
```

**Base URL im Ollama-Zugang (n8n in Docker, Ollama auf dem Rechner)**

```
http://host.docker.internal:11434
```

**Kontakte im Text des Send-Email-Nodes (nach dem Bericht der KI)**

```
{{ $('Get row(s)').all().map(function (r) { return 'Anfrage ' + r.json.id + ': ' + r.json.name + ', ' + r.json.email }).join('\n') }}
```

## Quellen und weiterführende Seiten

- [DSGVO, Verordnung (EU) 2016/679 (EUR-Lex)](https://eur-lex.europa.eu/eli/reg/2016/679/oj?locale=de)
- [EU AI Act, Verordnung (EU) 2024/1689 (EUR-Lex)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj?locale=de)
- [Cloud and AI Development Act, Vorschlag der EU-Kommission vom Juni 2026](https://digital-strategy.ec.europa.eu/en/library/proposal-cloud-and-ai-development-act-cada)
- [Datenübermittlung in die USA, EU-Kommission](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/eu-us-data-transfers_de)
- [Data Privacy Framework, Liste der teilnehmenden Firmen](https://www.dataprivacyframework.gov/list)
- [Orientierungshilfe KI und Datenschutz der Datenschutzkonferenz (DSK)](https://www.datenschutzkonferenz-online.de/media/oh/20240506_DSK_Orientierungshilfe_KI_und_Datenschutz.pdf)
- [OpenAI Data Processing Addendum](https://openai.com/policies/data-processing-addendum/)
- [n8n-Dokumentation zum Guardrails-Node](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-langchain.guardrails/)
- [Ollama herunterladen](https://ollama.com/download)
