# Storage Setup

## Cel

Dokument opisuje konfigurację warstwy Storage wykorzystywanej przez HomeLab.

Obejmuje:

- konfigurację ZFS,
- strukturę datasetów,
- snapshoty,
- monitoring SMART,
- udziały SMB dla backupów.

---

# Sprzęt

## Dysk systemowy

- Samsung 970 EVO Plus 500 GB (NVMe)

## Dane

- WD Red Plus 6 TB
- WD Red Plus 6 TB

Konfiguracja:

```
ZFS Mirror
```

---

# Struktura ZFS

Pool:

```
tank
```

Datasety:

```
tank
├── apps
├── cloud
├── media
├── photos
├── git
└── backups
    ├── timemachine-macbookair-m4
    ├── timemachine-macbookair2017
    └── fedora44
```

---

# Właściwości ZFS

- Compression: lz4
- atime: off

Snapshoty:

- realizowane przez Sanoid
- uruchamiane przez systemd timer

---

# Snapshoty

## Dane użytkowników

- 24 godzinne
- 30 dzienne
- 8 tygodniowych
- 12 miesięcznych

## Time Machine

- 14 dziennych
- 8 tygodniowych
- 12 miesięcznych

---

# Monitoring

## SMART

Realizowany przez:

```
smartd
```

Automatyczne testy:

- Short — każda niedziela 03:00
- Long — każdy poniedziałek 03:00

---

## ZFS

Regularnie wykonywać:

```bash
sudo zpool status
```

```bash
sudo zpool scrub tank
```

```bash
zfs list
```

```bash
zfs list -t snapshot
```

---

# Backup

## Time Machine

- MacBook Air M4
- MacBook Air 2017

## SMB

```
FedoraBackup
```

---

# Weryfikacja

Sprawdzenie puli:

```bash
zpool status
```

Sprawdzenie datasetów:

```bash
zfs list
```

Sprawdzenie snapshotów:

```bash
zfs list -t snapshot
```

Sprawdzenie harmonogramu SMART:

```bash
sudo smartd -q showtests
```

---

# Historia

## 2026-07

- wdrożono ZFS Mirror,
- wdrożono Sanoid,
- wdrożono SMART,
- uruchomiono Time Machine,
- dodano udział Fedora Backup.