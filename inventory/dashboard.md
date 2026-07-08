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
| ZFS Mirror | ⏳ |
| Snapshoty | ⏳ |
| SMART Monitoring | ⏳ |

---

# Usługi

| Usługa | LAN | Tailscale | Domena | Port | Status | Runbook |
|--------|-----|-----------|---------|-----:|:------:|---------|
| Homepage | | | | | ⏳ | ⏳ |
| Nginx Proxy Manager | | | | | ⏳ | ⏳ |
| Pi-hole | http://192.168.100.22:8080 | — | — | 8080 | ✅ | ⏳ |
| Unbound | localhost | — | — | 5335 | ✅ | ✅ |
| Nextcloud | http://192.168.100.22:8087 | ⏳ | ⏳ | 8087 | ✅ | ⏳ |
| Immich | | ⏳ | ⏳ | | ⏳ | ⏳ |
| Paperless-ngx | | ⏳ | ⏳ | | ⏳ | ⏳ |
| Stirling PDF | | ⏳ | ⏳ | | ⏳ | ⏳ |
| OpenProject | | ⏳ | ⏳ | | ⏳ | ⏳ |
| Beszel | | ⏳ | ⏳ | | ⏳ | ⏳ |
| Uptime Kuma | | ⏳ | ⏳ | | ⏳ | ⏳ |
| SMB (Samba) | smb://homelab/shared-media | LAN | — | 445 | ⏳ | ⏳ |
| SFTP (OpenSSH) | ssh://homelab | Tailscale | — | 22 | ✅ | ⏳ |
| Git | | | | | ⏳ | ⏳ |

---

# Infrastruktura

| Element | Status | Runbook |
|---------|:------:|---------|
| Storage (ZFS) | ⏳ | ✅ |
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

# Uwagi

Dashboard pokazuje wyłącznie bieżący stan infrastruktury.

Szczegóły architektury znajdują się w katalogu `docs/architecture`, a procedury administracyjne w `runbooks/`.