# Lokalny RAG

## Cel

Projekt ma zapewnić lokalne przetwarzanie dokumentów, generowanie embeddingów, indeksowanie w bazie wektorowej i wyszukiwanie fragmentów bez używania publicznej chmury AI.

## Lokalizacja

- host: `ai-node`,
- katalog projektu: `/srv/rag`,
- virtualenv: `/srv/rag/.venv`.

## Architektura

```text
PDF
 │
 ▼
Docling + RapidOCR
 │
 ▼
czyszczenie tekstu
 │
 ▼
chunking 300–800 tokenów
 │
 ▼
BGE-M3 przez Ollama
 │
 ▼
Qdrant
 │
 ▼
retrieve.py
```

## Komponenty

| Komponent | Rola |
|---|---|
| Docling | ekstrakcja treści z dokumentów |
| RapidOCR | OCR |
| BGE-M3 | embeddingi 1024-wymiarowe |
| Ollama | API modeli lokalnych |
| Qdrant | baza wektorowa |
| Open WebUI | przyszły interfejs użytkownika dla RAG |

## Stan testu

Przetworzono plik `protocol.pdf`.

Powstały:

- `protocol-clean.json`,
- `protocol-chunks.jsonl`,
- `protocol-embeddings.jsonl`.

Testowa kolekcja Qdrant:

- nazwa: `rag_chunks_bge_m3`,
- metryka: Cosine,
- liczba punktów testowych: 28.

Skrypt `retrieve.py` zwraca trafne fragmenty dla pytań dotyczących protokołu SLR.

## Skrypty

- `embed_chunks.py`,
- `index_qdrant.py`,
- `retrieve.py`.

## Następne kroki

- stabilne API projektu,
- automatyczny ingestion dokumentów,
- metadane źródeł i numerów stron,
- integracja z Open WebUI,
- ewaluacja jakości wyszukiwania,
- kontrola duplikatów,
- dokumentacja wdrożenia i odtwarzania.
