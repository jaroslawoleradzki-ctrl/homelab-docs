# HomeLab

Repozytorium zawiera dokumentację infrastruktury HomeLab oraz AI-node.

## Cel

Środowisko służy jako prywatna platforma do:

- przechowywania plików i kopii zapasowych,
- zarządzania dokumentami i zdjęciami,
- hostowania usług domowych,
- monitoringu infrastruktury,
- lokalnego środowiska AI,
- eksperymentów z RAG i automatyzacją.

## Hosty

| Host | Adres LAN | Rola |
|---|---|---|
| `homelab` | `192.168.100.22` | storage, usługi domowe, DNS, monitoring i backup |
| `ai-node` | `192.168.100.29` | lokalne modele AI, embeddingi, Qdrant i RAG |

## Aktualny stan

### HomeLab

- Ubuntu Server 24.04 LTS,
- Docker i Docker Compose,
- ZFS Mirror `tank` na 2 × WD Red Plus 6 TB,
- Nextcloud,
- Immich,
- Collabora,
- OpenProject,
- Stirling PDF,
- Pi-hole + Unbound,
- Nginx Proxy Manager,
- Beszel,
- Uptime Kuma,
- Portainer,
- Tailscale,
- snapshoty ZFS przez Sanoid,
- monitoring SMART,
- Time Machine i backup Fedora.

### AI-node

- Ubuntu Server 24.04 LTS,
- Ollama z akceleracją Vulkan na Radeon 780M,
- Open WebUI,
- Qdrant,
- model generatywny Gemma 4,
- embeddingi BGE-M3,
- projekt lokalnego RAG w `/srv/rag`,
- Docling i RapidOCR.

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

- [Nextcloud](runbooks/nextcloud.md)
- [Konfiguracja storage](runbooks/storage-setup.md)
- [Unbound](runbooks/unbound.md)

### Zarządzanie rozwojem

- [Roadmap](ROADMAP.md)
- [Historia zmian](CHANGELOG.md)

## Zasady dokumentacji

Każda trwała zmiana infrastruktury:

1. jest projektowana,
2. jest wdrażana,
3. jest opisywana w dokumentacji,
4. kończy się commitem Git.

Dane szybkozmienne, takie jak liczba kontenerów, wersje obrazów i zajętość storage, należy potwierdzać poleceniami diagnostycznymi zamiast utrzymywać jako stałe wartości w dokumentacji.

_Ostatni audyt dokumentacji: 2026-07-21._