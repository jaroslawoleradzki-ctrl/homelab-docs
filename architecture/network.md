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
| `ai-node` | `192.168.100.29` | `enp1s0` | lokalne AI, RAG i OpenClaw |

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

Nginx Proxy Manager działa na `homelab` i obsługuje porty 80 i 443, certyfikaty TLS oraz publikację wybranych aplikacji. Panel administracyjny działa na porcie 81.

## Dostęp zdalny

Tailscale jest podstawowym mechanizmem zdalnego dostępu administracyjnego. Publiczne wystawianie usług powinno być realizowane wyłącznie świadomie przez Nginx Proxy Manager.

## Docker

### HomeLab

Usługi działają w sieciach tworzonych przez poszczególne stosy Docker Compose.

### AI-node

Ollama, Open WebUI i Qdrant komunikują się przez sieć Docker `ai-backend`. OpenClaw działa w osobnym stosie w `/srv/compose/openclaw`.

## Firewall

Na `homelab` działa UFW z domyślną polityką `deny incoming` i `allow outgoing`. Dostęp do portów administracyjnych powinien być ograniczony do LAN lub Tailscale.

## Wake-on-LAN

- `ai-node`: skonfigurowany i przetestowany,
- `homelab`: konfiguracja systemowa sprawdzona, działanie po wyłączeniu nadal wymaga potwierdzenia ustawień BIOS/UEFI.

## Porty głównych usług

| Host | Usługa | Port |
|---|---|---:|
| homelab | Nginx Proxy Manager | 80, 81, 443 |
| homelab | Pi-hole | 53, 8080 |
| homelab | Unbound | 5335 |
| homelab | Nextcloud | 8087 |
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
| ai-node | OpenClaw Gateway | 18789-18790 |

Qdrant jest związany z localhostem i nie jest przeznaczony do bezpośredniej publikacji w LAN.