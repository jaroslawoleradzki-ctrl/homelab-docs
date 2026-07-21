# Dług techniczny

Dokument zawiera świadomie odłożone zadania oraz decyzje wymagające dalszej pracy.

## Wysoki priorytet

### Backup i odtwarzanie

- przygotować pełny backup off-site,
- opracować disaster recovery dla `homelab`,
- przygotować backup konfiguracji Docker Compose,
- przygotować backup i procedurę odtworzenia `ai-node`, w tym Qdrant, RAG i konfigurację OpenClaw,
- wykonać testowe odtworzenie kluczowych usług.

### Bezpieczeństwo

- uporządkować domeny, HTTPS i certyfikaty,
- ograniczyć publiczną ekspozycję usług,
- wyłączyć `allowInsecureAuth` w OpenClaw,
- skonfigurować rate limiting i dozwolone origins OpenClaw,
- zweryfikować zakres narzędzi elevated i dostęp OpenClaw do Docker socket,
- wdrożyć 2FA tam, gdzie jest dostępne.

## Średni priorytet

### Storage

- potwierdzić zakończenie migracji danych Immich do `tank/photos`,
- określić i udokumentować docelową lokalizację danych trwałych wszystkich usług,
- przygotować runbook wymiany dysku w ZFS mirror,
- monitorować pojemność i retencję snapshotów.

### Sieć

- zweryfikować Wake-on-LAN na `homelab` w BIOS/UEFI,
- przygotować politykę publikowania usług przez Nginx Proxy Manager,
- ocenić NetBird self-hosted jako alternatywę dla Tailscale,
- zaprojektować segmentację IoT i przyszłe VLAN-y.

### Docker i operacje

- zinwentaryzować wolumeny i sieci Docker,
- wdrożyć jednolitą politykę aktualizacji kontenerów,
- przygotować runbook aktualizacji Immich z backupem bazy,
- przygotować runbook odtworzenia Nextcloud,
- ustalić standard dodawania nowych usług do Homepage i monitoringu.

### AI-node

- ukończyć stabilne API lokalnego RAG,
- zintegrować RAG z Open WebUI,
- uruchomić automatyczny ingestion dokumentów,
- określić, które procesy AI mają działać stale, a które na żądanie,
- dodać monitoring AI-node do centralnego dashboardu,
- zakończyć utwardzenie OpenClaw.

## Niski priorytet

- uruchomić Navidrome,
- wdrożyć Prometheus i Grafanę,
- rozważyć Forgejo lub Gitea,
- przygotować wspólną pamięć agentów i modeli,
- ocenić integrację z Joplin.

## Zrealizowane

- ✅ ZFS mirror i datasety,
- ✅ Sanoid i monitoring SMART,
- ✅ Time Machine i backup Fedora,
- ✅ migracja Nextcloud na ZFS,
- ✅ Zotero przez Nextcloud WebDAV,
- ✅ Immich,
- ✅ Pi-hole i Unbound,
- ✅ Tailscale,
- ✅ mirrory Git w `tank/git`,
- ✅ `ai-node` z Ollama, Open WebUI i Qdrant,
- ✅ testowy pipeline RAG,
- ✅ OpenClaw uruchomiony w Dockerze,
- ✅ podstawowy zestaw runbooków administracyjnych.