# Feature 002 — Plano Técnico

## Estratégia de integração

Evolução **incremental e retrocompatível**: cada item entra sem quebrar o painel atual nem
violar P1. Build opcional (Python/CI) gera artefatos estáticos; o runtime continua *vanilla*.

## Abordagem por requisito

### RF-202.1 / RF-202.3 — Dados como artefatos versionados
- Extrair o gerador embutido em `tasks.md` para `scripts/gerar-acervo.py`.
- Emitir `data/acervo.json` e (futuro) `data/registros.json`.
- No painel, manter o **fallback embutido** para `file://` e tentar `fetch('data/acervo.json')`
  quando servido por HTTP (progressive enhancement, preserva RNF2).

### RF-202.4 — Deep-linking
- `showTab` passa a atualizar `location.hash`; no `load`, ler o hash e ativar a aba.
- Opcional: hash para abrir ficha (`#registro=lc-214-2025`).

### RF-202.5 — CI de integridade
- Workflow `.github/workflows/validar.yml`:
  - Extrai todos os `href="…"` relativos do `index.html` e confere no filesystem.
  - Confere que o `data/acervo.json` está sincronizado (re-rodar o gerador e `git diff`).
  - Roda um *smoke test* headless (ex.: `node` + jsdom ou Playwright) das funções de aba/busca.

### RF-202.6 — Busca de conteúdo
- Em build, extrair texto dos PDFs (`pdftotext`/`pdfminer`) para um índice `data/fulltext.json`
  (campos: id, trecho). Servido estático; a busca global passa a consultar também esse índice
  quando disponível. Não roda no navegador (P1).

### RF-202.7 — Cobertura ampliada
- Generalizar `data-ambito` para incluir `Estadual` e `Internacional`.
- Adicionar registros/fichas para os PLs do `material-complementar` e municípios citados.

### RF-202.8 — Exportação e visualização
- Export CSV: gerar client-side a partir do índice em memória (sem dependência).
- Gráficos: avaliar SVG inline simples; só usar lib via CDN se justificado em ADR.

## Sequenciamento sugerido

1. RF-202.1 + RF-202.5 (dados + CI) → reduz risco e custo de manutenção primeiro.
2. RF-202.4 (deep-link) → ganho de UX barato.
3. RF-202.7 (cobertura) + RF-202.3 (registros em JSON).
4. RF-202.2 (filtros acervo) + RF-202.8 (export/gráficos).
5. RF-202.6 (full-text) → maior esforço, menor prioridade.

## Riscos

| Risco | Mitigação |
|-------|-----------|
| `fetch` quebra em `file://` | Manter manifesto embutido como fallback. |
| Dependência pesada fere P1 | ADR obrigatório; preferir build estático. |
| Drift entre dados e HTML | CI que re-gera e compara (`git diff --exit-code`). |
