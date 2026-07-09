# Services Inventory

## Cel

Dokument zawiera pełną inwentaryzację usług uruchomionych w HomeLab.

Aktualizowany jest po każdej trwałej zmianie infrastruktury.

---

# Usługi

| Usługa | Kontener(y) | Port | Dane | Status | Reverse Proxy |
|----------|-------------|------|------|--------|---------------|
| Homepage | homepage | 3000 | SSD | ✅ | Tak |
| Nginx Proxy Manager | nginx-proxy-manager | 80, 81, 443 | SSD | ✅ | — |
| Nextcloud | nextcloud-app-1 | 8087 | ZFS (`tank/cloud`) | ✅ | Tak |
| MariaDB | nextcloud-db-1 | 3306 | SSD | ✅ | Nie |
| Collabora | collabora | 9980 | SSD | ✅ | Tak |
| Immich Server | immich_server | 2283 | ZFS (`tank/photos`) | ✅ | Tak |
| Immich Machine Learning | immich_machine_learning | — | SSD | ✅ | Nie |
| Immich PostgreSQL | immich_postgres | 5432 | SSD | ✅ | Nie |
| Immich Redis | immich_redis | 6379 | SSD | ✅ | Nie |
| Paperless-ngx | paperless-webserver-1 | 8010 | SSD + ZFS | ✅ | Tak |
| PostgreSQL | paperless-db-1 | 5432 | SSD | ✅ | Nie |
| Redis | paperless-broker-1 | 6379 | SSD | ✅ | Nie |
| OpenProject | openproject | 8090 | SSD | ✅ | Tak |
| Stirling PDF | stirling-pdf | 8020 | SSD | ✅ | Tak |
| Pi-hole | pihole | 53, 67, 8080 | SSD | ✅ | Nie |
| Unbound | unbound | 5335 | SSD | ✅ | Nie |
| Beszel | beszel | 8060 | SSD | ✅ | Tak |
| Beszel Agent | beszel-agent | — | SSD | ✅ | Nie |
| Uptime Kuma | uptime-kuma | 3001 | SSD | ✅ | Tak |
| Portainer | portainer | 9443 | SSD | ✅ | Tak |

---

# Storage

## ZFS

- tank/cloud
- tank/photos
- tank/media
- tank/git
- tank/backups

## SSD

- system operacyjny
- Docker
- konfiguracje
- bazy danych
- logi

---

# Backup

## Snapshoty ZFS

Realizowane automatycznie przez Sanoid.

## SMART

Monitorowanie wszystkich dysków realizowane przez smartd.

## Time Machine

- MacBook Air M4
- MacBook Air 2017

## SMB

- Fedora Backup

---

# Statystyki

| Parametr | Wartość |
|-----------|---------|
| System operacyjny | Ubuntu Server 24.04 LTS |
| Docker Compose Stacks | 9 |
| Kontenery | 19 |
| Pool ZFS | tank |
| Dyski danych | 2 × WD Red Plus 6 TB (Mirror) |
| Dysk systemowy | Samsung 970 EVO Plus 500 GB |