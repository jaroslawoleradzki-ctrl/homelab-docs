# Architektura HomeLab

## Ogólny model

Środowisko składa się z dwóch głównych hostów:

```text
                    Użytkownicy
                         │
                 LAN / Tailscale / Internet
                         │
                         ▼
                Router 192.168.100.1
                         │
             ┌───────────┴───────────┐
             │                       │
             ▼                       ▼
 homelab 192.168.100.22     ai-node 192.168.100.29
 storage i usługi domowe    lokalne AI, RAG i agenty
             │                       │
             ▼                       ▼
       ZFS Mirror tank         Ollama / Open WebUI
       Docker Compose          Qdrant / RAG / OpenClaw
```

## Host `homelab`

### Rola

- prywatna chmura,
- dokumenty i zdjęcia,
- DNS i reverse proxy,
- monitoring,
- storage,
- backup,
- mirrory repozytoriów Git.

### Platforma

- HP EliteDesk 800 G3 SFF,
- Intel Core i5-6500,
- Samsung 970 EVO Plus 500 GB,
- 2 × WD Red Plus 6 TB,
- Ubuntu Server 24.04 LTS,
- Docker Compose,
- ZFS Mirror `tank`.

### Najważniejsze usługi

- Nginx Proxy Manager,
- Homepage,
- Nextcloud,
- Collabora,
- Immich,
- OpenProject,
- Stirling PDF,
- Pi-hole,
- Unbound,
- Beszel,
- Uptime Kuma,
- Portainer.

## Host `ai-node`

### Rola

- lokalne modele językowe,
- embeddingi,
- wyszukiwanie wektorowe,
- przetwarzanie dokumentów,
- pipeline RAG,
- środowisko agentowe OpenClaw.

### Platforma

- Minisforum AI X1,
- AMD Ryzen 7 255,
- Radeon 780M,
- Kingston NVMe 1 TB,
- Ubuntu Server 26.04 LTS,
- Docker Compose.

### Najważniejsze usługi

- Ollama,
- Open WebUI,
- Qdrant,
- projekt RAG w `/srv/rag`,
- OpenClaw w `/srv/compose/openclaw`.

## Storage

Dane użytkowników są przechowywane w puli ZFS `tank` na hoście `homelab`.

Najważniejsze datasety:

- `tank/cloud`,
- `tank/photos`,
- `tank/media`,
- `tank/git`,
- `tank/backups`,
- `tank/apps`.

Snapshoty są wykonywane automatycznie przez Sanoid. AI-node korzysta z lokalnego NVMe; strategia jego pełnego backupu pozostaje zadaniem otwartym.

## Dostęp

- LAN: `192.168.100.0/24`,
- zdalnie: Tailscale,
- publikacja usług: Nginx Proxy Manager na `homelab`,
- Qdrant pozostaje usługą lokalną,
- dostęp z Internetu jest ograniczany do świadomie wystawionych usług.