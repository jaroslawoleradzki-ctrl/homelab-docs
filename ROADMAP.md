# HomeLab Roadmap

## Wizja

Celem środowiska jest niezawodna, prywatna platforma do przechowywania danych, usług domowych, pracy naukowej, lokalnego AI, automatyzacji i backupu.

## Stan obecny

### Hosty i infrastruktura

- ✅ `homelab`: Ubuntu Server 24.04 LTS
- ✅ `ai-node`: Ubuntu Server 26.04 LTS
- ✅ Docker i Docker Compose na obu hostach
- ✅ ZFS mirror `tank` na `homelab`
- ✅ snapshoty Sanoid i monitoring SMART
- ✅ Tailscale
- ✅ Wake-on-LAN na `ai-node`
- ⏳ Wake-on-LAN na `homelab` — test BIOS/UEFI

### Dane i usługi

- ✅ Nextcloud i Collabora
- ✅ Immich
- ✅ OpenProject i Stirling PDF
- ✅ Time Machine i backup Fedora
- ✅ Zotero przez Nextcloud WebDAV
- ✅ mirrory repozytoriów Git w `tank/git`
- ✅ Homepage, Beszel, Uptime Kuma i Portainer
- ✅ Pi-hole, Unbound i Nginx Proxy Manager

### Lokalne AI

- ✅ Ollama z Vulkan
- ✅ Open WebUI
- ✅ Qdrant
- ✅ Gemma 4 i BGE-M3
- ✅ Docling i RapidOCR
- ✅ testowy pipeline RAG: parser → chunking → embedding → Qdrant → retrieval
- ✅ OpenClaw uruchomiony w Dockerze
- ⏳ API dla RAG
- ⏳ utwardzenie konfiguracji OpenClaw

## Najbliższe zadania

1. [ ] przygotować backup konfiguracji i danych `ai-node`,
2. [ ] przygotować runbook disaster recovery dla `homelab`,
3. [ ] przygotować pełny backup off-site,
4. [ ] zweryfikować Wake-on-LAN na `homelab`,
5. [ ] uporządkować domeny, HTTPS i certyfikaty,
6. [ ] wdrożyć politykę aktualizacji kontenerów,
7. [ ] przygotować runbook publikacji usługi przez Nginx Proxy Manager,
8. [ ] przygotować runbook aktualizacji i odtworzenia Immich.

## Średni termin

- [ ] stabilne API lokalnego RAG,
- [ ] integracja RAG z Open WebUI,
- [ ] automatyczny ingestion dokumentów,
- [ ] bezpieczny dostęp do OpenClaw spoza hosta,
- [ ] Prometheus i Grafana,
- [ ] Navidrome,
- [ ] publiczny dostęp do Immich,
- [ ] ocena NetBird self-hosted,
- [ ] wydzielona sieć IoT.

## Długi termin

- [ ] agentowe automatyzacje AI,
- [ ] wspólna pamięć modeli i agentów,
- [ ] integracja z Joplin lub innym repozytorium wiedzy,
- [ ] drugi serwer backupowy poza lokalizacją,
- [ ] segmentacja VLAN,
- [ ] dedykowany firewall/router.

## Zakończone kamienie milowe — 2026-07

- uruchomiono HomeLab i ZFS mirror,
- wdrożono snapshoty, SMART, Time Machine i backup Fedora,
- uruchomiono Nextcloud, Zotero WebDAV i Immich,
- uruchomiono AI-node,
- wdrożono Ollama, Open WebUI i Qdrant,
- uruchomiono testowy pipeline lokalnego RAG,
- uruchomiono OpenClaw,
- wykonano pełny audyt dokumentacji i utworzono podstawowe runbooki.