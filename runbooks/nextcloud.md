# Nextcloud

## Status

✅ Działa poprawnie.

---

## Dostęp

Aktualna domena:

https://nextcloud.klucznik.biz

Backend:

http://192.168.100.22:8087

---

## Architektura

Internet
↓
Nginx Proxy Manager
↓
192.168.100.22:8087
↓
Nextcloud

---

## Incydent 2026-07-01

### Objawy

HTTP 502 Bad Gateway.

### Przyczyna

W konfiguracji Nginx Proxy Manager znajdowały się wpisy w **Custom Locations**:

```
/hosting/
/ 
```

które przekierowywały ruch na:

```
192.168.100.242:8080
```

Był to nieaktualny adres backendu.

### Rozwiązanie

Usunięto wszystkie wpisy z **Custom Locations**.

Proxy Host zaczął ponownie korzystać z konfiguracji głównej:

- Host: 192.168.100.22
- Port: 8087

### Wynik

Nextcloud działa poprawnie.