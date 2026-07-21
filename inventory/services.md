# Inwentaryzacja usług

Dokument opisuje usługi działające na hostach `homelab` i `ai-node`.

Nie należy utrzymywać tutaj ręcznie sumarycznej liczby kontenerów, ponieważ zmienia się ona wraz z aktualizacjami i kontenerami pomocniczymi.

## HomeLab

| Usługa | Kontener lub stos | Port | Dane | Status |
|---|---|---:|---|---|
| Homepage | `homepage` | 3000 | SSD | ✅ |
| Nginx Proxy Manager | `nginx-proxy-manager` | 80, 81, 443 | SSD | ✅ |
| Nextcloud | `nextcloud-app-1` | 8087 | `tank/cloud` | ✅ |
| MariaDB Nextcloud | `nextcloud-db-1` | 3306 | SSD | ✅ |
| Collabora | `collabora` | 9980 | SSD | ✅ |
| Immich Server | `immich_server` | 2283 | `tank/photos` | ✅ |
| Immich Machine Learning | `immich_machine_learning` | — | `tank/apps/immich/model-cache` | ✅ |
| Immich PostgreSQL | `immich_postgres` | 5432 | `tank/apps/immich/postgres` | ✅ |
| OpenProject | `openproject` | 8090 | SSD | ✅ |
| Stirling PDF | `stirling-pdf` | 8020 | SSD | ✅ |
| Pi-hole | `pihole` | 53, 8080 | SSD | ✅ |
| Unbound | `unbound` | 5335 | SSD | ✅ |
| Beszel | `beszel` | 8060 | SSD | ✅ |
| Beszel Agent | `beszel-agent` | — | SSD | ✅ |
| Uptime Kuma | `uptime-kuma` | 3001 | SSD | ✅ |
| Portainer | `portainer` | 9443 | SSD | ✅ |

## AI-node

| Usługa | Kontener lub stos | Port | Dane | Status |
|---|---|---:|---|---|
| Ollama | `ollama` | 11434 | NVMe | ✅ |
| Open WebUI | `open-webui` | 3000 | NVMe | ✅ |
| Qdrant | `qdrant` | 6333, 6334 | NVMe | ✅ |

## Storage

### ZFS na `homelab`

- `tank/cloud`,
- `tank/photos`,
- `tank/media`,
- `tank/git`,
- `tank/backups`,
- `tank/apps`.

### NVMe na `ai-node`

- system operacyjny,
- Docker,
- modele Ollama,
- Qdrant,
- projekt `/srv/rag`.

## Backup i ochrona danych

- snapshoty ZFS: Sanoid,
- monitoring dysków: smartd,
- Time Machine,
- backup Fedora,
- backup bazy Immich,
- mirrory repozytoriów Git w `tank/git`.

Pełny backup off-site pozostaje zadaniem otwartym.