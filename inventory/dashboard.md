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

# Usługi

| Usługa | LAN | Tailscale | Domena | Port | Status | Runbook |
|--------|-----|-----------|---------|-----:|--------|----------|
| Homepage | | | | | | |
| Nginx Proxy Manager | | | | | | |
| Pi-hole | | | | 8080 | ✅ | |
| Unbound | localhost | — | — | 5335 | ✅ | ✅ runbooks/unbound.md |
| Nextcloud | http://192.168.100.22:8087| | | | | |
| Paperless | | | | | | |
| OpenProject | | | | | | |
| Stirling PDF | | | | | | |
| Beszel | | | | | | |
| Uptime Kuma | | | | | | |
| WebDAV | | | | | | |

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

Do uzupełnienia.

---

# Uwagi

Ten plik jest głównym panelem administratora HomeLab.

Każda nowa usługa powinna zostać tutaj dopisana.