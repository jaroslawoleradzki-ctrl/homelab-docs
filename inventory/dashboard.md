# Dashboard stanu HomeLab

Dokument jest skróconym widokiem środowiska. Dane szybkozmienne należy potwierdzać poleceniami z [runbooka kontroli stanu](../runbooks/health-check.md).

## Hosty

| Host | LAN | System | Rola | Stan |
|---|---|---|---|:---:|
| `homelab` | `192.168.100.22` | Ubuntu Server 24.04 LTS | ZFS, usługi domowe, DNS, monitoring i backup | ✅ |
| `ai-node` | `192.168.100.29` | Ubuntu Server 26.04 LTS | Ollama, Open WebUI, Qdrant, RAG i OpenClaw | ✅ |

## Storage i ochrona danych

| Element | Lokalizacja | Stan |
|---|---|:---:|
| ZFS mirror `tank` | `homelab`, 2 × WD Red Plus 6 TB | ✅ |
| Snapshoty Sanoid | `homelab` | ✅ |
| Monitoring SMART | `homelab` | ✅ |
| Time Machine | `tank/backups` | ✅ |
| Backup Fedora | `tank/backups/fedora44` | ✅ |
| Mirrory Git | `tank/git` | ✅ |
| Backup off-site | poza lokalizacją | ⏳ |
| Backup AI-node | konfiguracje, modele i dane RAG | ⏳ |

## Główne usługi HomeLab

| Usługa | Adres lub port | Stan | Runbook |
|---|---|:---:|---|
| Homepage | `http://192.168.100.22:3000` | ✅ | — |
| Nginx Proxy Manager | `http://192.168.100.22:81` | ✅ | planowany |
| Pi-hole | `http://192.168.100.22:8080/admin` | ✅ | — |
| Unbound | `5335` | ✅ | [tak](../runbooks/unbound.md) |
| Nextcloud | `https://nextcloud.klucznik.biz` | ✅ | [tak](../runbooks/nextcloud.md) |
| Immich | `http://192.168.100.22:2283` | ✅ | planowany |
| Stirling PDF | `http://192.168.100.22:8020` | ✅ | — |
| OpenProject | `https://projekty.klucznik.biz` | ✅ | — |
| Beszel | `http://192.168.100.22:8060` | ✅ | — |
| Uptime Kuma | `http://192.168.100.22:3001` | ✅ | — |
| Portainer | `https://192.168.100.22:9443` | ✅ | — |
| Collabora | `9980` | ✅ | — |

## Główne usługi AI-node

| Usługa | Port | Stan | Uwagi |
|---|---:|:---:|---|
| Open WebUI | 3000 | ✅ | interfejs użytkownika |
| Ollama | 11434 | ✅ | Vulkan, Radeon 780M |
| Qdrant REST | 6333 | ✅ | związany z localhostem |
| Qdrant gRPC | 6334 | ✅ | związany z localhostem |
| Lokalny RAG | — | rozwój | `/srv/rag` |
| OpenClaw Gateway | 18789–18790 | ✅ | wymaga dalszego utwardzenia |

## Stan kluczowych obszarów

| Obszar | Stan |
|---|:---:|
| Storage ZFS | ✅ |
| DNS Pi-hole + Unbound | ✅ |
| Monitoring | ✅ |
| Dostęp Tailscale | ✅ |
| Wake-on-LAN AI-node | ✅ |
| Wake-on-LAN HomeLab | test BIOS/UEFI |
| Publiczne domeny i TLS | w toku |
| Disaster recovery | do przygotowania |
| Backup off-site | do przygotowania |

## Ostatnia aktualizacja

2026-07-21 — pełny audyt dokumentacji, uwzględnienie AI-node, usunięcie Paperless-ngx i dodanie pierwszego zestawu runbooków.