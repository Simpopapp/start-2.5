# Stage 02 — Geração das 3 versões de grupos (project3)

Status: completed
Date: 2026-10-08

## O que foi entregue
- Script gerador determinístico `data/generate_group_versions.py` (dataset → A por song_group; B fatias de 20; C fatias de 30).
- 3 JSONs: `data/wfd-groups-a.json` (31 grupos), `data/wfd-groups-b.json` (16 grupos: 15×20+1×1), `data/wfd-groups-c.json` (11 grupos: 10×30+1×1), 301 frases cada, UTF-8 sem BOM, `ensure_ascii=False`, `indent=2`.
- 4 módulos TS: `src/data/wfd-groups-a.ts`, `wfd-groups-b.ts`, `wfd-groups-c.ts` (mesmo formato de `wfd-groups.ts`) + `src/data/wfd-group-versions.ts` (mapa A/B/C com labels e contagens).
- Script de validação `data/validate_group_versions.py` (totais, tamanhos, fidelidade frase a frase, A == original).
- Roadmap `.opencode/roadmap-proj3.md` Fase 2 marcada `[x]` com linha de Gates.

## Arquivos / áreas tocadas
- `data/generate_group_versions.py` (novo)
- `data/validate_group_versions.py` (novo)
- `data/wfd-groups-a.json`, `data/wfd-groups-b.json`, `data/wfd-groups-c.json` (novos)
- `src/data/wfd-groups-a.ts`, `wfd-groups-b.ts`, `wfd-groups-c.ts`, `wfd-group-versions.ts` (novos)
- `.opencode/roadmap-proj3.md` (Fase 2 marcada)
- Intocados: `data/wfd-dataset.json`, `data/wfd-groups.json`, `src/routes/index.tsx`

## Notas para o monitor
- Fontes de escopo (protocolo 3 arquivos): `.opencode/project3.md` → `.opencode/prd-project3.md` → `.opencode/roadmap-proj3.md` (Fases 1-4; Fase 1 e 2 concluídas).
- Gates Fase 2: `python3 data/validate_group_versions.py` → VALIDACAO OK; Tipo A idêntico ao original; dataset intocado (git status só mostra novos); `bunx tsc --noEmit` limpo.
- OpenCode NÃO usado para produção (regra AGENTS.md); usado apenas como monitor (recebimento do estado inicial confirmado em ses_ee5a8636cffe7c4D3UcmpF6Elg).
