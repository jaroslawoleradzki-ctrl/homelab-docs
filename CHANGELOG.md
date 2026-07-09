# Changelog

## [1.0.0] - 2026-07-09

### Added

- wdrożono pulę ZFS Mirror (`tank`),
- skonfigurowano automatyczne snapshoty ZFS (Sanoid),
- wdrożono monitoring SMART dla wszystkich dysków,
- dodano udział SMB dla Fedora 44,
- skonfigurowano Time Machine dla dwóch komputerów macOS.

### Changed

- migracja danych OneDrive do Nextcloud,
- migracja Zotero z dedykowanego kontenera WebDAV do WebDAV Nextcloud,
- uproszczono architekturę Storage,
- zaktualizowano dokumentację HomeLab.

### Fixed

- naprawiono problem z nazwami plików Unicode (NFC/NFD),
- ustabilizowano usługę Unbound,
- poprawiono konfigurację Time Machine.

---

## 2026-07-01

### Fixed

- przywrócono działanie Nextcloud,
- usunięto błędne wpisy Custom Locations w Nginx Proxy Manager,
- rozwiązano problem HTTP 502 Bad Gateway.