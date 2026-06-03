# SDD - Spec-Driven Development

Este repositório passa a usar um fluxo de **Spec-Driven Development (SDD)**: a especificação é o artefato primário; código, testes e documentação devem derivar dela.

## Objetivo

Reduzir retrabalho e decisões implícitas ao transformar cada mudança relevante em um conjunto rastreável de artefatos:

1. Constituição do projeto: princípios e regras que guiam decisões.
2. Especificação funcional: o que será entregue e por quê.
3. Plano técnico: como a solução será implementada com a arquitetura escolhida.
4. Lista de tarefas: execução incremental, testável e revisável.
5. Validação: testes, critérios de aceite e análise de consistência entre artefatos.

## Estrutura criada

```text
.specify/
  memory/
    constitution.md
  templates/
    spec-template.md
    plan-template.md
    tasks-template.md
specs/
  001-monitoramento-airbnb/
    spec.md
    plan.md
    tasks.md
.github/
  ISSUE_TEMPLATE/
    sdd-feature.yml
```

## Fluxo recomendado

### 1. Criar ou atualizar a constituição

Antes de qualquer feature, revise `.specify/memory/constitution.md` para garantir que segurança, qualidade, observabilidade e limites do produto estejam claros.

### 2. Criar a especificação

Crie uma pasta em `specs/NNN-nome-da-feature/` e copie `.specify/templates/spec-template.md` para `spec.md`.

A especificação deve focar no comportamento esperado, usuários, regras de negócio, critérios de aceite, casos de borda e requisitos não funcionais. Evite decisões técnicas prematuras nesta etapa.

### 3. Criar o plano técnico

Copie `.specify/templates/plan-template.md` para `plan.md` dentro da mesma pasta da feature.

O plano deve mapear a especificação para arquitetura, dados, integrações, riscos, testes e rollout. Decisões relevantes devem ser registradas como ADRs curtos no próprio plano ou em `docs/adr/`.

### 4. Quebrar em tarefas

Copie `.specify/templates/tasks-template.md` para `tasks.md` e transforme o plano em tarefas pequenas, ordenadas e verificáveis.

Cada tarefa deve ter:

- identificador único;
- dependências, quando houver;
- arquivos prováveis a alterar;
- critério objetivo de conclusão;
- teste ou validação associada.

### 5. Implementar e validar

Uma mudança só deve ser considerada pronta quando:

- os critérios de aceite da spec estiverem cobertos;
- os testes relevantes estiverem passando;
- logs/observabilidade forem suficientes para diagnosticar falhas;
- limites de uso de integrações externas forem respeitados;
- a documentação operacional estiver atualizada quando necessário.

## Convenções

- Nome de pasta de feature: `specs/NNN-slug-curto/`, exemplo: `specs/002-alertas-preco/`.
- Status de artefato: `Draft`, `Ready for Plan`, `Ready for Implementation`, `Implemented`, `Deprecated`.
- IDs de requisitos: `FR-001`, `NFR-001`, `AC-001`, `T-001`.
- Branch sugerida: `NNN-slug-curto`.

## Uso com agentes de IA

Ao pedir implementação para um agente, aponte sempre para:

1. `.specify/memory/constitution.md`
2. `specs/NNN-slug/spec.md`
3. `specs/NNN-slug/plan.md`
4. `specs/NNN-slug/tasks.md`

Peça para o agente executar somente tarefas marcadas como pendentes e atualizar o `tasks.md` conforme concluir cada item.
