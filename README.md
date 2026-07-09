# HomeLab

Repozytorium zawiera dokumentację oraz konfigurację mojego HomeLaba.

## Cel

HomeLab jest centralną platformą IT wykorzystywaną do:

- prywatnej chmury plików,
- zarządzania dokumentami,
- przechowywania zdjęć,
- środowiska AI,
- automatyzacji,
- monitoringu,
- backupów,
- usług sieciowych.

## Aktualny stan

Platforma działa na Ubuntu Server 24.04 LTS i wykorzystuje:

- ZFS Mirror jako główną przestrzeń danych,
- Nextcloud jako prywatną chmurę,
- Immich do zarządzania zdjęciami,
- Paperless-ngx do dokumentów,
- Homepage jako dashboard usług,
- Pi-hole + Unbound jako lokalny DNS,
- Beszel i Uptime Kuma do monitoringu,
- OpenProject do zarządzania projektami,
- Stirling PDF do pracy z dokumentami,
- automatyczne snapshoty ZFS (Sanoid),
- monitoring SMART dysków,
- backupy Time Machine dla komputerów macOS.

## Dokumentacja

### Architektura

- overview.md
- storage.md
- network.md
- backup.md

### Inwentaryzacja

- dashboard.md
- services.md
- technical-debt.md

### Runbooki

- nextcloud.md
- storage-setup.md
- unbound.md

### Plan rozwoju

- ROADMAP.md

### Historia zmian

- CHANGELOG.md

## Zasady

Każda trwała zmiana infrastruktury:

1. jest projektowana,
2. jest wdrażana,
3. jest opisywana w dokumentacji,
4. kończy się commitem Git.