# HomeLab

**Wersja dokumentacji:** 0.1  
**Data utworzenia:** 2026-07-01

## Cel projektu

HomeLab jest prywatnym środowiskiem serwerowym opartym o Docker, którego zadaniem jest wspieranie:

- działalności konsultingowej,
- rozwoju własnych aplikacji,
- zarządzania dokumentacją,
- środowiska AI,
- automatyzacji,
- monitoringu infrastruktury,
- bezpiecznego przechowywania danych.

Dokumentacja jest rozwijana równolegle z projektem.

## Stan obecny

- Hostname: `homelab`
- IP LAN: `192.168.100.22`
- System: Ubuntu 24.04.4 LTS
- Kernel: Linux 6.8.0-124
- Architektura: x86_64
- Sprzęt: HP EliteDesk 800 G3 SFF
- Kontenery: Docker

## Główne usługi

- Nextcloud
- Paperless-ngx
- Pi-hole
- Unbound
- Nginx Proxy Manager
- Homepage
- Beszel
- Uptime Kuma
- OpenProject
- Stirling PDF
- OpenRefine
- WebDAV dla Zotero

## Znane problemy

- Unbound restartuje się i wymaga diagnostyki.
- Dysk systemowy jest zajęty w około 70–75%.
- Backupy wymagają pełnego opisania.
- Sieci i wolumeny Docker wymagają inwentaryzacji.

## Zasada prowadzenia dokumentacji

Każda trwała zmiana w HomeLabie powinna zostać opisana w dokumentacji i zatwierdzona commitem w Git.
---

# Runbooki

Dokumentacja operacyjna znajduje się w katalogu `runbooks`.

## Dostępne

- [Unbound](runbooks/unbound.md)

## Dokumentacja

### Dashboard administratora

- [Dashboard](inventory/dashboard.md)

### Runbooki

- [Unbound](runbooks/unbound.md)