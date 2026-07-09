# Security Architecture

## Cel

Dokument opisuje mechanizmy bezpieczeństwa zastosowane w HomeLab oraz kierunek ich dalszego rozwoju.

Bezpieczeństwo obejmuje ochronę:

- infrastruktury,
- danych,
- usług,
- dostępu administracyjnego.

---

# Warstwy bezpieczeństwa

HomeLab wykorzystuje wielowarstwowy model zabezpieczeń:

1. Ubuntu Server
2. Docker
3. ZFS
4. Reverse Proxy
5. Nextcloud
6. Uwierzytelnianie
7. Backup

---

# System operacyjny

System:

- Ubuntu Server 24.04 LTS

Założenia:

- minimalna instalacja,
- wyłącznie niezbędne pakiety,
- aktualizacje bezpieczeństwa,
- administracja przez SSH.

---

# Dostęp administracyjny

Administracja serwerem odbywa się przez:

- SSH
- Tailscale (planowane rozszerzenie dokumentacji)

Port:

```
22
```

Dostęp administracyjny powinien być ograniczony wyłącznie do zaufanych urządzeń.

---

# Docker

Każda usługa działa jako oddzielny kontener Docker.

Korzyści:

- izolacja usług,
- łatwiejsze aktualizacje,
- prostsze odtwarzanie środowiska,
- ograniczenie wpływu awarii pojedynczej usługi.

---

# Storage

Dane użytkowników przechowywane są w:

```
tank
```

Mechanizmy ochrony:

- ZFS Mirror,
- Snapshoty Sanoid,
- monitoring SMART.

---

# Reverse Proxy

Za publikację usług odpowiada:

Nginx Proxy Manager.

Odpowiada za:

- HTTPS,
- certyfikaty SSL,
- mapowanie domen,
- publikację usług.

---

# DNS

Zapytania DNS realizowane są lokalnie:

```text
Urządzenie
     │
     ▼
Pi-hole
     │
     ▼
Unbound
     │
     ▼
Root DNS
```

Dzięki temu HomeLab nie korzysta z publicznych resolverów DNS.

---

# Nextcloud

Dostęp do danych użytkowników realizowany jest przez:

- HTTPS,
- konta użytkowników,
- WebDAV.

WebDAV Zotero wykorzystuje ten sam mechanizm uwierzytelniania co Nextcloud.

---

# Uwierzytelnianie

Obecnie wykorzystywane są:

- silne, unikalne hasła,
- Bitwarden jako menedżer haseł,
- 2FA dla wybranych usług.

Planowane jest rozszerzenie 2FA na wszystkie usługi, które je obsługują.

---

# Kopie zapasowe

Ochrona danych obejmuje:

- ZFS Mirror,
- Snapshoty ZFS,
- Time Machine,
- Backup SMB,
- Git.

Szczegóły opisano w:

```
architecture/backup.md
```

---

# Aktualizacje

Każda aktualizacja usługi powinna obejmować:

1. wykonanie snapshotu ZFS,
2. aktualizację kontenera,
3. test działania,
4. aktualizację dokumentacji,
5. commit Git.

---

# Obszary do rozwoju

Planowane jest wdrożenie:

- HTTPS dla wszystkich usług,
- pełnej dokumentacji Tailscale,
- centralnego zarządzania certyfikatami,
- automatycznego backupu konfiguracji Docker,
- procedur Disaster Recovery,
- monitorowania bezpieczeństwa.

---

# Zasady administracyjne

1. Dane należą do infrastruktury, nie do kontenerów.

2. Każda trwała zmiana infrastruktury wymaga aktualizacji dokumentacji.

3. Każda zmiana kończy się commitem Git.

4. Konfiguracja usług powinna być odtwarzalna z repozytorium.

5. Backup powinien być regularnie testowany.

---

# Historia

## 2026-07

- wdrożono ZFS Mirror,
- skonfigurowano snapshoty Sanoid,
- wdrożono monitoring SMART,
- ustabilizowano Unbound,
- przeniesiono Zotero WebDAV do Nextcloud,
- uporządkowano architekturę bezpieczeństwa.