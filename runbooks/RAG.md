# Runbook — Lokalny RAG dla HomeLab

**Status:** W trakcie realizacji  
**Host:** ai-node (Minisforum AI X1)  
**Data rozpoczęcia:** 2026-07-15

---

# Cel

Budowa lokalnego systemu RAG (Retrieval Augmented Generation), który umożliwia rozmowę z dokumentami bez wysyłania danych do chmury.

Docelowo system będzie wykorzystywany do:

- dokumentacji HomeLab,
- pracy doktorskiej,
- dokumentacji ISO,
- instrukcji maszyn,
- baz awarii,
- dokumentacji klientów.

Całość działa lokalnie.

---

# Architektura

```
Dokument

      │

      ▼

Docling

(parser)

      │

      ▼

JSON

Markdown

      │

      ▼

Czyszczenie

      │

      ▼

Chunkowanie

      │

      ▼

Embedding (BGE-M3)

      │

      ▼

Qdrant

      │

      ▼

Similarity Search

      │

      ▼

Gemma 4 (Ollama)

      │

      ▼

Open WebUI
```

---

# Zrealizowane etapy

## Etap 1 — AI Node

Status: ✅

- Ubuntu Server
- Docker
- UFW
- Ollama
- Open WebUI

---

## Etap 2 — GPU

Status: ✅

AMD Radeon 780M została poprawnie wykryta przez Ollamę.

```
PROCESSOR: 100% GPU
Library: Vulkan
```

Inference odbywa się na GPU.

---

## Etap 3 — Model LLM

Status: ✅

Model:

```
gemma4
```

Uruchamiany lokalnie przez Ollama.

---

## Etap 4 — Open WebUI

Status: ✅

Połączenie:

```
Open WebUI

↓

Ollama

↓

Gemma4
```

Zweryfikowano poprawność działania.

---

## Etap 5 — Embedding model

Status: ✅

Model:

```
bge-m3
```

Zainstalowany w Ollama.

Zweryfikowano działanie endpointu:

```
/api/embed
```

Model zwraca embedding 1024 wymiarów.

---

## Etap 6 — Qdrant

Status: ✅

Uruchomiono lokalny kontener.

Port:

```
6333
```

Dostęp wyłącznie z localhost.

---

## Etap 7 — Parser dokumentów

Status: ✅ (MVP)

Wybrano:

```
Docling
```

Powody:

- PDF
- DOCX
- PPTX
- XLSX
- HTML
- OCR
- Tabele
- Obrazy
- JSON

Parser działa lokalnie.

---

## Etap 8 — Środowisko parsera

Status: ✅

Utworzono niezależne środowisko Python:

```
/srv/rag/.venv
```

Parser jest całkowicie odseparowany od systemu operacyjnego.

---

## Etap 9 — OCR

Status: ✅

RapidOCR został automatycznie pobrany.

Parser rozpoznaje tekst znajdujący się na obrazach.

---

## Etap 10 — Czyszczenie dokumentów

Status: ✅

Usuwane są:

- spis treści
- nagłówki stron
- stopki
- numery stron

Pozostaje wyłącznie treść merytoryczna.

---

## Etap 11 — Chunkowanie

Status: ✅

Dokument dzielony jest na logiczne fragmenty.

Każdy chunk zawiera:

- tekst
- numer strony
- typ elementu

Test:

```
23 strony

↓

207 elementów

↓

28 chunków
```

---

# Aktualny stan

Działa:

```
PDF

↓

Docling

↓

JSON

↓

Clean

↓

Chunks
```

Kolejne etapy nie korzystają już z PDF.

Pracują wyłącznie na chunkach.

---

# Kolejne etapy

## Etap 12 — Embeddingi

Status:

⬜

Każdy chunk zostanie zamieniony na embedding BGE-M3.

---

## Etap 13 — Qdrant

Status:

⬜

Embeddingi zostaną zapisane w bazie wektorowej.

---

## Etap 14 — Retrieval

Status:

⬜

Zapytanie użytkownika będzie zamieniane na embedding.

Qdrant odnajdzie najbardziej podobne fragmenty.

---

## Etap 15 — Odpowiedź LLM

Status:

⬜

Gemma4 otrzyma:

- pytanie
- znalezione fragmenty

Model będzie odpowiadał wyłącznie na podstawie dokumentów.

---

# Plan rozwoju

Po zakończeniu MVP planowane są:

- [ ] obsługa wielu dokumentów
- [ ] indeksowanie katalogów
- [ ] automatyczne wykrywanie zmian
- [ ] wersjonowanie dokumentów
- [ ] OCR dla skanów
- [ ] analiza wykresów (Vision)
- [ ] analiza tabel
- [ ] Reranking
- [ ] Cytowania źródeł
- [ ] API dla aplikacji
- [ ] Integracja z Open WebUI
- [ ] Integracja z n8n

---

# Docelowe zastosowania

- Dokumentacja HomeLab
- Dokumentacja doktoratu
- ISO 9001
- ISO 14001
- ISO 50001
- Instrukcje maszyn
- Dokumentacja UR
- Baza awarii
- Dokumentacja klientów
- Procedury operacyjne

---

# Najważniejsza decyzja architektoniczna

Przyjęto architekturę modułową.

Każdy etap jest niezależny.

```
Parser

↓

Chunker

↓

Embedding

↓

Vector DB

↓

Retriever

↓

LLM
```

Dzięki temu w przyszłości możliwa jest wymiana dowolnego komponentu bez przebudowy całego systemu (np. Gemma → Qwen, Qdrant → Milvus, BGE-M3 → inny model embeddingowy)