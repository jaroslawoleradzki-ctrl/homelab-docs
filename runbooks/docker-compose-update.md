# Aktualizacja stosu Docker Compose

## Założenia

Procedura dotyczy pojedynczego stosu. Nie aktualizuj wszystkich usług jednocześnie.

## Przed aktualizacją

```bash
cd /srv/compose/NAZWA_STOSU
sudo docker compose ps
sudo docker compose config > /tmp/NAZWA_STOSU-compose-$(date +%F).yaml
sudo docker compose images
```

Sprawdź dokumentację wydania aplikacji i wykonaj wymagany backup. Dla usług bazodanowych backup bazy jest obowiązkowy.

## Aktualizacja

```bash
sudo docker compose pull
sudo docker compose up -d
sudo docker compose ps
sudo docker compose logs --tail 100
```

## Weryfikacja

- otwórz aplikację,
- sprawdź logowanie i podstawową funkcję,
- sprawdź stan w Uptime Kuma i Beszel,
- potwierdź brak pętli restartów:

```bash
sudo docker ps --format 'table {{.Names}}\t{{.Status}}'
```

## Wycofanie

Jeżeli nowa wersja nie działa:

1. nie usuwaj wolumenów,
2. ustaw poprzedni tag obrazu w `compose.yaml`,
3. uruchom `sudo docker compose pull && sudo docker compose up -d`,
4. w razie migracji bazy użyj procedury odtworzeniowej właściwej dla aplikacji.

## Dokumentacja

Zapisz nazwę stosu, poprzednią i nową wersję, wykonany backup oraz wynik testu w `CHANGELOG.md`.