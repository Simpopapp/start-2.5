# Stage 04 — Validação dos artefatos

**Data:** 2026-10-08
**Status:** concluída

## O que foi feito
- Validador automático: `data/validate_songs_tipo_c.py`.
- Checagens: existência dos 22 txt; fidelidade palavra a palavra das frases do dataset dentro das letras; letra ≥ ~2000 chars; tags Suno presentes; estilo ≤ 200 chars e sem colchetes.
- Resultado: **VALIDACAO OK** — 11 grupos × 2 txt, fidelidade confirmada (301 frases do dataset; 330 posições checadas por repetição).

## Evidências
- Execução: `python3 data/validate_songs_tipo_c.py` → `VALIDACAO OK`.
- Teste de regra no projeto: `src/test/wfd-songs-c.test.ts` (3 asserts: 11 estruturas, estilo ≤ 200 sem colchetes, fidelidade palavra a palavra) — verde.
