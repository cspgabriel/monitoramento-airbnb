# Feature 001 — Tarefas

Legenda: ✅ concluída · ⬜ pendente

## Implementação

- ✅ T01 — Criar `index.html` na raiz como página inicial do repositório.
- ✅ T02 — Definir design system (tokens de cor, badges, cards, tabelas, timeline, modais).
- ✅ T03 — Aba **Visão Geral** com indicadores e 6 destaques.
- ✅ T04 — Aba **Federal**: 9 registros (Inquilinato, Lei Geral do Turismo, Lei 14.978/2024, PL 2.730/2019, PLC 1.809/2020, LC 182/2021, PL 4/2025, LC 214/2025, Decreto 12.955/2026).
- ✅ T05 — Aba **Municipal**: 8 registros (SP decreto, PL Diego, RJ, Floripa PL+memo, Petrópolis, Ubatuba, Fortaleza).
- ✅ T06 — Aba **STJ**: 3 acórdãos + teses consolidadas.
- ✅ T07 — Aba **Artigos & Análises**: 5 itens com link às fontes (material complementar).
- ✅ T08 — Aba **Todos os Registros**: tabela unificada e filtros por âmbito.
- ✅ T09 — Aba **Cronologia**: 15 marcos de 1991 a 2026.
- ✅ T10 — Aba **Clippings**: aviso editorial + cards categorizados + filtros (incl. novos clippings do material complementar: golpes, mortes/gás, lavagem, estudo de crime, Operação Litus).
- ✅ T11 — Aba **Acervo**: gerar manifesto dos 129 documentos e render agrupado por subpasta.
- ✅ T12 — Modais (20) com ementa, impacto e botões para documento do acervo / fonte oficial.
- ✅ T13 — **Busca global** indexando registros, artigos, clippings e acervo.
- ✅ T14 — Correções de CSS do protótipo (seletores `.summary-card.c-* .num` quebrados) e contador dinâmico de clippings.
- ✅ T15 — `README.md` na raiz + `.github/workflows/pages.yml` (deploy Pages).

## Validação

- ✅ T16 — Conferir que todos os caminhos de documento existem (9/9 modais + 129/129 acervo).
- ✅ T17 — Validar sintaxe do JS e o balanceamento de `<section>`/modais.

## Procedimento de manutenção (repetível)

### Regenerar o manifesto do acervo

Ao adicionar/remover arquivos em `legislacao-brasil/` ou `clippings/`, rode na raiz:

```bash
python3 - <<'PY'
import os, json, urllib.parse, re
roots = ["legislacao-brasil", "clippings", "arquivos ChatGPT/materiais-brutos-sharepoint"]
labels = {"legislacao-brasil":"Legislação","clippings":"Clipping","arquivos ChatGPT":"Material SharePoint"}
exts = (".pdf",".docx",".xlsx",".pptx")
items = []
for root in roots:
    for dp, dirs, files in os.walk(root):
        dirs.sort()
        for fn in sorted(files):
            if not fn.lower().endswith(exts): continue
            parts = os.path.join(dp, fn).split(os.sep)
            y = re.search(r"(19|20)\d{2}", "/".join(parts))
            items.append({
              "t": re.sub(r"\s+"," ", os.path.splitext(fn)[0].replace("_"," ")).strip(),
              "cat": labels.get(parts[0], parts[0]),
              "sub": " / ".join(parts[1:-1]),
              "ext": fn.split(".")[-1].upper(),
              "url": "/".join(urllib.parse.quote(p) for p in parts),
              "ano": y.group(0) if y else ""
            })
print("const ACERVO=[\n" + ",\n".join(json.dumps(i,ensure_ascii=False) for i in items) + "\n];")
PY
```

Substitua o bloco `const ACERVO=[…];` dentro do `<script>` em `index.html` pela saída.
Atualize também o número **129** no cabeçalho, na Visão Geral e no texto da aba Acervo.

### Adicionar um registro jurídico

1. Inserir a linha na tabela da aba (Federal/Municipal/STJ) e em "Todos os Registros".
2. Criar a `<div class="modal-overlay" id="modal-<slug>">` correspondente.
3. Se houver documento no repo, adicionar o botão `📄 Abrir documento` com o caminho relativo.
4. Atualizar contadores do cabeçalho e, se relevante, a Cronologia.
