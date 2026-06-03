# Feature 002 — Próximas Etapas (roadmap para "ficar completo")

**Estado:** 📝 Especificado (20%)

## 1. Objetivo

Evoluir o painel de um protótipo curado para uma ferramenta de monitoramento sustentável,
reduzindo trabalho manual, ampliando a cobertura e garantindo qualidade contínua — sem violar
a constituição (especialmente P1: simplicidade e zero dependências em runtime).

## 2. Épicos e histórias

### E1 — Acervo orientado a dados
- **US** Como mantenedor, quero que o **manifesto do acervo seja gerado automaticamente** para
  não editar HTML manualmente a cada novo PDF.
- **US** Como usuário, quero **buscar por categoria/país/ano** no acervo com filtros mais ricos.

### E2 — Busca de conteúdo (não só títulos)
- **US** Como pesquisador, quero buscar **dentro do texto** dos documentos (PDFs), não apenas
  pelos títulos, para encontrar dispositivos e termos específicos.

### E3 — Cobertura regulatória ampliada
- **US** Como analista, quero **abas/filtros para âmbito estadual e internacional** com fichas
  próprias, e mais municípios (Salvador, Curitiba, Olímpia, Ponta Grossa…).
- **US** Como analista, quero ver os **PLs do material complementar** (Salvino, Flávio Valle,
  minutas) como registros com ficha e link ao documento.

### E4 — Qualidade contínua
- **US** Como mantenedor, quero **CI que valide links** (documentos do acervo e modais) a cada PR.
- **US** Como mantenedor, quero **testes de fumaça** do JS (abas, busca, render do acervo).

### E5 — Experiência e dados abertos
- **US** Como usuário, quero **deep-link por aba** (`#federal`) e por ficha para compartilhar.
- **US** Como integrador, quero um **`data/registros.json`** público com todos os registros.
- **US** Como usuário, quero **exportar** a visão atual (CSV/impressão/PDF) e ver **mapa/§gráficos**
  simples de distribuição por âmbito/ano.

## 3. Requisitos (priorizados)

| ID | Requisito | Prioridade |
|----|-----------|------------|
| RF-202.1 | Script versionado (`scripts/gerar-acervo.py`) que gera o manifesto e/ou um `data/acervo.json`. | Alta |
| RF-202.2 | Filtros do acervo por categoria, país e ano. | Média |
| RF-202.3 | Registros jurídicos migrados para `data/registros.json` e renderizados por JS. | Média |
| RF-202.4 | Deep-linking por aba via `location.hash`. | Alta |
| RF-202.5 | CI (GitHub Actions) validando existência dos arquivos referenciados. | Alta |
| RF-202.6 | Indexação de texto dos PDFs para busca de conteúdo (índice estático). | Baixa |
| RF-202.7 | Abas/filtros para âmbito estadual e internacional + novos municípios/PLs. | Média |
| RF-202.8 | Exportação CSV e gráficos simples (sem dependexterna pesada, ou lib leve via CDN opcional). | Baixa |

## 4. Critérios de aceite (do épico mínimo viável)

- [ ] `python3 scripts/gerar-acervo.py` regenera o manifesto de forma idempotente.
- [ ] Abrir `index.html#stj` ativa diretamente a aba de jurisprudência.
- [ ] Um PR que referencie um arquivo inexistente **falha** no CI.
- [ ] Os PLs do material complementar aparecem como registros com link ao documento.

## 5. Restrições

- Manter P1: se a busca de conteúdo exigir índice pesado, gerá-lo **em build** e servir
  estático — nunca processar PDF no navegador em runtime.
- Acessibilidade e funcionamento offline não podem regredir.
