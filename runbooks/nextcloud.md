# Nextcloud

## Powiązane dokumenty

- architecture/storage.md
- dashboard.md

## Status

✅ Działa poprawnie.

---

## Dostęp

### Publiczny

https://nextcloud.klucznik.biz

### LAN

http://192.168.100.22:8087

---

## Architektura

Internet

↓

Nginx Proxy Manager

↓

192.168.100.22:8087

↓

Nextcloud (Docker)

↓

MariaDB (SSD)

↓

Nextcloud Data (/tank/cloud)

---

## Storage

### Aplikacja

```
/home/cloud/docker/nextcloud-server_nextcloud_data/_data
```

Lokalizacja:

**SSD**

Zawiera:

- aplikację Nextcloud,
- konfigurację,
- aplikacje,
- motywy.

---

### Dane użytkowników

```
/tank/cloud
```

Lokalizacja:

**ZFS Mirror**

Dataset:

```
tank/cloud
```

Przechowuje:

- pliki użytkowników,
- strukturę PARA,
- dane WebDAV,
- dane synchronizowane z klientami.

---

### Baza danych

```
/home/cloud/docker/nextcloud-server_nextcloud_db/_data
```

Lokalizacja:

**SSD**

Silnik:

MariaDB 10.6

---

## Docker

### Kontenery

- nextcloud-app-1
- nextcloud-db-1

### Bind mounts

```
/home/cloud/docker/nextcloud-server_nextcloud_data/_data
    ↓
/var/www/html

/tank/cloud
    ↓
/var/www/html/data

/home/cloud/docker/nextcloud-server_nextcloud_db/_data
    ↓
/var/lib/mysql
```

---

## Weryfikacja

Status:

```bash
sudo docker exec -u www-data nextcloud-app-1 php occ status
```

Skan plików:

```bash
sudo docker exec -u www-data nextcloud-app-1 php occ files:scan --all
```

Sprawdzenie mountów:

```bash
sudo docker inspect nextcloud-app-1 --format '{{json .Mounts}}' | jq
```

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

Proxy Host ponownie korzysta z konfiguracji:

- Host: 192.168.100.22
- Port: 8087

### Wynik

Nextcloud działa poprawnie.

---

## Historia zmian

### 2026-07-08

- utworzono pulę ZFS `tank`,
- utworzono dataset `tank/cloud`,
- przeniesiono dane użytkowników na ZFS,
- pozostawiono aplikację i bazę danych na SSD,
- zaktualizowano Docker Compose o bind mount `/tank/cloud -> /var/www/html/data`,
- zweryfikowano poprawność migracji (`occ status`, `files:scan`, zapis nowych plików).