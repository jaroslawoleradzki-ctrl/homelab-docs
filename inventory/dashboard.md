# HomeLab Dashboard

> Centralny punkt monitorowania stanu HomeLab.

---

# Serwer

| Parametr | Wartość |
|----------|----------|
| Hostname | homelab |
| LAN | 192.168.100.22 |
| Tailscale | *(do uzupełnienia)* |
| System | Ubuntu Server 24.04 LTS |
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
| Snapshoty ZFS (Sanoid) | ✅ |
| SMART Monitoring | ✅ |
| Time Machine | ✅ |
| Fedora Backup (SMB) | ✅ |

---

# Pojemność Storage

| Dataset | Przeznaczenie | Status |
|---------|---------------|:------:|
| tank/cloud | Nextcloud, dane użytkowników, OneDrive, Zotero | ✅ |
| tank/photos | Biblioteka zdjęć / Immich | ✅ |
| tank/media | Multimedia i pliki współdzielone | ✅ |
| tank/backups | Kopie zapasowe | ✅ |
| tank/backups/timemachine-macbookair-m4 | Time Machine MacBook Air M4 | ✅ |
| tank/backups/timemachine-macbookair2017 | Time Machine MacBook Air 2017 | ✅ |
| tank/backups/fedora44 | Backup Fedora 44 | ✅ |
| tank/git | Repozytoria Git | ✅ |
| tank/apps | Dane trwałe aplikacji | ✅ |

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
| Portainer | https://192.168.100.22:9443 | ⏳ | ⏳ | 9443 | ✅ | ⏳ |
| Collabora | http://192.168.100.22:9980 | ⏳ | ⏳ | 9980 | ✅ | ⏳ |
| Time Machine M4 | smb://homelab/TimeMachine-MacBookAir-M4 | LAN | — | 445 | ✅ | ⏳ |
| Time Machine 2017 | smb://homelab/TimeMachine-MacBookAir-2017 | LAN | — | 445 | ✅ | ⏳ |
| Fedora Backup | smb://homelab/FedoraBackup | LAN | — | 445 | ✅ | ⏳ |
| SFTP (OpenSSH) | ssh://homelab | Tailscale | — | 22 | ✅ | ⏳ |
| Git | ⏳ | ⏳ | ⏳ | ⏳ | ⏳ | ⏳ |

---

# Infrastruktura

| Element | Status | Runbook |
|---------|:------:|:--------:|
| Storage (ZFS) | ✅ | ✅ |
| Docker | ✅ | ⏳ |
| Backup | ✅ | ⏳ |
| Monitoring | ✅ | ⏳ |
| Security | ⏳ | ⏳ |
| Samba | ✅ | ⏳ |
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
| Backup Foundation | ✅ |
| ZFS Snapshots | ✅ |
| SMART Monitoring | ✅ |
| Samba | ✅ |
| Time Machine | ✅ |
| Fedora Backup | ✅ |
| Git Server | ⏳ |
| Immich Migration | ⏳ |
| Paperless Migration | ⏳ |
| Migracja danych aplikacji na ZFS | ⏳ |
| OneDrive → Nextcloud | ✅ |
| Zotero → Nextcloud WebDAV | ✅ |

---

# Ostatnie zmiany

## 2026-07

- wdrożono ZFS Mirror,
- skonfigurowano automatyczne snapshoty Sanoid,
- skonfigurowano monitoring SMART,
- uruchomiono Time Machine dla dwóch komputerów macOS,
- dodano udział SMB dla Fedora 44,
- przeniesiono Zotero WebDAV do Nextcloud,
- zakończono migrację OneDrive do Nextcloud,
- naprawiono problem Unicode/NFC w nazwach plików Nextcloud.

---

# Uwagi

Dashboard pokazuje wyłącznie bieżący stan infrastruktury.

Szczegóły architektury znajdują się w `architecture/`, a procedury administracyjne w `runbooks/`.

---

**Ostatnia aktualizacja:** 2026-07-09  
**Wersja infrastruktury:** 1.0