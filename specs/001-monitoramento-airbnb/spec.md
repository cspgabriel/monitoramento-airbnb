# Especificação: Monitoramento Airbnb

**Feature ID:** `001-monitoramento-airbnb`  
**Status:** `Ready for Plan`  
**Criado em:** `2026-06-03`  
**Responsável:** `cspgabriel`

## Resumo

Criar a base funcional de um sistema para monitorar anúncios, preços, disponibilidade e mudanças relevantes relacionadas a imóveis acompanhados. O sistema deve manter histórico consultável, identificar variações importantes e preparar notificações úteis sem depender de coleta abusiva, credenciais expostas ou comportamento que burle mecanismos de plataformas externas.

## Contexto e problema

Usuários que acompanham imóveis ou mercados específicos precisam saber quando preço, disponibilidade, título, avaliação, localização aproximada ou outros atributos mudam. Fazer isso manualmente é repetitivo, sujeito a esquecimento e não cria histórico estruturado.

O projeto deve oferecer uma base confiável para registrar imóveis monitorados, executar coletas autorizadas ou baseadas em fontes permitidas, comparar snapshots e gerar eventos de mudança.

## Objetivos

- [ ] Permitir cadastro de anúncios ou imóveis monitorados.
- [ ] Registrar snapshots históricos de dados relevantes.
- [ ] Detectar mudanças de preço, disponibilidade e atributos importantes.
- [ ] Gerar eventos de alteração deduplicados.
- [ ] Preparar a base para alertas e relatórios futuros.

## Fora de escopo

- Burlar autenticação, captchas, rate limits, paywalls ou mecanismos antiabuso.
- Automatizar ações em contas de terceiros sem autorização.
- Persistir credenciais, cookies ou tokens em arquivos versionados.
- Garantir cobertura de 100% dos anúncios ou disponibilidade em tempo real.
- Enviar notificações por múltiplos canais nesta primeira entrega, exceto se já existir integração pronta no projeto.

## Usuários e cenários

### Persona principal

- **Quem:** pessoa que acompanha anúncios de imóveis de curta temporada, preços ou disponibilidade.
- **Necessidade:** saber quando há mudanças relevantes sem verificar manualmente todos os anúncios.
- **Resultado esperado:** histórico claro e eventos de mudança confiáveis.

### Jornada principal

1. O usuário cadastra um anúncio ou imóvel para monitoramento.
2. O sistema executa uma rotina de coleta autorizada ou importação de dados.
3. O sistema normaliza os dados coletados em um snapshot.
4. O sistema compara o snapshot novo com o snapshot anterior.
5. O sistema registra mudanças relevantes e evita eventos duplicados.
6. O usuário consulta histórico, status da última coleta e mudanças detectadas.

## Requisitos funcionais

### FR-001 - Cadastro de item monitorado

O sistema deve permitir registrar um item monitorado com identificador externo, URL ou referência equivalente, nome amigável, status e metadados mínimos.

**Critérios de aceite:**

- **AC-001:** Dado um novo item válido, quando ele for cadastrado, então o sistema deve persistir o item com status ativo.
- **AC-002:** Dado um item já cadastrado com o mesmo identificador externo ou URL normalizada, quando houver nova tentativa de cadastro, então o sistema deve evitar duplicidade.
- **AC-003:** Dado um item inativo, quando a coleta recorrente executar, então ele não deve ser processado por padrão.

### FR-002 - Registro de snapshots

O sistema deve registrar snapshots históricos com os dados coletados ou importados para cada item monitorado.

**Critérios de aceite:**

- **AC-004:** Dado um item ativo, quando uma coleta válida retornar dados, então o sistema deve criar um snapshot associado ao item.
- **AC-005:** Dado um snapshot com campos ausentes, quando ele for persistido, então o sistema deve manter informação suficiente para distinguir campo ausente de campo com valor zero ou falso.
- **AC-006:** Dado erro de coleta, quando nenhum dado confiável estiver disponível, então o sistema não deve criar snapshot falso e deve registrar a falha operacional.

### FR-003 - Detecção de mudanças

O sistema deve comparar o snapshot mais recente com o snapshot anterior e registrar eventos de mudança relevantes.

**Critérios de aceite:**

- **AC-007:** Dado que o preço mudou entre dois snapshots, quando a comparação executar, então deve ser criado um evento de mudança de preço com valor anterior, valor novo e variação.
- **AC-008:** Dado que a disponibilidade mudou, quando a comparação executar, então deve ser criado um evento de disponibilidade.
- **AC-009:** Dado que não houve mudança relevante, quando a comparação executar, então nenhum evento novo deve ser criado.
- **AC-010:** Dado que a mesma mudança já foi registrada, quando a comparação executar novamente, então o sistema deve evitar duplicidade.

### FR-004 - Consulta de histórico

O sistema deve permitir consultar o histórico de snapshots e eventos de mudança por item monitorado.

**Critérios de aceite:**

- **AC-011:** Dado um item monitorado, quando o histórico for solicitado, então o sistema deve retornar snapshots ordenados por data de coleta.
- **AC-012:** Dado um item monitorado, quando eventos forem solicitados, então o sistema deve retornar eventos ordenados do mais recente para o mais antigo.
- **AC-013:** Dado um item inexistente, quando o histórico for solicitado, então o sistema deve retornar erro claro ou resposta vazia documentada.

### FR-005 - Status operacional da coleta

O sistema deve registrar o resultado de cada execução de coleta ou importação.

**Critérios de aceite:**

- **AC-014:** Dado uma execução bem-sucedida, quando ela terminar, então devem ser registrados horário de início, horário de fim, quantidade de itens processados e quantidade de mudanças detectadas.
- **AC-015:** Dado uma execução com falha parcial, quando ela terminar, então o sistema deve registrar quais itens falharam e o motivo resumido.
- **AC-016:** Dado uma falha recuperável, quando houver retry configurado, então o sistema deve registrar tentativas e resultado final.

## Requisitos não funcionais

### NFR-001 - Conformidade e uso responsável

O sistema deve respeitar termos de uso, limites técnicos, privacidade, LGPD e políticas das fontes de dados utilizadas. Qualquer integração externa deve documentar fonte, permissão, limite e estratégia de uso.

### NFR-002 - Segurança de credenciais

Credenciais, tokens, cookies e chaves de API não devem ser versionados. O sistema deve usar variáveis de ambiente, secrets do ambiente de execução ou mecanismo equivalente.

### NFR-003 - Observabilidade

Rotinas recorrentes devem emitir logs com identificador da execução, item processado, resultado, tempo gasto e erro resumido quando houver falha.

### NFR-004 - Testabilidade

Comparações, normalização de dados e geração de eventos devem ser cobertas por testes unitários ou fixtures verificáveis.

### NFR-005 - Resiliência

Falhas em um item monitorado não devem interromper necessariamente o processamento dos demais itens. O sistema deve ter timeout, tratamento de exceções e política de retry para falhas transitórias.

## Dados e entidades

| Entidade | Descrição | Campos principais | Observações |
|---|---|---|---|
| MonitoredItem | Item/anúncio acompanhado | id, external_id, url, display_name, status, created_at, updated_at | URL deve ser normalizada quando aplicável. |
| Snapshot | Registro histórico dos dados observados | id, monitored_item_id, collected_at, price, availability, rating, title, raw_data_hash | `raw_data` completo só deve ser salvo se não contiver dado sensível. |
| ChangeEvent | Mudança relevante detectada | id, monitored_item_id, snapshot_id, event_type, previous_value, current_value, delta, created_at, dedupe_key | `dedupe_key` evita eventos repetidos. |
| CollectionRun | Execução de coleta/importação | id, started_at, finished_at, status, processed_count, failed_count, change_count | Ajuda auditoria e troubleshooting. |

## Regras de negócio

- **BR-001:** Um item monitorado ativo pode ter vários snapshots ao longo do tempo.
- **BR-002:** Eventos de mudança devem ser derivados da comparação entre snapshots consecutivos confiáveis.
- **BR-003:** Mudanças duplicadas não devem gerar eventos duplicados.
- **BR-004:** Falhas de coleta devem ser registradas, mas não devem criar snapshots com dados inventados.
- **BR-005:** Preços devem preservar moeda quando disponível.
- **BR-006:** Campos opcionais devem diferenciar valor ausente de valor vazio ou zero.

## Casos de borda

- Fonte externa indisponível temporariamente.
- Item removido, expirado ou indisponível.
- Preço ausente em uma coleta e presente em outra.
- Moeda diferente entre snapshots.
- Mudança de URL canônica do anúncio.
- Dados parcialmente coletados.
- Execução interrompida antes de processar todos os itens.
- Mesma coleta executada duas vezes em sequência.

## Dependências

- Fonte de dados permitida ou autorizada.
- Banco de dados ou armazenamento persistente.
- Scheduler, cron, fila ou comando manual para execução recorrente.
- Sistema de logs.
- Futuras integrações de notificação, como e-mail, Telegram, WhatsApp ou Slack, se forem adicionadas posteriormente.

## Riscos e dúvidas abertas

| ID | Tipo | Descrição | Dono | Status |
|---|---|---|---|---|
| Q-001 | Dúvida | Qual fonte de dados será usada de forma autorizada e sustentável? | cspgabriel | Aberta |
| Q-002 | Dúvida | Qual banco ou formato de persistência o projeto já usa? | cspgabriel | Aberta |
| Q-003 | Dúvida | Qual canal de alerta será priorizado no futuro? | cspgabriel | Aberta |
| R-001 | Risco | Mudanças no formato da fonte externa podem quebrar parsers. | cspgabriel | Aberto |
| R-002 | Risco | Coletas frequentes podem gerar bloqueio ou comportamento indesejado. | cspgabriel | Aberto |
| R-003 | Risco | Alertas sem deduplicação podem gerar spam. | cspgabriel | Aberto |

## Métricas de sucesso

- Percentual de execuções concluídas sem falha crítica.
- Quantidade de itens processados por execução.
- Quantidade de snapshots válidos criados.
- Quantidade de mudanças detectadas e deduplicadas.
- Tempo médio de execução por item.

## Checklist de prontidão para plano

- [x] Problema e objetivo estão claros.
- [x] Requisitos funcionais têm critérios de aceite.
- [x] Fora de escopo está declarado.
- [x] Riscos e dúvidas abertas estão listados.
- [x] Requisitos de segurança, dados e observabilidade foram considerados.
