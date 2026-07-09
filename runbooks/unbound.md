# Unbound

## Cel

Unbound jest lokalnym rekursywnym serwerem DNS wykorzystywanym przez Pi-hole jako jedyny upstream DNS.

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
Root DNS
```

---

# Architektura

- Docker
- Kontener: `unbound`
- Obraz: `mvance/unbound:latest`
- Port hosta: **5335**
- Port kontenera: **53**

Mapowanie portów:

```yaml
ports:
  - "5335:53/tcp"
  - "5335:53/udp"
```

---

# Konfiguracja Pi-hole

Upstream DNS:

```
127.0.0.1#5335
```

Drugi serwer DNS:

```
wyłączony
```

Dzięki temu wszystkie zapytania DNS są rozwiązywane lokalnie przez Unbound.

---

# Pliki konfiguracyjne

Kontener wymaga obecności następujących plików:

- `a-records.conf`
- `srv-records.conf`
- `forward-records.conf`

Nawet jeśli są puste, muszą istnieć.

---

# Test poprawności

Sprawdzenie odpowiedzi DNS:

```bash
dig @127.0.0.1 -p 5335 google.com
```

Oczekiwany wynik:

```
status: NOERROR
```

---

# Diagnostyka

## Status kontenera

```bash
docker ps
```

lub

```bash
docker inspect unbound
```

---

## Logi

```bash
docker logs unbound
```

---

## Typowe problemy

### Kontener restartuje się

Najczęstsze przyczyny:

- brak wymaganych plików konfiguracyjnych,
- błędne mapowanie portów,
- niepoprawna konfiguracja stacka.

---

### Pi-hole nie rozwiązuje nazw

Sprawdzić:

- czy Unbound działa,
- czy odpowiada na porcie 5335,
- czy Pi-hole wskazuje `127.0.0.1#5335` jako jedyny upstream DNS.

---

# Aktualizacja

Zmiany konfiguracji należy wykonywać przez aktualizację Stacka w Portainerze.

Nie należy edytować działającego kontenera.

---

# Historia

## 2026-07-01

- utworzono brakujące pliki konfiguracyjne,
- poprawiono mapowanie portów `5335 → 53`,
- przywrócono stabilną pracę usługi.