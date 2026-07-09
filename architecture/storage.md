# Storage Architecture

## Cel

Architektura przechowywania danych definiuje sposób organizacji wszystkich danych w HomeLab.

Jej głównym celem jest zapewnienie:

- bezpieczeństwa danych,
- prostoty zarządzania,
- łatwej rozbudowy,
- niezależności danych od aplikacji,
- możliwości odtworzenia środowiska po awarii.

---

# Architektura

HomeLab wykorzystuje dwie warstwy przechowywania danych.

## Warstwa operacyjna (SSD)

Na dysku NVMe znajdują się:

- Ubuntu Server,
- Docker Engine,
- Docker Compose,
- konfiguracje usług,
- bazy danych kontenerów,
- logi systemowe,
- dane operacyjne aplikacji.

Dysk systemowy nie służy do przechowywania danych użytkowników.

---

## Warstwa danych (ZFS)

Dwa dyski WD Red Plus 6 TB pracują jako **ZFS Mirror**.

Pula danych:

```
tank
```

Całość danych użytkowników przechowywana jest w tej puli.

---

# Struktura puli

```
tank
├── apps
├── cloud
├── git
├── media
├── photos
└── backups
    ├── timemachine-macbookair-m4
    ├── timemachine-macbookair2017
    └── fedora44
```

---

# Datasety

## apps

Dataset przeznaczony na przyszłe aplikacje wymagające własnej przestrzeni danych.

Obecnie pozostaje pusty.

---

## cloud

Centralny magazyn danych użytkowników wykorzystywany przez Nextcloud.

Przechowuje wszystkie pliki użytkowników.

Przykładowa struktura:

```
tank/cloud
└── joleradzki
    └── files
        ├── Documents
        ├── OneDrive
        ├── Photos
        ├── Zotero
        └── ...
```

Folder `Zotero` jest udostępniany przez WebDAV Nextcloud.

Nie jest już wykorzystywany osobny kontener WebDAV.

---

## media

Biblioteka dużych plików.

Przeznaczona na:

- obrazy ISO,
- multimedia,
- archiwa,
- materiały techniczne,
- pliki współdzielone przez SMB.

---

## photos

Dataset przeznaczony dla biblioteki zdjęć.

Docelowo wykorzystywany przez Immich.

Oddzielenie zdjęć od pozostałych danych umożliwia niezależną politykę snapshotów i backupów.

---

## git

Repozytoria Git przechowywane lokalnie.

Przykłady:

- HomeLab
- PhD
- workshop-time-tracking

Docelowo może zostać wykorzystany przez Forgejo lub Gitea.

---

## backups

Dataset przeznaczony wyłącznie na kopie zapasowe.

Zawiera osobne datasety:

- Time Machine — MacBook Air M4,
- Time Machine — MacBook Air 2017,
- udział SMB dla Fedora 44,
- przyszłe backupy usług.

---

# Snapshoty ZFS

Automatyczne snapshoty realizowane są przez **Sanoid**.

### Dane użytkowników

- 24 snapshoty godzinowe,
- 30 dziennych,
- 8 tygodniowych,
- 12 miesięcznych.

### Time Machine

Dla datasetów Time Machine stosowana jest osobna polityka:

- 14 dziennych,
- 8 tygodniowych,
- 12 miesięcznych.

---

# Dostęp do danych

| Dataset | Nextcloud | SMB | WebDAV | Inne |
|----------|-----------|-----|---------|------|
| cloud | ✓ | ✗ | ✓ | |
| media | ✗ | ✓ | ✗ | |
| photos | ✗ | ✗ | ✗ | Immich |
| backups | ✗ | ✓ | ✗ | Time Machine |
| git | ✗ | opcjonalnie | ✗ | |

---

# Zasady projektowe

1. Dane należą do infrastruktury HomeLab, a nie do aplikacji.

2. Kontenery mogą zostać odtworzone bez utraty danych.

3. Dane użytkowników przechowywane są wyłącznie w puli ZFS.

4. SSD zawiera jedynie system operacyjny i dane operacyjne usług.

5. Snapshoty ZFS stanowią pierwszą linię ochrony przed przypadkowym usunięciem danych.

6. Każda nowa usługa powinna wykorzystywać istniejący dataset lub uzasadniać utworzenie nowego.

7. Backup i Disaster Recovery opisane są w odrębnych dokumentach.

---

# Kierunek rozwoju

Nowe usługi powinny wykorzystywać istniejącą strukturę datasetów.

Nowe datasety tworzone są wyłącznie wtedy, gdy wymagają:

- odmiennej polityki snapshotów,
- innych uprawnień,
- innej kompresji,
- odmiennego sposobu udostępniania danych.