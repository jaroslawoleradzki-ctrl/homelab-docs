# Kontrola stanu środowiska

## Cel

Szybkie sprawdzenie hostów `homelab` i `ai-node` przed aktualizacją, po restarcie albo podczas diagnostyki.

## HomeLab

```bash
ssh cloud@192.168.100.22
hostnamectl
uptime
ip -br address
df -h /
sudo zpool status
sudo zfs list
sudo docker ps --format 'table {{.Names}}\t{{.Status}}\t{{.Ports}}'
systemctl --failed
sudo ufw status verbose
```

Sprawdź temperatury i dyski:

```bash
sensors
sudo smartctl -H /dev/sda
sudo smartctl -H /dev/sdb
```

## AI-node

```bash
ssh cloud@192.168.100.29
hostnamectl
uptime
ip -br address
df -h /
sudo docker ps --format 'table {{.Names}}\t{{.Status}}\t{{.Ports}}'
systemctl --failed
sudo ufw status verbose
```

Sprawdź stos AI:

```bash
curl -fsS http://127.0.0.1:11434/api/tags
curl -fsS http://127.0.0.1:6333/collections
sudo docker logs --tail 50 open-webui
```

OpenClaw:

```bash
cd /srv/compose/openclaw
sudo docker compose ps
sudo docker compose logs --tail 50 gateway
```

## Kryteria poprawnego stanu

- brak zdegradowanej puli ZFS,
- brak usług w `failed`,
- kluczowe kontenery mają status `Up` lub `healthy`,
- dostępny jest DNS przez Pi-hole i Unbound,
- Open WebUI odpowiada w LAN,
- Ollama zwraca listę modeli,
- Qdrant zwraca listę kolekcji.

Nie naprawiaj kilku niezależnych problemów naraz. Najpierw zapisz stan i wybierz jeden incydent.