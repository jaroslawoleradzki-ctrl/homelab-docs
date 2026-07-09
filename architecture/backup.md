# Backup Architecture

## Cel

Dokument opisuje strategię ochrony danych stosowaną w HomeLab.

Backup opiera się na kilku niezależnych warstwach zabezpieczeń, dzięki czemu awaria pojedynczego elementu nie powoduje utraty danych.

---

# Warstwy ochrony

HomeLab wykorzystuje następujące mechanizmy:

1. ZFS Mirror
2. Snapshoty ZFS
3. Backup Time Machine
4. Backup SMB
5. Monitoring SMART
6. Git (dla dokumentacji i konfiguracji)

---

# Warstwa 1 — ZFS Mirror

Dane użytkowników przechowywane są na dwóch dyskach WD Red Plus 6 TB pracujących w konfiguracji:

```
ZFS Mirror
```

Zapewnia to odporność na awarię jednego dysku.

Mirror nie jest backupem.

---

# Warstwa 2 — Snapshoty ZFS

Snapshoty wykonywane są automatycznie przez Sanoid uruchamiany z wykorzystaniem `systemd timer`.

## Dane użytkowników

- 24 snapshoty godzinowe,
- 30 dziennych,
- 8 tygodniowych,
- 12 miesięcznych.

## Time Machine

- 14 dziennych,
- 8 tygodniowych,
- 12 miesięcznych.

Snapshoty umożliwiają szybkie odtworzenie przypadkowo usuniętych lub zmodyfikowanych plików.

---

# Warstwa 3 — Time Machine

HomeLab udostępnia dwa zasoby Time Machine:

| Komputer | Dataset |
|-----------|---------|
| MacBook Air M4 | tank/backups/timemachine-macbookair-m4 |
| MacBook Air 2017 | tank/backups/timemachine-macbookair2017 |

Backup wykonywany jest automatycznie przez macOS.

---

# Warstwa 4 — Backup SMB

HomeLab udostępnia udział:

```
FedoraBackup
```

Przeznaczony do wykonywania kopii zapasowych komputera z Fedora 44.

Dataset:

```
tank/backups/fedora44
```

---

# Warstwa 5 — Monitoring SMART

Wszystkie dyski objęte są monitoringiem SMART.

Automatyczne testy:

- Short — każda niedziela o 03:00,
- Long — każdy poniedziałek o 03:00.

Stan dysków można sprawdzić:

```bash
sudo smartctl -H /dev/sda
sudo smartctl -H /dev/sdb
sudo smartctl -H /dev/nvme0
```

Harmonogram testów:

```bash
sudo smartd -q showtests
```

---

# Warstwa 6 — Git

Dokumentacja HomeLab przechowywana jest w repozytorium Git.

Repozytorium zawiera:

- architekturę,
- runbooki,
- roadmapę,
- changelog,
- dokumentację operacyjną.

---

# Zakres ochrony

| Element | Mechanizm |
|----------|-----------|
| Dane użytkowników | ZFS Mirror + Snapshoty |
| Nextcloud | Snapshoty ZFS |
| Dokumentacja | Git |
| Komputery macOS | Time Machine |
| Fedora | Backup SMB |
| Stan dysków | SMART |

---

# Ograniczenia

Obecna architektura nie chroni przed:

- pożarem,
- kradzieżą serwera,
- przepięciem uszkadzającym cały sprzęt,
- katastrofą obejmującą całą lokalizację.

W przyszłości planowany jest backup poza lokalizacją (off-site).

---

# Kierunek rozwoju

Planowane jest:

- backup konfiguracji Docker Compose,
- automatyczny eksport baz danych,
- backup off-site,
- okresowe testy odtwarzania środowiska (Disaster Recovery).

---

# Weryfikacja

Sprawdzenie stanu puli:

```bash
zpool status
```

Sprawdzenie snapshotów:

```bash
zfs list -t snapshot
```

Sprawdzenie harmonogramu SMART:

```bash
sudo smartd -q showtests
```

Sprawdzenie Time Machine:

```bash
tmutil destinationinfo
```

---

# Historia

## 2026-07

- wdrożono ZFS Mirror,
- skonfigurowano automatyczne snapshoty Sanoid,
- uruchomiono Time Machine dla dwóch komputerów macOS,
- dodano udział Fedora Backup,
- wdrożono monitoring SMART.