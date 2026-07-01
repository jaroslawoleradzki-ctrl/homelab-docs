# Architektura HomeLab

## Ogólny model

HomeLab działa jako serwer usług lokalnych oparty o Ubuntu Server i Docker.

```text
LAN / Internet
      |
      v
Router
      |
      v
HomeLab: 192.168.100.22
      |
      v
Docker
Warstwa usług
Docker
├── Nginx Proxy Manager
├── Homepage
├── Nextcloud
├── Paperless-ngx
├── OpenProject
├── Stirling PDF
├── OpenRefine
├── Pi-hole
├── Unbound
├── Beszel
├── Uptime Kuma
└── WebDAV
Reverse proxy

Do obsługi reverse proxy wykorzystywany jest Nginx Proxy Manager.

Do uzupełnienia:

* domeny,
* subdomeny,
* certyfikaty SSL,
* usługi wystawione poza LAN,
* usługi dostępne tylko lokalnie.

# Inwentaryzacja usług

| Usługa | Status | Przeznaczenie |
|--------|--------|---------------|
| Nextcloud | działa | prywatna chmura |
| MariaDB | działa | baza danych Nextcloud |
| Paperless-ngx | działa | zarządzanie dokumentami |
| PostgreSQL | działa | baza danych Paperless |
| Redis | działa | cache Paperless |
| Pi-hole | działa | filtrowanie DNS |
| Unbound | problem | lokalny resolver DNS |
| Nginx Proxy Manager | działa | reverse proxy |
| Homepage | działa | dashboard usług |
| Beszel | działa | monitoring serwera |
| Beszel Agent | działa | agent monitorujący |
| Uptime Kuma | działa | monitoring dostępności |
| OpenProject | działa | zarządzanie projektami |
| Stirling PDF | działa | operacje na PDF |
| OpenRefine | działa | czyszczenie i analiza danych |
| WebDAV | działa | synchronizacja Zotero |
