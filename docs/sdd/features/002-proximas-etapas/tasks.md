# Feature 002 — Tarefas

Legenda: ⬜ pendente · 🔜 próxima · ✅ concluída

## Sprint 1 — Dados e qualidade (fundação)
- 🔜 T01 — Criar `scripts/gerar-acervo.py` (extrair o gerador de `001/tasks.md`) e emitir `data/acervo.json`.
- 🔜 T02 — Painel: tentar `fetch('data/acervo.json')` quando em HTTP, com fallback ao manifesto embutido.
- 🔜 T03 — Workflow `.github/workflows/validar.yml`: validar links relativos do `index.html`.
- ⬜ T04 — CI: re-rodar o gerador e falhar se `data/acervo.json` estiver dessincronizado.

## Sprint 2 — UX
- ⬜ T05 — Deep-linking por aba via `location.hash` (`showTab` escreve; `load` lê).
- ⬜ T06 — Deep-link opcional para abrir ficha por id.
- ⬜ T07 — Filtros do acervo por categoria, país e ano.

## Sprint 3 — Cobertura regulatória
- ⬜ T08 — Adicionar registros + fichas para PLs do material complementar
  (Salvino, Flávio Valle, Minuta Regulação/Tributação, Projeto 2237, 372/2025, 396/2025).
- ⬜ T09 — Adicionar municípios citados (Salvador, Curitiba, Olímpia, Ponta Grossa) com link/fonte.
- ⬜ T10 — Generalizar âmbito para `Estadual` e `Internacional` (aba/filtros).

## Sprint 4 — Registros orientados a dados
- ⬜ T11 — Migrar registros jurídicos para `data/registros.json` + render por JS (mantendo modais).
- ⬜ T12 — Atualizar contadores do cabeçalho automaticamente a partir dos dados.

## Sprint 5 — Avançado
- ⬜ T13 — Export CSV da visão atual (client-side, sem dependência).
- ⬜ T14 — Gráficos simples (distribuição por âmbito/ano) em SVG inline.
- ⬜ T15 — Índice full-text dos PDFs em build (`data/fulltext.json`) + busca de conteúdo.
- ⬜ T16 — Smoke test headless das funções de aba/busca/acervo no CI.

## Dívidas / validações pendentes herdadas
- ⬜ T17 — Validar a fonte oficial da **Operação Litus** antes de promover de "a validar" a publicado.
- ⬜ T18 — Conferir números/datas dos itens de 2026 contra fontes oficiais ao publicar.
