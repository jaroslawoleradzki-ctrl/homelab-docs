# Architektura HomeLab

## Ogólny model

HomeLab działa jako centralny serwer usług domowych oparty o Ubuntu Server, Docker oraz ZFS.

```text
                Użytkownicy
                     │
                     ▼
          LAN / VPN / Internet
                     │
                     ▼
                 Router
                     │
                     ▼
          HomeLab (192.168.100.22)
                     │
 ┌───────────────────┴───────────────────┐
 │                                       │
 ▼                                       ▼
Ubuntu Server 24.04 LTS              ZFS Mirror
                                     (tank)
 │                                       │
 ▼                                       ▼
Docker Engine                     Dane użytkowników
 │
 ▼
Usługi kontenerowe
├── Nginx Proxy Manager
├── Homepage
├── Nextcloud
├── Collabora
├── Immich
├── Paperless-ngx
├── OpenProject
├── Stirling PDF
├── Pi-hole
├── Unbound
├── Beszel
└── Uptime Kuma
```

---

# Warstwy architektury

## System operacyjny

- Ubuntu Server 24.04 LTS

---

## Kontenery

Wszystkie usługi uruchamiane są jako kontenery Docker Compose.

---

## Storage

Dane użytkowników przechowywane są w puli ZFS `tank`.

Najważniejsze datasety:

- cloud
- photos
- media
- git
- backups

Snapshoty realizowane są automatycznie przez Sanoid.

---

## Reverse Proxy

Reverse proxy realizowany jest przez Nginx Proxy Manager.

Odpowiada za:

- HTTPS,
- certyfikaty SSL,
- publikację usług,
- lokalny dostęp do aplikacji.

---

# Inwentaryzacja usług

| Usługa | Status | Przeznaczenie |
|--------|--------|---------------|
| Homepage | ✅ | dashboard usług |
| Nginx Proxy Manager | ✅ | reverse proxy |
| Nextcloud | ✅ | prywatna chmura |
| MariaDB | ✅ | baza danych Nextcloud |
| Collabora | ✅ | edycja dokumentów Office |
| Immich | ✅ | zarządzanie zdjęciami |
| Paperless-ngx | ✅ | zarządzanie dokumentami |
| PostgreSQL | ✅ | baza danych Paperless |
| Redis | ✅ | cache Paperless |
| OpenProject | ✅ | zarządzanie projektami |
| Stirling PDF | ✅ | operacje na PDF |
| Pi-hole | ✅ | filtrowanie DNS |
| Unbound | ✅ | lokalny resolver DNS |
| Beszel | ✅ | monitoring serwera |
| Beszel Agent | ✅ | agent monitorujący |
| Uptime Kuma | ✅ | monitoring usług |

---

# Kierunek rozwoju

Planowany rozwój obejmuje:

- lokalne środowisko AI,
- RAG,
- Ollama,
- Open WebUI,
- AnythingLLM,
- Navidrome,
- dalszą automatyzację HomeLaba.