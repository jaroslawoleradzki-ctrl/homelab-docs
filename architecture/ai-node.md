# AI-node

## Cel

`ai-node` jest wydzielonym hostem do lokalnego uruchamiania modeli AI, embeddingów, wyszukiwania wektorowego i pipeline RAG.

## Sprzęt

| Element | Wartość |
|---|---|
| Model | Minisforum AI X1 |
| CPU | AMD Ryzen 7 255 |
| GPU | Radeon 780M |
| Dysk | Kingston NVMe 1 TB |
| System | Ubuntu Server 24.04 LTS |
| Adres LAN | `192.168.100.29` |

## Sieć

- główny interfejs: `enp1s0`,
- Wi-Fi wyłączone,
- podstawowy dostęp administracyjny: SSH przez LAN lub Tailscale,
- sieć kontenerowa: `ai-backend`,
- Wake-on-LAN skonfigurowany i przetestowany.

## Kontenery

| Usługa | Port | Uwagi |
|---|---:|---|
| Ollama | 11434 | akceleracja Vulkan |
| Open WebUI | 3000 | interfejs użytkownika |
| Qdrant REST | 6333 | związany z localhostem |
| Qdrant gRPC | 6334 | związany z localhostem |

## Modele

- `gemma4:latest` — model generatywny,
- `bge-m3:latest` — embeddingi 1024-wymiarowe.

## Projekt RAG

Projekt znajduje się w `/srv/rag`.

Główne elementy:

- Python virtualenv: `/srv/rag/.venv`,
- Docling,
- RapidOCR,
- czyszczenie tekstu,
- chunking,
- embeddingi przez Ollama,
- Qdrant,
- retrieval.

## Bezpieczeństwo

- Qdrant nie jest publicznie wystawiony,
- usługi AI nie powinny być publikowane bez uwierzytelniania,
- zdalny dostęp administracyjny powinien odbywać się przez Tailscale.
