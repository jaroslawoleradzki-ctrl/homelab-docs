# Changelog

## [1.3.0] - 2026-07-21

### Added

- dodano indeks runbooków,
- dodano runbook kontroli stanu obu hostów,
- dodano runbook aktualizacji stosów Docker Compose,
- dodano runbook mirrorów repozytoriów Git,
- dodano runbook Wake-on-LAN,
- dodano runbook stosu AI, RAG i OpenClaw.

### Changed

- wykonano pełny audyt dokumentacji środowiska dwuwęzłowego,
- poprawiono system `ai-node` na Ubuntu Server 26.04 LTS,
- uwzględniono `ai-node` w README, architekturze, inwentaryzacji i dashboardzie,
- dodano OpenClaw do architektury i inwentaryzacji usług,
- przebudowano dashboard stanu infrastruktury,
- zaktualizowano roadmapę i priorytety backupu, disaster recovery oraz bezpieczeństwa OpenClaw,
- ujednolicono zasadę weryfikowania danych szybkozmiennych poleceniami diagnostycznymi.

### Fixed

- usunięto pozostałe odwołania do Paperless-ngx z dashboardu,
- usunięto nieaktualne informacje o jednohostowej architekturze,
- poprawiono nieaktualne wpisy dotyczące systemu i roli `ai-node`.

## [1.2.1] - 2026-07-21

### Removed

- usunięto Paperless-ngx z hosta `homelab`,
- usunięto kontenery webserver, PostgreSQL i Redis należące do stosu Paperless-ngx,
- usunięto Paperless-ngx z inwentaryzacji usług, opisu architektury i roadmapy.

## [1.2.0] - 2026-07-19

### Added

- dodano osobny host `ai-node` (`192.168.100.29`),
- wdrożono Ollama z akceleracją Vulkan,
- wdrożono Open WebUI,
- wdrożono Qdrant,
- dodano modele Gemma 4 i BGE-M3,
- uruchomiono projekt lokalnego RAG w `/srv/rag`,
- dodano parser Docling, OCR RapidOCR, chunking, embeddingi i retrieval,
- dodano dokumentację hostów, AI-node i lokalnego RAG.

### Changed

- zaktualizowano architekturę z jednego serwera do środowiska dwuwęzłowego,
- przeniesiono Ollama, Open WebUI i RAG z planów do stanu wdrożonego,
- zaktualizowano topologię sieci,
- usunięto statyczne liczby kontenerów i stosów,
- uporządkowano odnośniki w README.

## [1.1.0] - 2026-07-14

### Added

- utworzono datasety ZFS dla Immich,
- zapisano backup bazy Immich przed aktualizacją.

### Changed

- zaktualizowano Immich do wersji 3.0.2,
- rozpoczęto migrację danych użytkowników do docelowych datasetów ZFS.

## [1.0.0] - 2026-07-09

### Added

- wdrożono pulę ZFS Mirror (`tank`),
- skonfigurowano automatyczne snapshoty ZFS przez Sanoid,
- wdrożono monitoring SMART,
- dodano udział SMB dla Fedora,
- skonfigurowano Time Machine.

### Changed

- zmigrowano dane OneDrive do Nextcloud,
- zmigrowano Zotero do WebDAV Nextcloud,
- uproszczono architekturę storage.

### Fixed

- naprawiono problem z nazwami plików Unicode,
- ustabilizowano usługę Unbound,
- poprawiono konfigurację Time Machine.

## 2026-07-01

### Fixed

- przywrócono działanie Nextcloud,
- usunięto błędne wpisy Custom Locations w Nginx Proxy Manager,
- rozwiązano problem HTTP 502 Bad Gateway.