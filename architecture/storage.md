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

# Założenia

HomeLab wykorzystuje dwie warstwy przechowywania danych.

## Warstwa operacyjna (SSD)

Na dysku systemowym znajdują się:

- Ubuntu Server
- Docker Engine
- Docker Compose
- konfiguracje usług
- bazy danych
- logi systemowe
- dane operacyjne aplikacji

Dysk SSD nie służy do przechowywania danych użytkowników.

---

## Warstwa danych (ZFS)

Dwa dyski WD Red Plus 6 TB tworzą pulę ZFS Mirror.

Planowana nazwa puli:

```
tank
```

Wszystkie trwałe dane użytkowników przechowywane są w tej puli.

---

# Struktura puli

```
tank
├── nextcloud-data
├── immich-library
├── shared-media
├── backups
└── git
```

---

# Datasety

## nextcloud-data

Centralny magazyn danych użytkowników wykorzystywany przez Nextcloud.

Przechowuje między innymi:

- strukturę PARA
- dokumenty prywatne
- dokumenty rodzinne
- dokumenty firmowe
- materiały do doktoratu
- współdzielone pliki
- foldery klientów
- Zotero WebDAV

Dostęp:

- Nextcloud
- WebDAV

---

## immich-library

Biblioteka zdjęć i filmów.

Docelowo wykorzystywana przez Immich.

Przechowuje:

- zdjęcia
- filmy

---

## shared-media

Biblioteka dużych plików.

Przechowuje:

- obrazy ISO
- instalatory
- multimedia
- materiały techniczne

Dostęp:

- SMB

---

## backups

Centralna przestrzeń kopii zapasowych.

Przechowuje:

- backupy komputerów
- backupy Dockera
- eksporty baz danych
- konfiguracje
- kopie wybranych usług

---

## git

Przestrzeń przeznaczona dla repozytoriów Git oraz przyszłych usług developerskich.

Może zawierać:

- lokalne kopie repozytoriów
- archiwalne projekty
- przyszły serwer Forgejo/Gitea

---

# Dostęp do danych

| Dataset | Nextcloud | SMB | WebDAV | Immich |
|----------|-----------|-----|---------|---------|
| nextcloud-data | ✓ | ✗ | ✓ | ✗ |
| immich-library | ✗ | ✗ | ✗ | ✓ |
| shared-media | ✗ | ✓ | ✗ | ✗ |
| backups | ✗ | administrator | ✗ | ✗ |
| git | ✗ | opcjonalnie | ✗ | ✗ |

---

# Zasady projektowe

1. Dane należą do HomeLab, nie do aplikacji.

2. Aplikacje korzystają z danych, ale nie definiują ich struktury.

3. Wyjątkiem jest `nextcloud-data`, który jest wymaganym katalogiem danych Nextcloud.

4. Wszystkie dane użytkowników przechowywane są na ZFS.

5. SSD przechowuje wyłącznie dane operacyjne.

6. Każda nowa usługa powinna zostać przypisana do istniejącego datasetu lub uzasadnić utworzenie nowego.

7. Backup nie jest częścią architektury Storage i opisany jest w osobnym dokumencie.

---

# Kierunek rozwoju

Architektura została zaprojektowana z myślą o wieloletnim rozwoju HomeLab.

Dodawanie nowych usług powinno polegać przede wszystkim na wykorzystaniu istniejących datasetów.

Nowe datasety tworzone są wyłącznie wtedy, gdy wymagają odrębnych właściwości ZFS (snapshotów, uprawnień, kompresji lub sposobu udostępniania).