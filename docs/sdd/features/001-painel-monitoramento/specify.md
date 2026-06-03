# Feature 001 — Painel de Monitoramento

**Estado:** ✅ Implementado (100%)
**Arquivo principal:** [`/index.html`](../../../../index.html)

## 1. Resumo

Painel web de arquivo único que consolida e torna navegável todo o material do repositório
sobre regulação do Airbnb/curta temporada no Brasil: normas federais e municipais,
jurisprudência do STJ, artigos, clippings e o acervo de 113 documentos.

## 2. Personas

- **Analista jurídico / regulatório** — acompanha a evolução de leis, PLs e decisões.
- **Setor hoteleiro / associações** — monitora risco competitivo e regulatório.
- **Anfitrião / investidor** — entende obrigações e tendências (tributárias, condominiais).
- **Pesquisador / jornalista** — busca fontes primárias e clippings organizados.

## 3. Histórias de usuário

- **US1** Como analista, quero **ver os destaques recentes** ao abrir o painel, para captar o cenário atual rapidamente.
- **US2** Como usuário, quero **navegar por abas** (Federal, Municipal, STJ, Artigos, Clippings, Acervo) para encontrar o que preciso.
- **US3** Como usuário, quero **buscar em tudo de uma vez** por um campo único no topo.
- **US4** Como usuário, quero **filtrar** registros por âmbito, status, município e categoria.
- **US5** Como usuário, quero **abrir uma ficha detalhada** de cada norma/decisão com ementa, impacto e link ao documento original.
- **US6** Como pesquisador, quero **acessar os 113 documentos** do acervo agrupados por categoria, com link direto.
- **US7** Como usuário, quero **ver a cronologia** (1991→2026) da regulação.
- **US8** Como usuário em celular, quero a interface **responsiva** e **imprimível**.

## 4. Requisitos funcionais

| ID | Requisito | Status |
|----|-----------|--------|
| RF1 | 9 abas: Visão Geral, Federal, Municipal, STJ, Artigos, Todos, Cronologia, Clippings, Acervo. | ✅ |
| RF2 | Registros federais (≥9), municipais (≥8), STJ (3) em tabelas filtráveis. | ✅ |
| RF3 | Modais detalhados com ementa, impacto, fundamentos e botões de documento/fonte. | ✅ |
| RF4 | Aba **Artigos & Análises** com 5 itens e link externo às fontes. | ✅ |
| RF5 | Aba **Clippings** com aviso editorial, categorias (habitação, crime, segurança, lavagem, condomínio, tributário, social) e filtros. | ✅ |
| RF6 | Aba **Acervo**: 113 documentos agrupados por subpasta, com link relativo e extensão. | ✅ |
| RF7 | **Busca global** que indexa registros, artigos, clippings e acervo. | ✅ |
| RF8 | **Cronologia** em linha do tempo com 15 marcos. | ✅ |
| RF9 | Contadores/estatísticas no cabeçalho (clippings contado dinamicamente). | ✅ |
| RF10 | Links de documento apontam para arquivos existentes no repositório. | ✅ |

## 5. Requisitos não-funcionais

| ID | Requisito | Status |
|----|-----------|--------|
| RNF1 | Arquivo único, zero dependências, sem build (P1). | ✅ |
| RNF2 | Funciona em `file://` e em GitHub Pages. | ✅ |
| RNF3 | Responsivo (mobile/desktop) e com regras de impressão. | ✅ |
| RNF4 | Navegação por teclado (ESC fecha modais/busca). | ✅ |
| RNF5 | Sem chamadas a terceiros / sem rastreadores (P4). | ✅ |
| RNF6 | Conteúdo em pt-BR, datado e com fonte (P5). | ✅ |

## 6. Critérios de aceite

- [x] Abrir `index.html` exibe a aba "Visão Geral" com indicadores e destaques.
- [x] Cada aba alterna sem recarregar a página e rola para o topo.
- [x] A busca global (≥2 caracteres) retorna resultados das 4 origens e abre o item.
- [x] Todos os botões "📄 Abrir documento" apontam para arquivos que **existem** no repo
      (validado: 9/9 referências de modal + 113/113 do acervo).
- [x] O contador de clippings do cabeçalho corresponde ao número de cards renderizados.
- [x] HTML estruturalmente balanceado e JS sem erro de sintaxe (validado).

## 7. Fora de escopo (vai para 002)

- Geração automatizada do manifesto do acervo (hoje é regenerado por script manual).
- Extração de texto/metadados dos PDFs para busca de conteúdo.
- Âmbito estadual e internacional como abas próprias (hoje há clippings por país).
- Testes automatizados e CI de validação de links.
