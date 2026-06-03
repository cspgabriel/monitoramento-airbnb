# Constituição do Projeto

## Nome

Monitoramento Airbnb

## Propósito

Criar um sistema confiável para acompanhar informações públicas e/ou autorizadas de anúncios, preços, disponibilidade e mudanças relevantes relacionadas a imóveis monitorados, com foco em alertas úteis, histórico consultável e operação responsável.

## Princípios

### 1. Especificação antes de implementação

Toda feature relevante deve começar em `specs/NNN-slug/spec.md`, seguida por `plan.md` e `tasks.md`. Código sem especificação explícita deve ser exceção documentada.

### 2. Conformidade e uso responsável de dados

O projeto deve respeitar termos de uso, limites técnicos, privacidade, LGPD e boas práticas de acesso a fontes externas. Nenhuma implementação deve tentar burlar autenticação, paywalls, rate limits, captchas ou mecanismos antiabuso.

### 3. Observabilidade por padrão

Jobs, coletas, alertas e integrações devem registrar eventos suficientes para responder: o que rodou, quando rodou, qual foi o resultado, o que falhou e como reproduzir ou investigar.

### 4. Testabilidade e reprodutibilidade

Regras de negócio, parsers, cálculos de variação e critérios de disparo de alerta devem ter testes automatizados ou fixtures verificáveis. Fluxos dependentes de serviços externos devem usar mocks, contratos ou ambientes controlados.

### 5. Mudanças pequenas e rastreáveis

Cada tarefa deve gerar mudanças pequenas, revisáveis e ligadas a requisitos ou critérios de aceite. Pull requests devem referenciar a spec correspondente.

### 6. Segurança operacional

Credenciais, tokens, cookies, chaves de API e dados sensíveis nunca devem ser versionados. Configurações sensíveis devem usar variáveis de ambiente ou secret manager.

## Regras de qualidade

- Cada requisito funcional deve ter pelo menos um critério de aceite.
- Cada plano técnico deve declarar riscos e estratégia de validação.
- Cada tarefa deve ter um critério objetivo de conclusão.
- Jobs recorrentes devem definir política de retry, timeout, deduplicação e tratamento de falhas.
- Alertas devem evitar spam por meio de deduplicação, agrupamento ou janela mínima entre notificações equivalentes.

## Gate de revisão SDD

Antes da implementação, verifique:

- [ ] A spec descreve comportamento do usuário e regras de negócio sem depender de detalhes técnicos prematuros.
- [ ] O plano técnico cobre arquitetura, dados, integrações, segurança, observabilidade e testes.
- [ ] As tarefas são pequenas o suficiente para execução incremental.
- [ ] Há critérios de aceite claros para validar a entrega.

## Governança

Mudanças nesta constituição devem ser feitas em pull request específico ou commit explícito, explicando o motivo da alteração e o impacto esperado nos próximos planos.
