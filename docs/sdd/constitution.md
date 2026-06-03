# Constituição do Projeto — Monitoramento Airbnb

> A constituição reúne os princípios inegociáveis e as decisões arquiteturais que regem o
> projeto. Toda especificação, plano e tarefa deve ser compatível com este documento.
> Mudanças aqui exigem justificativa explícita no histórico do repositório.

## 1. Missão

Oferecer um **painel público, confiável e navegável** que consolide a legislação, a
jurisprudência, os projetos de lei, as análises e os clippings de imprensa relacionados ao
**Airbnb e ao aluguel de curta temporada no Brasil**, apoiando o monitoramento de risco
regulatório, jurídico e reputacional — com finalidade acadêmica e informativa.

## 2. Princípios

### P1 — Simplicidade radical (zero dependências)
O painel é entregue como **arquivo único `index.html`** (HTML + CSS + JS *vanilla*), sem
build, sem framework e sem dependências externas em runtime. Qualquer pessoa deve conseguir
abrir o arquivo e ter o sistema funcionando. Bibliotecas só entram se um requisito não puder
ser atendido de outra forma — e a decisão deve ser registrada em um `plan.md`.

### P2 — O repositório é a fonte da verdade
Os documentos originais (PDF/DOCX) versionados no repositório são a base factual. O painel
**referencia** esses arquivos por caminho relativo; nunca os substitui nem os reescreve.
Links para fontes oficiais externas (Planalto, STJ, imprensa) complementam, não substituem.

### P3 — Rigor e honestidade editorial
- Separar **fato jurídico** de **opinião/clipping**.
- Marcar explicitamente itens **não confirmados** (ex.: "validar fonte").
- Exibir contrapontos quando uma fonte for controversa.
- Nenhum clipping imputa culpa; serve a monitoramento. O aviso editorial é obrigatório.

### P4 — Acessível e durável
Funciona offline (via `file://`) e online (GitHub Pages). Responsivo (mobile → desktop),
navegável por teclado (ESC fecha modais), imprimível, e com HTML semântico. Sem
rastreadores nem chamadas a terceiros.

### P5 — Conteúdo em português, neutro e datado
A língua do produto é o português do Brasil. Todo registro tem data/ano e fonte. O painel
exibe a data da última atualização.

### P6 — Manutenção previsível
Adicionar um registro ou documento deve seguir um caminho documentado e repetível
(ver `tasks.md`). Dados estruturados (ex.: manifesto do acervo) são preferíveis a HTML
duplicado sempre que reduzirem o custo de manutenção.

## 3. Decisões arquiteturais

| # | Decisão | Justificativa |
|---|---------|---------------|
| A1 | Single-file `index.html` na raiz | Página inicial do repo; deploy trivial no Pages; portátil. |
| A2 | CSS e JS embutidos, *vanilla* | Cumpre P1; sem etapa de build. |
| A3 | Acervo via manifesto JS embutido (`const ACERVO`) | Lista os 113 arquivos sem `fetch` (funciona em `file://`). |
| A4 | Registros jurídicos em HTML estático + modais | Conteúdo curado, rico e estável; baixo volume. |
| A5 | Links de documento por caminho relativo URL-encoded | Servível tanto local quanto no Pages. |
| A6 | Deploy via GitHub Actions (`pages.yml`) | Publicação automática a cada push em `main`. |
| A7 | Especificação versionada em `docs/sdd/` | Visível no GitHub; espelha o sdd-skill (`.speckit/`). |

## 4. Restrições

- **Sem backend**: tudo é estático. Não há banco de dados nem API própria.
- **Sem segredos**: nada de chaves/credenciais no repositório.
- **Tamanho**: manter o `index.html` em ordem de centenas de KB; mídia pesada fica nos PDFs.
- **Privacidade**: não coletar dados de visitantes.

## 5. Definição de "completo" (para o produto)

O sistema é considerado completo quando: (a) todo o material do repositório está refletido
ou referenciado no painel; (b) cada registro relevante tem ficha e link ao documento/fonte;
(c) há especificação SDD versionada; (d) o deploy público funciona; (e) existe um processo
documentado de atualização. O caminho para os itens ainda abertos vive na feature `002`.
