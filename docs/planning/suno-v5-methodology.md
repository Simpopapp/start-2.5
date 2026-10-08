# Guia Metodológico — Estruturas Suno V5 no estilo Imagine Dragons (project4)

> Fonte de verdade para os subagentes da Fase 3. Base: `.opencode/prompt-replicar-artista.md`
> + pesquisa web ( ToneDraft, Suno Field Guide, guias v5/v5.5 de 2026 — ver PRD §4).

## 0. Regra suprema (OBSERVAÇÃO CONTRADITÓRIA)

As frases do grupo são **intocáveis**: nenhuma palavra muda, nenhuma palavra é cortada,
nenhuma é adicionada ao corpo lírico. O trabalho é exclusivamente **estrutural**:
dividir as frases em seções, ordenar a performance e intercalar instruções (em inglês)
para que o Suno V5 cante o texto exatamente igual.

## 1. Formato Suno V5 (verificado em 2026)

Campo de letra (Lyrics):
- Metatags entre colchetes, **uma por linha**, sempre **antes** do conteúdo que descrevem.
- Tags estruturais canônicas: `[Intro]`, `[Verse 1]`, `[Verse 2]`, `[Pre-Chorus]`,
  `[Chorus]`, `[Post-Chorus]`, `[Bridge]`, `[Breakdown]`, `[Build]`, `[Drop]`, `[Solo]`,
  `[Interlude]`, `[Outro]`, `[End]`, `[Fade Out]`.
- Forma parametrizada (v5+): `[Verse: whispered vocals, sparse piano]`,
  `[Chorus: anthemic belted vocals, stadium claps]` — combine seção + direção de entrega.
- Tag stacking com `|`: `[Chorus | stacked harmonies | huge drums]` — máx. 4–8 dentro de
  um mesmo colchete.
- Ad-libs: parênteses em linha própria, ≤ 3 palavras: `(yeah)`, `(hold on)`.
- Repetição: **duplique fisicamente a linha**; `(x2)` é pouco confiável.
- Tag inline no meio da linha de letra é ignorada — nunca faça isso.
- O campo de letra comporta até ~5000 chars, mas acima de ~3000 a música "corre";
  alvo do projeto: ~2000 chars totais por letra (≈1000 líricos + ≈1000 instruções).

Campo de estilo (Style):
- Linguagem natural **sem colchetes**, separada por vírgulas.
- Ordem: gênero/subgênero → mood/energia → voz → instrumentos-chave → produção → tempo.
- **Front-load**: os primeiros termos pesam mais.
- **Nunca usar nome de artista** (o Suno remove/bloqueia). Descreva a assinatura sonora.
- Limite do projeto (especificação do usuário): **≤ 200 caracteres**.

## 2. DNA sonoro "Imagine Dragons" (descrição sem o nome)

Referência artística do projeto. Assinatura a descrever no style field e nas instruções:
- Alternative rock / pop-rock antemico com percussão tribal grande (stomps, claps, toms).
- Arco dinâmico quiet→loud: verso contido e quase falado → refrão explosivo.
- Vocal masculino: barítono tenor emotivo, falsete em momentos íntimos, belt com rasgo
  no clímax; gang vocals e "whoa-oh" coletivos no refrão.
- Camadas cinemáticas: sintetizadores escuros, piano melódico, guitarra texturizada,
  baixo pulsante, cordas em crescendo.
- Letra confessional/urgent­e: imagens concretas de luta interna, luz vs. escuridão,
  superação — mas SEM alterar as frases do dataset (regra suprema). O tema emerge da
  escolha de quais frases viram verso, pré-refrão ou refrão.
- BPM típico: 100–124 (meio-tempo percussivo); construir no mínimo um `[Build]` e um
  clímax de refrão com `Energy: Maximum`.

## 3. Estágios de produção (obrigatórios por estrutura)

1. **Análise** — ler as 30 frases do grupo; identificar tema dominante, repetições,
   imagens fortes, candidato a hook (frase-ímpar curta e marcante).
2. **Arranjo** — plano de seções: quais frases em [Verse]/[Pre-Chorus]/[Chorus]/
   [Bridge]/[Outro]; BPM, tonalidade sugerida, arco de energia; repetições planejadas
   (duplicação física de linhas, nunca reescrita).
3. **Redação** — escrever `letra.txt` com marcações Suno V5 e instruções de performance
   embutidas (inglês): dinâmica, timbre, respiração, ad-libs, BPM por seção.
4. **Revisão de fidelidade** — conferir palavra a palavra: as 30 frases aparecem
   íntegras. Ajustes só nas marcações, nunca no texto.
5. **Estilo** — escrever `estilo.txt` (≤ 200 chars, inglês, sem colchetes, sem nome de
   artista, vírgulas, front-load).
6. **Checagem de limites** — letra ≥ ~2000 chars; estilo ≤ 200 chars.

## 4. Contrato de saída do subagente

Cada subagente recebe: número do grupo (1–11), caminho do dataset
(`data/wfd-groups-c.json`) e este guia. Entrega na mensagem final, exatamente nestes
blocos:

```
===LETRA GRUPO NN===
(conteúdo integral do letra.txt)
===ESTILO GRUPO NN===
(conteúdo integral do estilo.txt)
===CHECKLIST===
frases: 30/30 íntegras | letra: N chars | estilo: N chars | bpm: NN | hook: "<frase>"
```

Sem resumos parciais dentro dos blocos; o conteúdo dos blocos é o artefato final.
