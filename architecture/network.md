# Architektura sieci

## Topologia

```text
Internet
   │
Router ISP 192.168.100.1
   │
LAN 192.168.100.0/24
   ├── homelab  192.168.100.22
   ├── ai-node  192.168.100.29
   └── urządzenia użytkowników i IoT
```

## Hosty

| Host | Adres LAN | Interfejs | Rola |
|---|---|---|---|
| `homelab` | `192.168.100.22` | Ethernet | usługi, storage, DNS i backup |
| `ai-node` | `192.168.100.29` | `enp1s0` | lokalne AI i RAG |

Na `ai-node` Wi-Fi jest wyłączone. Podstawowym połączeniem jest Ethernet.

## DNS

```text
Urządzenie
   │
   ▼
Pi-hole na homelab:53
   │
   ▼
Unbound na homelab:5335
   │
   ▼
Root DNS
```

Pi-hole filtruje zapytania DNS, a Unbound pełni funkcję lokalnego resolvera rekursywnego.

## Reverse proxy

Nginx Proxy Manager działa na `homelab` i obsługuje:

- porty 80 i 443,
- certyfikaty TLS,
- lokalne i publiczne nazwy usług,
- publikację wybranych aplikacji.

Panel administracyjny działa na porcie 81.

## Dostęp zdalny

Tailscale jest aktywny i stanowi podstawowy mechanizm zdalnego dostępu administracyjnego.

Publiczne wystawianie usług przez domenę `oleradzki.pl` jest w trakcie przygotowania.

## Docker

### HomeLab

Usługi działają w sieciach tworzonych przez poszczególne stosy Docker Compose.

### AI-node

Ollama, Open WebUI i pozostałe komponenty AI komunikują się przez sieć Docker `ai-backend`.

## Firewall

Na `homelab` działa UFW z domyślną polityką:

- deny incoming,
- allow outgoing.

Dostęp do portów administracyjnych i usług jest ograniczony do LAN lub Tailscale, o ile dana usługa nie została świadomie opublikowana.

## Wake-on-LAN

- `ai-node`: skonfigurowany w systemie i przetestowany,
- `homelab`: konfiguracja systemowa została sprawdzona, ale działanie po wyłączeniu wymaga dalszej weryfikacji BIOS/UEFI.

## Porty głównych usług

| Host | Usługa | Port |
|---|---|---:|
| homelab | Nginx Proxy Manager | 80, 81, 443 |
| homelab | Pi-hole | 53, 8080 |
| homelab | Unbound | 5335 |
| homelab | Nextcloud | 8087 |
| homelab | Paperless-ngx | 8010 |
| homelab | Stirling PDF | 8020 |
| homelab | Beszel | 8060 |
| homelab | OpenProject | 8090 |
| homelab | Immich | 2283 |
| homelab | Collabora | 9980 |
| homelab | Portainer | 9443 |
| ai-node | Open WebUI | 3000 |
| ai-node | Ollama | 11434 |
| ai-node | Qdrant REST | 6333 |
| ai-node | Qdrant gRPC | 6334 |

Qdrant jest obecnie związany z localhostem i nie jest przeznaczony do bezpośredniej publikacji w LAN.
