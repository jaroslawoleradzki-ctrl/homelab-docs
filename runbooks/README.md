# Runbooki HomeLab

Runbook opisuje bezpieczną, powtarzalną procedurę administracyjną. Przed wykonaniem poleceń należy sprawdzić host, katalog roboczy i zakres wpływu zmiany.

## Dostępne procedury

- [Kontrola stanu środowiska](health-check.md)
- [Aktualizacja stosu Docker Compose](docker-compose-update.md)
- [Mirrory repozytoriów Git](git-mirrors.md)
- [Wake-on-LAN](wake-on-lan.md)
- [Stos AI na ai-node](ai-stack.md)
- [Nextcloud](nextcloud.md)
- [Konfiguracja storage](storage-setup.md)
- [Unbound](unbound.md)

## Runbooki do przygotowania

1. odtworzenie HomeLab po awarii systemowego NVMe,
2. backup i odtworzenie AI-node,
3. wymiana uszkodzonego dysku w ZFS mirror,
4. publikacja usługi przez Nginx Proxy Manager,
5. aktualizacja Immich z backupem bazy,
6. odtworzenie Nextcloud z bazy i danych,
7. konfiguracja nowej usługi w Homepage,
8. procedura pełnego backupu off-site.

## Zasada wykonania

Po każdej trwałej zmianie:

1. sprawdź stan usługi,
2. zapisz wynik diagnostyki,
3. zaktualizuj dokumentację,
4. wykonaj commit,
5. wypchnij zmiany do GitHub i zsynchronizuj mirror na HomeLab.