# Tarefas: [Nome da Feature]

**Feature ID:** `[NNN-slug]`  
**Spec:** `specs/[NNN-slug]/spec.md`  
**Plano:** `specs/[NNN-slug]/plan.md`  
**Status:** `Draft`

## Convenções

- `[ ]` pendente
- `[~]` em andamento
- `[x]` concluída
- `[!]` bloqueada
- Cada tarefa deve ser pequena, verificável e ligada a requisito, critério de aceite ou decisão técnica.

## Fase 0 - Preparação

- [ ] **T-001** Confirmar escopo da spec e remover dúvidas bloqueantes.
  - **Requisitos:** FR-001, FR-002
  - **Critério de conclusão:** spec marcada como `Ready for Plan` ou `Ready for Implementation`.

- [ ] **T-002** Configurar ambiente local e variáveis necessárias.
  - **Requisitos:** NFR-001
  - **Critério de conclusão:** ambiente executa comandos básicos sem credenciais versionadas.

## Fase 1 - Modelo e fundação

- [ ] **T-003** Criar ou atualizar modelo de dados.
  - **Requisitos:** [FR/NFR]
  - **Arquivos prováveis:** [arquivos]
  - **Critério de conclusão:** migrations/modelos definidos e testáveis.

- [ ] **T-004** Implementar camada base de configuração.
  - **Requisitos:** [FR/NFR]
  - **Arquivos prováveis:** [arquivos]
  - **Critério de conclusão:** configuração validada com defaults seguros.

## Fase 2 - Implementação funcional

- [ ] **T-005** Implementar [componente/fluxo principal].
  - **Requisitos:** [FR-001]
  - **Arquivos prováveis:** [arquivos]
  - **Critério de conclusão:** fluxo principal executa com entrada controlada.

- [ ] **T-006** Implementar [regra de negócio].
  - **Requisitos:** [FR-002, BR-001]
  - **Arquivos prováveis:** [arquivos]
  - **Critério de conclusão:** regra coberta por teste automatizado ou fixture.

## Fase 3 - Observabilidade e resiliência

- [ ] **T-007** Adicionar logs estruturados para execução e falhas.
  - **Requisitos:** NFR-002
  - **Critério de conclusão:** logs indicam início, fim, contagem processada e erros por tipo.

- [ ] **T-008** Adicionar timeout, retry e tratamento de falhas recuperáveis.
  - **Requisitos:** NFR-003
  - **Critério de conclusão:** falhas temporárias não quebram o fluxo sem registro.

## Fase 4 - Testes e validação

- [ ] **T-009** Criar testes unitários para regras críticas.
  - **Requisitos:** [FR/BR]
  - **Critério de conclusão:** testes cobrem casos felizes e casos de borda.

- [ ] **T-010** Criar teste de integração ou fixture para dependências externas.
  - **Requisitos:** [FR/NFR]
  - **Critério de conclusão:** validação não depende de serviço externo instável para rodar em CI/local.

- [ ] **T-011** Executar checklist de aceite da spec.
  - **Requisitos:** todos
  - **Critério de conclusão:** cada AC está validado ou explicitamente pendente.

## Fase 5 - Documentação e entrega

- [ ] **T-012** Atualizar documentação operacional.
  - **Requisitos:** NFR-002, NFR-003
  - **Critério de conclusão:** instruções de execução, configuração e troubleshooting documentadas.

- [ ] **T-013** Preparar PR ou commit final referenciando a spec.
  - **Requisitos:** todos
  - **Critério de conclusão:** PR/commit lista spec, plano, tarefas concluídas e validações executadas.

## Bloqueios

| ID | Tarefa | Bloqueio | Responsável | Próxima ação |
|---|---|---|---|---|
| B-001 | [T-XXX] | [Descrição] | [nome] | [ação] |

## Registro de validação

| Data | Comando/checagem | Resultado | Observações |
|---|---|---|---|
| [AAAA-MM-DD] | [comando] | [passou/falhou] | [observações] |
