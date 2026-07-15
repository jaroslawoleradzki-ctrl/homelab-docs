# AI Node – Day 0

## Cel

Przygotowanie nowego serwera AI (Minisforum AI X1) do pracy jako węzeł AI w HomeLab.

---

# Etap 1 – Odbiór sprzętu

## Zadania

- [x] Rozpakowanie i kontrola sprzętu.
- [x] Pierwsze uruchomienie Windows 11 Pro.
- [x] Połączenie z Internetem.
- [x] Sprawdzenie aktywacji systemu.
- [x] Zanotowanie wersji BIOS.

**Rezultat:** komputer działa poprawnie, Windows jest aktywowany.

---

# Etap 2 – Backup fabrycznego dysku

## Zadania

- [x] Uruchomienie Clonezilli.
- [x] Wykonanie obrazu całego dysku.
- [x] Zapis obrazu na serwerze HomeLab:

```text
/tank/backups/minisforum/
```

**Rezultat:** możliwość pełnego przywrócenia fabrycznego Windows.

---

# Etap 3 – Konfiguracja BIOS

## Do sprawdzenia

- [x] UEFI Boot
- [x] Power On After AC Loss
- [x] Wake-on-LAN
- [x] SVM (AMD Virtualization)
- [x] IOMMU
- [x] Kolejność bootowania

---

# Etap 4 – Instalacja Ubuntu Server 26.04 LTS

## Plan partycjonowania

| Partycja | Rozmiar |
|----------|---------:|
| EFI | 1 GB |
| /boot | 2 GB |
| / | 100 GB |
| /data | pozostała przestrzeń |

---

# Etap 5 – Aktualizacja systemu

- [x] Aktualizacja pakietów.
- [x] Restart.
- [x] Sprawdzenie wersji kernela.

---

# Etap 6 – Konfiguracja podstawowa

- [x] Hostname
- [x] SSH
- [x] Konfiguracja sieci
- [x] Test połączenia z HomeLab

---

# Etap 7 – Docker

- [x] Instalacja Docker Engine.
- [x] Instalacja Docker Compose.
- [x] Test działania.

---

# Etap 8 – Ollama

- [x] Instalacja Ollama.
- [x] Pobranie pierwszego modelu.
- [x] Weryfikacja wykorzystania CPU/GPU.

---

# Etap 9 – Open WebUI

- [x] Uruchomienie kontenera.
- [x] Połączenie z Ollamą.
- [x] Test rozmowy z modelem.

---

# Zakończenie Day 0

Na tym etapie komputer powinien posiadać:

- Ubuntu Server 26.04 LTS,
- Docker,
- Ollama,
- Open WebUI,
- działający lokalny model AI,
- możliwość przywrócenia fabrycznego Windows z obrazu Clonezilli.

**Nie instalujemy jeszcze:**

- n8n,
- Qdrant,
- RAG,
- MCP,
- Hermes.

Te elementy zostaną wdrożone w kolejnych etapach projektu AI Node.