# 🏠 Monitoramento Airbnb — Legislação, Jurisprudência e Acervo (Brasil)

Painel e acervo documental para **monitorar a regulação do Airbnb e do aluguel de curta
temporada no Brasil**: legislação federal e municipal, projetos de lei, jurisprudência do
STJ, artigos/análises e clippings de imprensa (nacionais e internacionais).

> **Página inicial do projeto:** [`index.html`](index.html) — um painel interativo de
> arquivo único (HTML/CSS/JS, sem dependências) que organiza todo o material do repositório.

## 🌐 Acessar o painel

- **GitHub Pages:** uma vez ativado (ver abaixo), o painel fica em
  `https://cspgabriel.github.io/monitoramento-airbnb/`
- **Localmente:** abra o arquivo `index.html` no navegador (ou rode `python3 -m http.server`
  na raiz e acesse `http://localhost:8000`). Servir por HTTP é recomendado para que os
  links do **Acervo** abram os PDFs/DOCX corretamente.

### Ativar o GitHub Pages

O site já está pronto para publicação. Para ligar:

1. **Settings → Pages** do repositório.
2. Em **Build and deployment → Source**, escolha **GitHub Actions** (já existe o workflow
   [`.github/workflows/pages.yml`](.github/workflows/pages.yml)), **ou** escolha
   **Deploy from a branch** apontando para `main` / pasta `/ (root)`.
3. Aguarde o deploy. O `index.html` da raiz é servido como página inicial.

## ✨ O que o painel oferece

| Aba | Conteúdo |
|-----|----------|
| **Visão Geral** | Indicadores e destaques recentes (STJ 2026, Reforma Tributária, etc.). |
| **Federal** | Leis, LCs, decretos e PLs federais (Inquilinato, Lei Geral do Turismo, LC 214/2025…). |
| **Municipal** | Normas de São Paulo, Rio, Florianópolis, Petrópolis, Ubatuba, Fortaleza… |
| **Jurisprudência STJ** | Acórdãos e teses (2021 → paradigma de 2026, quórum de 2/3). |
| **Artigos & Análises** | Análises regulatórias e posicionamentos com links às fontes. |
| **Todos os Registros** | Tabela unificada e filtrável de tudo. |
| **Cronologia** | Linha do tempo de 1991 a 2026. |
| **🔴 Clippings** | Notícias/estudos negativos (fraude, segurança, lavagem, habitação, impacto social). |
| **📁 Acervo** | Navegador dos **113 documentos** (PDF/DOCX) do repositório, com link direto. |

Recursos: **busca global** no topo (varre todas as abas e o acervo), filtros por
âmbito/status/categoria, fichas detalhadas (modais) com link para o documento original e
para a fonte oficial, layout responsivo e modo impressão.

## 📂 Estrutura do repositório

```
.
├── index.html                         # 👉 Painel (página inicial)
├── README.md
├── .github/workflows/pages.yml        # Deploy automático no GitHub Pages
├── docs/sdd/                          # Especificação (Spec-Driven Development)
│   ├── constitution.md
│   └── features/001-painel-monitoramento/
│       ├── specify.md · plan.md · tasks.md · checklist.md
├── legislacao-brasil/                 # Legislação, decisões, PLs e análises
│   ├── federal/  municipios/  decisoes-judiciais/  projetos-de-lei/  analises/
├── clippings/                         # Clippings de imprensa
│   ├── geral-2024/  geral-2025/  problemas-recentes/  regulacao-por-pais/
└── material-complementar-criado-pelo-chatgpt/   # Material editorial de apoio
```

## 🛠️ Manutenção

- **Acervo:** os 113 itens da aba 📁 Acervo são listados a partir de um manifesto embutido no
  `index.html` (constante `ACERVO`). Ao adicionar/remover arquivos em `legislacao-brasil/` ou
  `clippings/`, regenere o manifesto (ver [`docs/sdd/.../tasks.md`](docs/sdd/features/001-painel-monitoramento/tasks.md)).
- **Registros jurídicos:** edite as tabelas/cards e as modais correspondentes no `index.html`.

## ⚠️ Aviso

Material de uso **acadêmico e informativo**, voltado a monitoramento de risco regulatório.
A inclusão de um clipping não imputa culpa a nenhuma parte. Confira sempre a redação vigente
nas fontes oficiais (Planalto, Diário Oficial, STJ, portais legislativos) e consulte um
advogado para orientação jurídica específica.
