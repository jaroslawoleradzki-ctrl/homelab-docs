# HomeLab Dashboard

> Centralny punkt monitorowania stanu HomeLab.

---

# Serwer

| Parametr | Wartość |
|----------|----------|
| Hostname | homelab |
| LAN | 192.168.100.22 |
| Tailscale | *(do uzupełnienia)* |
| System | Ubuntu 24.04 LTS |
| Docker | ✅ |
| Portainer | ✅ |

---

# Storage

| Element | Status |
|----------|:------:|
| SSD System | ✅ |
| ZFS Mirror | ✅ |
| Datasets | ✅ |
| Nextcloud Storage Migration | ✅ |
| Snapshoty | ⏳ |
| SMART Monitoring | ⏳ |

---

# Pojemność Storage

| Dataset | Przeznaczenie | Status |
|---------|---------------|:------:|
| tank/cloud | Nextcloud, PARA, Zotero WebDAV | ✅ |
| tank/photos | Zdjęcia (Immich) | ⏳ |
| tank/media | Multimedia i pliki współdzielone | ⏳ |
| tank/backups | Kopie zapasowe | ⏳ |
| tank/git | Repozytoria Git | ⏳ |
| tank/apps | Dane trwałe aplikacji | ⏳ |

---

# Usługi

| Usługa | LAN | Tailscale | Domena | Port | Status | Runbook |
|--------|-----|-----------|---------|-----:|:------:|:--------:|
| Homepage | http://192.168.100.22:3000 | ⏳ | ⏳ | 3000 | ✅ | ⏳ |
| Nginx Proxy Manager | http://192.168.100.22:81 | ⏳ | ⏳ | 81 | ✅ | ⏳ |
| Pi-hole | http://192.168.100.22:8080 | — | — | 8080 | ✅ | ⏳ |
| Unbound | localhost | — | — | 5335 | ✅ | ✅ |
| Nextcloud | http://192.168.100.22:8087 | ⏳ | nextcloud.klucznik.biz | 8087 | ✅ | ✅ |
| Immich | http://192.168.100.22:2283 | ⏳ | ⏳ | 2283 | ✅ | ⏳ |
| Paperless-ngx | http://192.168.100.22:8010 | ⏳ | ⏳ | 8010 | ✅ | ⏳ |
| Stirling PDF | http://192.168.100.22:8020 | ⏳ | ⏳ | 8020 | ✅ | ⏳ |
| OpenProject | http://192.168.100.22:8090 | ⏳ | ⏳ | 8090 | ✅ | ⏳ |
| Beszel | http://192.168.100.22:8060 | ⏳ | ⏳ | 8060 | ✅ | ⏳ |
| Uptime Kuma | http://192.168.100.22:3001 | ⏳ | ⏳ | 3001 | ✅ | ⏳ |
| SMB (Samba) | smb://homelab/shared-media | LAN | — | 445 | ⏳ | ⏳ |
| SFTP (OpenSSH) | ssh://homelab | Tailscale | — | 22 | ✅ | ⏳ |
| Git | ⏳ | ⏳ | ⏳ | ⏳ | ⏳ | ⏳ |

---

# Infrastruktura

| Element | Status | Runbook |
|---------|:------:|:--------:|
| Storage (ZFS) | ✅ | ✅ |
| Docker | ✅ | ⏳ |
| Backup | ⏳ | ⏳ |
| Monitoring | ⏳ | ⏳ |
| Security | ⏳ | ⏳ |
| Samba | ⏳ | ⏳ |
| OpenSSH / SFTP | ✅ | ⏳ |

---

# Architektura

| Dokument | Status |
|----------|:------:|
| Storage Architecture | ✅ |
| Network Architecture | ⏳ |
| Security Architecture | ⏳ |
| Backup Strategy | ⏳ |

---

# Roadmap

| Etap | Status |
|------|:------:|
| Storage Foundation | ✅ |
| Nextcloud on ZFS | ✅ |
| Backup Foundation | ⏳ |
| ZFS Snapshots | ⏳ |
| SMART Monitoring | ⏳ |
| Samba | ⏳ |
| Git Server | ⏳ |
| Immich Migration | ⏳ |
| Paperless Migration | ⏳ |
| Pozostałe migracje na ZFS | ⏳ |
| OneDrive → Nextcloud | ⏳ |

---

# Uwagi

Dashboard pokazuje wyłącznie bieżący stan infrastruktury.

Szczegóły architektury znajdują się w `docs/architecture`, a procedury administracyjne w `runbooks/`.