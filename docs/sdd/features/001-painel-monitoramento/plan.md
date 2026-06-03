# Feature 001 — Plano Técnico

## 1. Arquitetura

Aplicação **estática de arquivo único**. Não há servidor, banco ou API. O navegador carrega
`index.html`, que contém três camadas:

```
index.html
├── <style>      CSS embutido (design tokens em :root, componentes, responsivo, print)
├── <body>       Markup semântico
│   ├── header   título, estatísticas e BUSCA GLOBAL
│   ├── tabs      navegação entre 9 <section>
│   ├── sections  conteúdo de cada aba (tabelas, cards, timeline, acervo)
│   ├── modals    20 fichas detalhadas (.modal-overlay)
│   └── footer
└── <script>     JS vanilla
    ├── const ACERVO = [...129 itens...]   (manifesto embutido — decisão A3)
    ├── navegação de abas e modais
    ├── filtros (tabela/cards/clippings/município/âmbito)
    ├── renderAcervo()    agrupa o ACERVO por subpasta e injeta HTML
    └── globalSearch()    índice em memória (registros+artigos+clippings+acervo)
```

## 2. Decisões técnicas

| Decisão | Alternativa descartada | Motivo |
|---------|------------------------|--------|
| Manifesto `ACERVO` embutido | `fetch('acervo.json')` | `fetch` falha em `file://`; embutir mantém portabilidade (P1/RNF2). |
| Registros jurídicos em HTML estático | Render a partir de JSON | Volume baixo e conteúdo curado; HTML é mais legível para revisão jurídica. |
| Índice de busca construído sob demanda | Índice pré-computado | Simplicidade; o DOM já é a fonte; custo desprezível para este volume. |
| Links relativos URL-encoded | Links absolutos para o GitHub | Funciona local e no Pages sem reescrever caminhos. |
| Deploy por GitHub Actions | Branch `gh-pages` manual | Automático a cada push; publica raiz com os PDFs. |

## 3. Modelo de dados (manifesto do acervo)

Cada item de `ACERVO`:

```js
{
  t:   "Título legível (derivado do nome do arquivo)",
  cat: "Legislação" | "Clipping",          // pasta de topo
  sub: "federal" | "regulacao-por-pais / Italia" | ...,  // caminho de subpastas
  ext: "PDF" | "DOCX",
  url: "caminho/relativo/encodado.pdf",
  ano: "2025"                               // ano inferido do caminho (pode ser "")
}
```

Gerado por script Python que percorre `legislacao-brasil/` e `clippings/` (ver `tasks.md`).

## 4. Convenções de UI

- **Cores por âmbito:** Federal `#0066CC`, Municipal `#00766C`, STJ `#C62828`, Artigo `#4527A0`.
- **Badges** padronizadas por tipo (lei/PL/decreto/LC/acórdão…), âmbito e status.
- **Modais:** `id="modal-<slug>"`, abertos via `openModal('<slug>')`.
- **Acessibilidade:** foco gerenciado por overlay; ESC fecha; `rel="noopener"` em links externos.

## 5. Compatibilidade

Navegadores *evergreen* (Chrome, Edge, Firefox, Safari). Usa apenas APIs amplamente
suportadas (CSS Grid, `classList`, `querySelectorAll`, template strings). Sem polyfills.

## 6. Pontos de integração

- **Filesystem do repo** → links do acervo e dos botões de documento (caminhos relativos).
- **Fontes externas** → links para Planalto, STJ e veículos de imprensa (abrem em nova aba).
- **GitHub Pages** → `.github/workflows/pages.yml` publica a raiz.
