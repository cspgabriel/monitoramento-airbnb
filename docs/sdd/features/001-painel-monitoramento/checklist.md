# Feature 001 — Checklist de Qualidade (portões)

## Portão 1 — Conformidade com a constituição
- [x] Arquivo único, zero dependências, sem build (P1 / A1 / A2).
- [x] Documentos referenciados por caminho relativo, sem alterar os originais (P2 / A5).
- [x] Fato jurídico separado de clipping; aviso editorial presente; itens "a validar" sinalizados (P3).
- [x] Conteúdo em pt-BR, datado, com fonte; data de atualização exibida (P5).

## Portão 2 — Funcional
- [x] As 9 abas alternam corretamente e rolam ao topo.
- [x] Filtros de tabela, status, município, âmbito e categoria de clipping funcionam.
- [x] Modais abrem/fecham (clique fora, botão ✕ e ESC).
- [x] Busca global retorna e abre resultados das 4 origens (registro/artigo/clipping/acervo).
- [x] Aba Acervo renateriza ao filtrar/buscar e agrupa por subpasta.

## Portão 3 — Integridade de dados
- [x] 9/9 links de documento das modais existem no repositório.
- [x] 129/129 URLs do manifesto do acervo existem no repositório.
- [x] Contador de clippings do cabeçalho = nº de `.clip-card` renderizados.

## Portão 4 — Robustez técnica
- [x] JS sem erro de sintaxe (validado com `new Function`).
- [x] `<section>` e `.modal-overlay` balanceados.
- [x] Links externos com `target="_blank"` e `rel="noopener"`.

## Portão 5 — Entrega
- [x] `index.html` na raiz (página inicial do repo).
- [x] README com instruções de acesso e de ativação do GitHub Pages.
- [x] Workflow de deploy (`pages.yml`) presente.
- [ ] **GitHub Pages ativado nas Settings** — ação manual do mantenedor (fora do controle do código).

## Verificação manual recomendada
- [ ] Abrir o painel publicado e clicar em 3 documentos de cada categoria do acervo.
- [ ] Testar a busca global em 3 navegadores diferentes.
- [ ] Conferir a renderização em tela de celular (≤ 700px).
