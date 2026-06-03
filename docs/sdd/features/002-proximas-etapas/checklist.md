# Feature 002 — Checklist de Qualidade (portões)

> Aplicar a cada incremento entregue desta feature.

## Portão 1 — Constituição preservada
- [ ] Runtime continua *vanilla* e o painel abre em `file://` (P1 / RNF2).
- [ ] Nenhuma dependência pesada adicionada sem ADR registrado.
- [ ] Documentos originais permanecem intocados (P2).

## Portão 2 — Dados
- [ ] `scripts/gerar-acervo.py` é idempotente (`git diff` vazio ao re-rodar).
- [ ] `data/acervo.json` reflete exatamente os arquivos do repositório.
- [ ] Fallback embutido funciona quando `fetch` não está disponível.

## Portão 3 — Integridade e CI
- [ ] CI falha ao referenciar arquivo inexistente.
- [ ] CI falha quando os dados gerados estão dessincronizados.
- [ ] Smoke test cobre: troca de aba, busca global, render do acervo.

## Portão 4 — UX
- [ ] Deep-link por aba (`#federal`, `#stj`, …) ativa a aba correta no load.
- [ ] Filtros novos não quebram os existentes.
- [ ] Sem regressão de responsividade/impressão/teclado.

## Portão 5 — Editorial
- [ ] Itens "a validar" só são promovidos após conferência em fonte oficial (T17/T18).
- [ ] Novos clippings mantêm o aviso editorial e a separação fato × opinião.
