# Inwentaryzacja hostów

## Hosty produkcyjne

| Host | Sprzęt | System | Adres LAN | Główna rola |
|---|---|---|---|---|
| `homelab` | HP EliteDesk 800 G3 SFF, i5-6500, NVMe 500 GB, 2 × 6 TB | Ubuntu Server 24.04 LTS | `192.168.100.22` | storage ZFS, usługi domowe, DNS, monitoring i backup |
| `ai-node` | Minisforum AI X1, Ryzen 7 255, Radeon 780M, NVMe 1 TB | Ubuntu Server 26.04 LTS | `192.168.100.29` | lokalne AI, embeddingi, Qdrant, RAG i OpenClaw |

## Zasady

- adresy LAN powinny być rezerwowane w DHCP lub konfigurowane statycznie,
- każdy host powinien mieć udokumentowane: rolę, storage, sieć, backup, monitoring i procedurę odtworzenia,
- zmiany sprzętowe i systemowe należy dopisywać do `CHANGELOG.md`,
- wersję systemu należy potwierdzać poleceniem `hostnamectl` przed aktualizacją dokumentacji.