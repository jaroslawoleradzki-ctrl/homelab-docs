# HomeLab

Repozytorium zawiera dokumentację infrastruktury HomeLab oraz AI-node.

## Cel

Środowisko służy jako prywatna platforma do:

- przechowywania plików i kopii zapasowych,
- hostowania usług domowych,
- zarządzania dokumentami, projektami i zdjęciami,
- monitoringu infrastruktury,
- lokalnego środowiska AI,
- eksperymentów z RAG i agentami,
- utrzymywania mirrorów repozytoriów Git.

## Hosty

| Host | Adres LAN | System | Rola |
|---|---|---|---|
| `homelab` | `192.168.100.22` | Ubuntu Server 24.04 LTS | storage ZFS, usługi domowe, DNS, monitoring i backup |
| `ai-node` | `192.168.100.29` | Ubuntu Server 26.04 LTS | lokalne modele AI, embeddingi, Qdrant, RAG i OpenClaw |

## Aktualny stan

### HomeLab

- HP EliteDesk 800 G3 SFF,
- Docker i Docker Compose,
- ZFS Mirror `tank` na 2 × WD Red Plus 6 TB,
- Nextcloud i Collabora,
- Immich,
- OpenProject,
- Stirling PDF,
- Pi-hole + Unbound,
- Nginx Proxy Manager,
- Homepage,
- Beszel i Uptime Kuma,
- Portainer,
- Tailscale,
- snapshoty ZFS przez Sanoid,
- monitoring SMART,
- Time Machine i backup Fedora,
- mirrory repozytoriów Git w `tank/git`.

### AI-node

- Minisforum AI X1,
- Ubuntu Server 26.04 LTS,
- Ollama z akceleracją Vulkan na Radeon 780M,
- Open WebUI,
- Qdrant związany lokalnie,
- Gemma 4 i BGE-M3,
- projekt lokalnego RAG w `/srv/rag`,
- Docling i RapidOCR,
- OpenClaw uruchomiony w Dockerze.

## Dokumentacja

### Architektura

- [Przegląd środowiska](architecture/overview.md)
- [Sieć](architecture/network.md)
- [AI-node](architecture/ai-node.md)
- [Storage](architecture/storage.md)
- [Backup](architecture/backup.md)

### Inwentaryzacja

- [Hosty](inventory/hosts.md)
- [Usługi](inventory/services.md)
- [Dashboard](inventory/dashboard.md)
- [Dług techniczny](inventory/technical-debt.md)

### Projekty

- [Lokalny RAG](projects/local-rag.md)

### Runbooki

- [Indeks runbooków](runbooks/README.md)
- [Nextcloud](runbooks/nextcloud.md)
- [Konfiguracja storage](runbooks/storage-setup.md)
- [Unbound](runbooks/unbound.md)
- [Kontrola stanu środowiska](runbooks/health-check.md)
- [Aktualizacja stosu Docker Compose](runbooks/docker-compose-update.md)
- [Mirrory repozytoriów Git](runbooks/git-mirrors.md)
- [Wake-on-LAN](runbooks/wake-on-lan.md)
- [Stos AI](runbooks/ai-stack.md)

### Zarządzanie rozwojem

- [Roadmap](ROADMAP.md)
- [Historia zmian](CHANGELOG.md)

## Zasady dokumentacji

Każda trwała zmiana infrastruktury:

1. jest projektowana,
2. jest wdrażana,
3. jest weryfikowana,
4. jest opisywana w dokumentacji,
5. kończy się commitem Git i synchronizacją mirrora.

Dane szybkozmienne, takie jak liczba kontenerów, wersje obrazów i zajętość storage, należy potwierdzać poleceniami diagnostycznymi zamiast utrzymywać jako stałe wartości w dokumentacji.

_Ostatni audyt dokumentacji: 2026-07-21._