# Network Architecture

## Cel

Dokument opisuje architekturę sieci HomeLab oraz sposób komunikacji pomiędzy usługami.

---

# Topologia

```text
                 Internet
                     │
                     ▼
                 Router ISP
                     │
                     ▼
          Sieć LAN 192.168.100.0/24
                     │
         ┌───────────┴───────────┐
         │                       │
         ▼                       ▼
   HomeLab Server          Pozostałe urządzenia
   192.168.100.22
```

---

# Serwer

| Parametr | Wartość |
|----------|----------|
| Hostname | homelab |
| Adres LAN | 192.168.100.22 |
| System | Ubuntu Server 24.04 LTS |

---

# Warstwy sieci

## Dostęp lokalny (LAN)

Usługi dostępne bezpośrednio po adresie IP oraz odpowiednim porcie.

Przykłady:

- Nextcloud
- Homepage
- Immich
- Paperless
- OpenProject

---

## Reverse Proxy

Za publikację usług odpowiada:

Nginx Proxy Manager

Obsługuje:

- HTTPS
- certyfikaty SSL
- mapowanie domen
- publikację usług

---

## DNS

Rozwiązywanie nazw:

```
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

---

## Docker

Komunikacja pomiędzy usługami odbywa się przez sieci Docker Compose.

Szczegółowa dokumentacja sieci Docker zostanie przygotowana w przyszłości.

---

# Dostęp zdalny

## Tailscale

Status:

⏳ planowane rozszerzenie dokumentacji.

---

# Porty usług

| Usługa | Port |
|---------|-----:|
| Homepage | 3000 |
| Pi-hole | 8080 |
| Nextcloud | 8087 |
| Paperless | 8010 |
| Stirling PDF | 8020 |
| Beszel | 8060 |
| OpenProject | 8090 |
| Immich | 2283 |
| Nginx Proxy Manager | 80,81,443 |
| Collabora | 9980 |

---

# Kierunek rozwoju

Planowane jest:

- pełna dokumentacja sieci Docker,
- pełna integracja z Tailscale,
- uporządkowanie nazw domen i subdomen.