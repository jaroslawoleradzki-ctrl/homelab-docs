# Unbound

## Cel

Unbound jest lokalnym rekursywnym serwerem DNS wykorzystywanym przez Pi-hole.

Schemat działania:

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
Internet Root DNS
```

---

# Konfiguracja

## Docker

```yaml
ports:
  - "5335:53/tcp"
  - "5335:53/udp"
```

Konfiguracja Pi-hole:

```text
DNS1 = 127.0.0.1#5335
DNS2 = no
```

---

# Naprawa z dnia 2026-07-01

## Objawy

Kontener `unbound` restartował się w pętli.

Logi zawierały błędy:

- brak `a-records.conf`
- brak `srv-records.conf`
- brak `forward-records.conf`

Dodatkowo Docker mapował port:

```text
5335 -> 5335
```

podczas gdy Unbound nasłuchuje wewnątrz kontenera na porcie:

```text
53
```

---

## Wykonana naprawa

Utworzono brakujące pliki:

- `a-records.conf`
- `srv-records.conf`
- `forward-records.conf`

Poprawiono mapowanie portów:

```yaml
ports:
  - "5335:53/tcp"
  - "5335:53/udp"
```

---

## Test poprawności

Na serwerze wykonano:

```bash
dig @127.0.0.1 -p 5335 google.com
```

Wynik:

```text
status: NOERROR
```

Kontener działa poprawnie i odpowiada na zapytania DNS.

---

# Uwagi

Każda zmiana konfiguracji Unbound powinna być wykonywana przez aktualizację Stacka w Portainerze, a nie przez ręczne modyfikowanie działającego kontenera.