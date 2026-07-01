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

HomeLab wykorzystuje dwie warstwy przechowywania danych:

## Warstwa operacyjna (SSD)

Na dysku SSD znajdują się elementy wymagające wysokiej wydajności:

- Ubuntu Server
- Docker Engine
- Docker Compose
- konfiguracje usług
- bazy danych
- cache
- logi systemowe

SSD nie służy do przechowywania dużych danych użytkownika.

---

## Warstwa danych (ZFS)

Dwa dyski HDD 6 TB tworzą pulę ZFS Mirror.

Warstwa ta przechowuje wszystkie dane użytkownika oraz trwałe dane aplikacji.

Planowana nazwa puli:

tank

---

# Klasy danych

HomeLab przechowuje sześć podstawowych klas danych.

## Cloud

Centralna prywatna chmura oparta o Nextcloud.

Przechowuje:

- strukturę PARA
- dokumenty prywatne
- dokumenty rodzinne
- dokumenty firmowe
- materiały do doktoratu
- współdzielone pliki rodziny

Dataset:

tank/cloud

---

## Photos

Biblioteka zdjęć.

Docelowo:

- kopia zdjęć z urządzeń Apple
- możliwość korzystania z alternatywnych aplikacji do zarządzania zdjęciami

Dataset:

tank/photos

---

## Media

Biblioteka multimediów.

Obejmuje:

- filmy
- muzykę

Dataset:

tank/media

---

## AI

Środowisko eksperymentalne.

Przechowuje:

- modele AI
- embeddingi
- bazy RAG
- dane eksperymentalne

Dataset:

tank/ai

---

## Backups

Centralna przestrzeń kopii zapasowych.

Obejmuje:

- Time Machine
- kopie komputerów Linux
- backupy Dockera
- eksporty baz danych
- konfiguracje

Dataset:

tank/backups

---

## Zotero WebDAV

Przestrzeń przeznaczona wyłącznie dla synchronizacji załączników Zotero.

Dataset:

tank/zotero-webdav

---

# Zasady projektowe

1. Dane należą do HomeLab, nie do aplikacji.

2. Aplikacje korzystają z danych, ale nie definiują ich struktury.

3. Wszystkie duże dane przechowywane są na ZFS.

4. SSD przechowuje wyłącznie dane operacyjne.

5. Każda nowa usługa powinna zostać przypisana do jednej z istniejących klas danych lub uzasadnić utworzenie nowej.

6. Backup nie jest częścią storage i opisany jest w osobnym dokumencie.

---

# Kierunek rozwoju

Architektura została zaprojektowana z myślą o wieloletnim rozwoju HomeLab.

Dodawanie nowych usług nie powinno wymagać zmiany struktury danych, a jedynie przypisania usługi do odpowiedniej klasy danych.