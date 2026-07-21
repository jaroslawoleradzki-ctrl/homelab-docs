# Stos AI na `ai-node`

## Zakres

- Ollama,
- Open WebUI,
- Qdrant,
- lokalny RAG w `/srv/rag`,
- OpenClaw w `/srv/compose/openclaw`.

## Kontrola podstawowa

```bash
ssh cloud@192.168.100.29
sudo docker ps --format 'table {{.Names}}\t{{.Status}}\t{{.Ports}}'
curl -fsS http://127.0.0.1:11434/api/tags
curl -fsS http://127.0.0.1:6333/collections
```

Open WebUI sprawdź w przeglądarce pod adresem LAN hosta na porcie 3000.

## Modele Ollama

```bash
sudo docker exec ollama ollama list
sudo docker exec ollama ollama ps
```

Pobranie modelu:

```bash
sudo docker exec ollama ollama pull NAZWA_MODELU
```

Przed usunięciem modelu sprawdź, czy nie jest używany przez Open WebUI lub pipeline RAG.

## Qdrant

```bash
curl -s http://127.0.0.1:6333/collections
curl -s http://127.0.0.1:6333/collections/rag_chunks_bge_m3
```

Qdrant pozostaje związany z localhostem i nie powinien być bezpośrednio wystawiany do Internetu.

## RAG

```bash
cd /srv/rag
source .venv/bin/activate
python retrieve.py
```

Przed zmianami wykonaj:

```bash
git status
```

Projekt nie musi działać stale, dopóki nie zostanie uruchomiony produkcyjny API lub automatyczny ingestion.

## OpenClaw

```bash
cd /srv/compose/openclaw
sudo docker compose ps
sudo docker compose logs --tail 100 gateway
```

Endpointy kontrolne:

```bash
curl -fsS http://127.0.0.1:18789/healthz
curl -fsS http://127.0.0.1:18789/readyz
```

Przed publikacją poza zaufany LAN należy co najmniej:

- wyłączyć `allowInsecureAuth`,
- skonfigurować ograniczanie prób logowania,
- zweryfikować dozwolone origins,
- ograniczyć narzędzia elevated i dostęp do Docker socket,
- ponowić audyt bezpieczeństwa.

## Restart

Restartuj tylko właściwy stos:

```bash
cd /srv/compose/NAZWA_STOSU
sudo docker compose restart
sudo docker compose ps
```

Nie używaj `docker system prune --volumes` podczas standardowej diagnostyki.