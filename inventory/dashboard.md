# HomeLab Dashboard

> Centralny punkt dostępu do wszystkich usług HomeLab.

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

| Dataset | Przeznaczenie | Status |
|----------|---------------|:------:|
| tank/nextcloud-data | Nextcloud, PARA, Zotero WebDAV | ⏳ |
| tank/immich-library | Zdjęcia i filmy | ⏳ |
| tank/shared-media | ISO, multimedia, pliki współdzielone | ⏳ |
| tank/backups | Kopie zapasowe | ⏳ |
| tank/git | Repozytoria Git | ⏳ |

---

# Usługi

| Usługa | LAN | Tailscale | Domena | Port | Status | Runbook |
|--------|-----|-----------|---------|-----:|:------:|---------|
| Homepage | | | | | ⏳ | |
| Nginx Proxy Manager | | | | | ⏳ | |
| Pi-hole | http://192.168.100.22:8080 | | | 8080 | ✅ | |
| Unbound | localhost | — | — | 5335 | ✅ | ✅ runbooks/unbound.md |
| Nextcloud | http://192.168.100.22:8087 | ⏳ | ⏳ | 8087 | ✅ | ⏳ |
| Immich | | ⏳ | ⏳ | | ⏳ | |
| Paperless-ngx | | ⏳ | ⏳ | | ⏳ | |
| Stirling PDF | | | | | ⏳ | |
| OpenProject | | | | | ⏳ | |
| Beszel | | | | | ⏳ | |
| Uptime Kuma | | | | | ⏳ | |
| Homepage Dashboard | | | | | ⏳ | |
| SMB | smb://homelab/shared-media | LAN | — | 445 | ⏳ | |
| SFTP | ssh://homelab | Tailscale | — | 22 | ⏳ | |
| Git (repozytoria) | | | | | ⏳ | |

---

# DNS

Pi-hole

↓

Unbound

↓

Root DNS

---

# Reverse Proxy

Nginx Proxy Manager

---

# Monitoring

- Beszel
- Uptime Kuma

---

# Backup

| Element | Metoda | Status |
|---------|---------|:------:|
| SSD System | ⏳ | ⏳ |
| ZFS Snapshots | ⏳ | ⏳ |
| Nextcloud | ⏳ | ⏳ |
| Docker Volumes | ⏳ | ⏳ |
| Databases | ⏳ | ⏳ |

---

# Uwagi

Ten plik jest głównym panelem administratora HomeLab.

Każda nowa usługa powinna zostać tutaj dopisana.