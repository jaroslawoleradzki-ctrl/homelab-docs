# Technical Debt

Dokument zawiera listę świadomie odłożonych zadań technicznych oraz decyzji architektonicznych wymagających realizacji w przyszłości.

---

# Wysoki priorytet

## Bezpieczeństwo

- Wdrożyć HTTPS dla wszystkich usług publikowanych przez Nginx Proxy Manager.
- Skonfigurować domenę `oleradzki.pl`.
- Opracować i wdrożyć politykę kopii zapasowych konfiguracji usług.

## Backup

- Przygotować procedurę Disaster Recovery.
- Zweryfikować możliwość odtworzenia HomeLaba wyłącznie z backupów.

---

# Średni priorytet

## Storage

- Zakończyć migrację danych Immich do `tank/photos`.
- Zakończyć migrację danych Paperless na ZFS.
- Określić docelową lokalizację trwałych danych wszystkich usług.

## Dokumentacja

- Przygotować `network.md`.
- Przygotować `backup.md`.
- Przygotować `security.md`.
- Uzupełnić runbooki wszystkich usług.

## Docker

- Udokumentować sieci Docker.
- Udokumentować wolumeny Docker.
- Przygotować politykę aktualizacji kontenerów.

---

# Niski priorytet

## AI

- Wdrożyć Ollama.
- Wdrożyć Open WebUI.
- Wdrożyć AnythingLLM.
- Zaprojektować lokalne środowisko RAG.

## Multimedia

- Uruchomić Navidrome.
- Zintegrować bibliotekę muzyki z HomeLab.

## Development

- Wdrożyć Forgejo lub Gitea.
- Przygotować standard dodawania nowych usług.

## Monitoring

- Rozbudować monitoring o Grafanę i Prometheusa.

---

# Zrealizowane

## Storage

- ✅ Migracja danych Nextcloud na ZFS.
- ✅ Snapshoty ZFS (Sanoid).
- ✅ Monitoring SMART.
- ✅ Time Machine dla dwóch komputerów macOS.
- ✅ Backup SMB dla Fedora 44.

## Nextcloud

- ✅ Migracja Zotero WebDAV do Nextcloud.
- ✅ Migracja OneDrive do Nextcloud.
- ✅ Naprawa problemu z nazwami plików Unicode (NFC/NFD).

## Infrastruktura

- ✅ Stabilizacja Unbound.
- ✅ Wdrożenie ZFS Mirror.
- ✅ Dokumentacja architektury Storage.