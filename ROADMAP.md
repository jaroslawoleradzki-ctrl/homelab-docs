# HomeLab Roadmap

## Wizja

Celem HomeLaba jest stworzenie niezawodnej, prywatnej platformy do:

- przechowywania danych,
- automatyzacji,
- lokalnego AI,
- pracy naukowej,
- monitoringu infrastruktury,
- usług domowych,
- backupu lokalnego i off-site.

## Stan obecny

### Infrastruktura

- ✅ Ubuntu Server 24.04 LTS na `homelab`
- ✅ Ubuntu Server 24.04 LTS na `ai-node`
- ✅ Docker i Docker Compose
- ✅ ZFS Mirror
- ✅ snapshoty Sanoid
- ✅ monitoring SMART
- ✅ Tailscale
- ✅ Wake-on-LAN skonfigurowany na `ai-node`

### Storage i dane

- ✅ Nextcloud
- ✅ Time Machine
- ✅ backup Fedora
- ✅ Zotero przez Nextcloud WebDAV
- ✅ Immich
- ✅ repozytoria Git mirrorowane na HomeLab

### Monitoring i sieć

- ✅ Homepage
- ✅ Beszel
- ✅ Uptime Kuma
- ✅ Pi-hole
- ✅ Unbound
- ✅ Nginx Proxy Manager

### Lokalne AI

- ✅ Ollama
- ✅ Open WebUI
- ✅ Qdrant
- ✅ Gemma 4
- ✅ BGE-M3
- ✅ Docling
- ✅ RapidOCR
- ✅ testowy pipeline RAG: parser → chunking → embedding → Qdrant → retrieval

## Najbliższe zadania

- [ ] wystawienie wybranych usług pod domeną `oleradzki.pl`,
- [ ] uporządkowanie HTTPS i certyfikatów,
- [ ] dokumentacja disaster recovery,
- [ ] backup konfiguracji Docker Compose,
- [ ] pełny backup off-site,
- [ ] weryfikacja Wake-on-LAN na `homelab`,
- [ ] dokumentacja dostępu zdalnego i Tailscale,
- [ ] uporządkowanie polityki aktualizacji kontenerów.

## Średni termin

- [ ] Prometheus i Grafana,
- [ ] Navidrome,
- [ ] produkcyjne wdrożenie Immich z dostępem zewnętrznym,
- [ ] stabilny interfejs API dla lokalnego RAG,
- [ ] integracja RAG z Open WebUI,
- [ ] automatyczny ingestion dokumentów,
- [ ] ocena NetBird self-hosted jako alternatywy dla Tailscale,
- [ ] przygotowanie wydzielonej sieci dla IoT.

## Długi termin

- [ ] agentowe automatyzacje AI,
- [ ] wspólna pamięć modeli i agentów,
- [ ] integracja z Joplin lub innym repozytorium wiedzy,
- [ ] drugi serwer backupowy poza lokalizacją,
- [ ] segmentacja VLAN,
- [ ] rozważenie dedykowanego firewalla/routera.

## Zakończone kamienie milowe

### 2026-07

- uruchomienie HomeLaba,
- migracja danych na ZFS,
- wdrożenie Time Machine,
- wdrożenie Sanoid i SMART,
- wdrożenie Nextcloud i Zotero WebDAV,
- uruchomienie Immich,
- uruchomienie AI-node,
- wdrożenie Ollama, Open WebUI i Qdrant,
- uruchomienie testowego pipeline lokalnego RAG.