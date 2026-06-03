# Plano Técnico: [Nome da Feature]

**Feature ID:** `[NNN-slug]`  
**Spec:** `specs/[NNN-slug]/spec.md`  
**Status:** `Draft`  
**Criado em:** `[AAAA-MM-DD]`  
**Responsável:** `[nome]`

## Resumo da abordagem

Descreva a solução técnica em 3-6 frases, conectando as decisões aos requisitos da especificação.

## Contexto técnico

- **Stack atual:** [linguagem, framework, banco, fila, scheduler]
- **Ambiente alvo:** [local, servidor, cloud, container]
- **Dependências relevantes:** [serviços, APIs, bibliotecas]
- **Restrições conhecidas:** [limites técnicos, políticas externas, custo, compliance]

## Mapeamento requisito -> solução

| Requisito | Estratégia técnica | Componentes impactados | Validação |
|---|---|---|---|
| FR-001 | [Como será implementado] | [arquivos/módulos] | [teste/checagem] |
| NFR-001 | [Como será atendido] | [arquivos/módulos] | [teste/checagem] |

## Arquitetura proposta

```text
[Entrada/Fonte]
      |
      v
[Coleta/Integração] -> [Normalização] -> [Persistência]
                                      -> [Regras/Comparação]
                                      -> [Alertas/Relatórios]
```

### Componentes

| Componente | Responsabilidade | Observações |
|---|---|---|
| [Componente] | [Responsabilidade] | [Observações] |

## Modelo de dados

| Tabela/coleção/arquivo | Campos | Índices/chaves | Observações |
|---|---|---|---|
| [Nome] | [Campos] | [Índices] | [Observações] |

## Fluxos principais

### Fluxo 1 - [Nome]

1. [Passo técnico]
2. [Passo técnico]
3. [Resultado]

### Fluxo 2 - [Nome]

1. [Passo técnico]
2. [Passo técnico]
3. [Resultado]

## Integrações externas

| Integração | Uso | Autenticação | Limites | Estratégia de falha |
|---|---|---|---|---|
| [Serviço] | [Uso] | [Auth] | [Rate limit] | [Retry/fallback] |

## Segurança, privacidade e conformidade

- Como secrets serão armazenados?
- Quais dados sensíveis existem?
- Quais dados não devem ser persistidos?
- Quais políticas externas precisam ser respeitadas?
- Como evitar uso abusivo de fontes externas?

## Observabilidade

### Logs

- Evento de início/fim de job.
- Quantidade de itens processados.
- Falhas por tipo.
- Identificador de execução/correlação.

### Métricas

- [Métrica operacional]
- [Métrica de qualidade]
- [Métrica de negócio]

### Alertas operacionais

- [Condição de alerta]
- [Canal de notificação]
- [Responsável]

## Estratégia de testes

| Tipo | Cobertura esperada | Ferramenta/abordagem |
|---|---|---|
| Unitário | [Regras/parsers/cálculos] | [ferramenta] |
| Integração | [Banco/API/fila] | [ferramenta] |
| Contrato/fixture | [Fonte externa] | [fixture/mock] |
| E2E/manual | [Fluxo principal] | [roteiro] |

## Rollout

1. [Passo incremental]
2. [Validação]
3. [Ativação]
4. [Plano de rollback]

## Riscos técnicos

| ID | Risco | Impacto | Mitigação |
|---|---|---|---|
| R-001 | [Risco] | [Impacto] | [Mitigação] |

## Decisões técnicas

### ADR-001 - [Título]

- **Contexto:** [Por que a decisão é necessária]
- **Decisão:** [O que foi decidido]
- **Consequências:** [Trade-offs]

## Checklist de prontidão para tarefas

- [ ] Cada requisito da spec tem uma estratégia técnica.
- [ ] Modelo de dados está definido.
- [ ] Testes e validações estão claros.
- [ ] Riscos e mitigação foram documentados.
- [ ] Segurança, observabilidade e rollout foram considerados.
