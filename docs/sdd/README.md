# Spec-Driven Development (SDD) — Monitoramento Airbnb

Esta pasta contém a **especificação executável** do projeto, seguindo a metodologia
*Spec-Driven Development* (referência: [SpillwaveSolutions/sdd-skill](https://github.com/SpillwaveSolutions/sdd-skill)),
adaptada para um projeto **brownfield** (já existente) e em português.

Na SDD a especificação é o artefato central: a partir dela derivam o plano técnico, as
tarefas e os critérios de qualidade. O código deve sempre refletir o que está aqui descrito.

## Estrutura

```
docs/sdd/
├── constitution.md        # Princípios e decisões arquiteturais do projeto
└── features/
    ├── 001-painel-monitoramento/   # Painel atual (HTML único + acervo)
    │   ├── specify.md      # O QUÊ: requisitos, histórias e critérios de aceite
    │   ├── plan.md         # COMO: arquitetura e decisões técnicas
    │   ├── tasks.md        # Tarefas granulares (com status)
    │   └── checklist.md    # Portões de qualidade / validação
    └── 002-proximas-etapas/        # Roadmap "para ficar completo"
        ├── specify.md
        ├── plan.md
        ├── tasks.md
        └── checklist.md
```

## Fluxo (brownfield — 7 passos)

1. **Analisar o código existente** → feito (painel HTML + acervo de 113 documentos).
2. **Inicializar a estrutura SDD** → esta pasta.
3. **Gerar a constituição a partir do código** → [`constitution.md`](constitution.md).
4. **Escolher estratégia de integração** → evolução incremental, sem reescrita.
5. **Documentar funcionalidades existentes** → feature `001`.
6. **Especificar novas funcionalidades** → feature `002`.
7. **Planejar pontos de integração** → `002/plan.md`.

## Rastreamento de funcionalidades

| ID  | Funcionalidade | Estado | Progresso |
|-----|----------------|--------|-----------|
| 001 | Painel de monitoramento (HTML único + acervo) | ✅ Implementado | 100% |
| 002 | Próximas etapas (dados, automação, novos âmbitos) | 📝 Especificado | 20% |

Estados: Especificado (20%) · Planejado (40%) · Tarefas definidas (60%) · Em progresso (80%) · Completo (100%).
