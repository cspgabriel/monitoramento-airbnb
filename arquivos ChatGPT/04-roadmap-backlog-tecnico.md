# 04 — Roadmap e backlog técnico

Data: 03/06/2026.

Este arquivo transforma a pesquisa e a especificação da plataforma em um backlog prático para desenvolvimento.

---

## 1. Roadmap por fases

### Fase 1 — Fundação do produto

Objetivo: criar a base para cadastro, regras, fontes oficiais e alertas.

Entregas:

- Cadastro de imóveis.
- Cadastro de anúncios.
- Cadastro de condomínios.
- Cadastro de fontes oficiais.
- Motor inicial de regras.
- Alertas P0/P1.
- Dashboard de risco por imóvel.
- Evidence Vault simples.

Critério de sucesso:

- Um imóvel pode ser cadastrado, associado a condomínio, política, fonte oficial e receber alertas rastreáveis.

---

### Fase 2 — Airbnb Policy Monitor

Objetivo: transformar políticas oficiais do Airbnb em regras automáticas.

Entregas:

- Regras para câmeras, dispositivos e decibelímetros.
- Regras para festas e perturbação.
- Regras para hóspedes.
- Regras para anfitriões.
- Regras para precisão do anúncio.
- Registro de fonte oficial por regra.

Critério de sucesso:

- O sistema bloqueia ou alerta sobre câmera interna, gravação de áudio, câmera oculta, falta de divulgação de dispositivo e risco de festa.

---

### Fase 3 — LGPD, privacidade e dispositivos

Objetivo: garantir que sensores e dados pessoais sejam tratados de forma segura.

Entregas:

- Inventário de dispositivos.
- Inventário de dados pessoais.
- Campos de finalidade, base legal e retenção.
- Aviso de privacidade por imóvel.
- Logs de acesso.
- Bloqueios para gravação de áudio, câmera interna e biometria sem revisão.

Critério de sucesso:

- Nenhum dispositivo sensível pode ser ativado sem finalidade, localização, divulgação, regra de retenção e avaliação de risco.

---

### Fase 4 — Condomínio e vizinhança

Objetivo: evitar multas, conflitos e reclamações.

Entregas:

- Cadastro de convenção e regimento.
- Regras de horário de silêncio.
- Regras de visitantes, garagem, lixo, pets e áreas comuns.
- Portal de ocorrência para vizinho/síndico/porteiro.
- Workflow de ocorrência.
- Relatório mensal de incidentes.

Critério de sucesso:

- Um vizinho ou síndico consegue registrar uma ocorrência, o operador recebe alerta, resolve e deixa trilha de auditoria.

---

### Fase 5 — Operação: limpeza, check-in e manutenção

Objetivo: reduzir reviews negativos e falhas durante a estadia.

Entregas:

- Checklist pré-check-in.
- Checklist pós-checkout.
- Checklist de limpeza.
- Checklist de manutenção.
- Fotos de vistoria.
- Controle de tarefas.
- Alertas de comodidade crítica.

Critério de sucesso:

- O imóvel não entra em check-in sem limpeza confirmada, instruções válidas e pendências críticas resolvidas.

---

### Fase 6 — Reputação e receita

Objetivo: transformar monitoramento em vantagem operacional e financeira.

Entregas:

- Importação/análise de reviews.
- Classificação de reclamações.
- Ocupação, ADR, RevPAR e receita.
- Alertas de queda de nota.
- Alertas de preço/ocupação.
- Relatórios por imóvel e carteira.

Critério de sucesso:

- O operador entende quais riscos estão afetando reputação e receita, e quais ações priorizar.

---

### Fase 7 — Regulação municipal e inteligência regional

Objetivo: acompanhar regras por cidade, bairro e região.

Entregas:

- Cadastro de leis municipais.
- Cadastro de registro/licença municipal.
- Mapa de risco por cidade/bairro.
- Alertas de vencimento de registro.
- Benchmark com modelos internacionais.

Critério de sucesso:

- Um imóvel tem status regulatório por cidade, incluindo fontes, validade e revisão jurídica.

---

## 2. Backlog por épicos

### Épico A — Imóveis e anúncios

Histórias:

1. Como operador, quero cadastrar um imóvel para monitorar sua operação.
2. Como operador, quero associar um ou mais anúncios ao imóvel.
3. Como operador, quero informar capacidade máxima, comodidades e regras da casa.
4. Como proprietário, quero ver o status de risco do meu imóvel.

Critérios de aceite:

- O imóvel tem endereço, tipo, capacidade e responsável.
- O anúncio tem URL, plataforma, status e regras.
- O dashboard mostra risco consolidado.

Tabelas sugeridas:

```text
properties
listings
property_amenities
house_rules
property_documents
```

---

### Épico B — Fontes oficiais e regras

Histórias:

1. Como admin, quero cadastrar uma fonte oficial.
2. Como admin, quero criar uma regra derivada de uma fonte.
3. Como operador, quero ver qual fonte sustenta um alerta.
4. Como jurídico, quero marcar regras que exigem revisão.

Critérios de aceite:

- Toda regra tem fonte.
- Toda fonte tem URL, jurisdição, tipo e data de verificação.
- Regra interpretativa pode ser marcada como revisão jurídica obrigatória.

Tabelas sugeridas:

```text
sources
policy_rules
rule_versions
rule_conditions
rule_actions
```

---

### Épico C — Alertas e Evidence Vault

Histórias:

1. Como operador, quero receber alertas priorizados.
2. Como admin, quero ver evidências de cada alerta.
3. Como jurídico, quero revisar alertas críticos.
4. Como proprietário, quero ver ações tomadas e resultado.

Critérios de aceite:

- Todo alerta tem severidade, confiança, fonte, evidência e ação recomendada.
- Alertas P0/P1 ficam destacados.
- Alerta com inferência crítica exige revisão humana.

Tabelas sugeridas:

```text
alerts
evidence_items
alert_reviews
actions_taken
```

---

### Épico D — Privacidade, LGPD e dispositivos

Histórias:

1. Como operador, quero cadastrar dispositivos do imóvel.
2. Como plataforma, quero bloquear dispositivos proibidos.
3. Como admin, quero registrar finalidade e retenção de dados.
4. Como hóspede, quero ter transparência sobre dispositivos permitidos.

Critérios de aceite:

- Câmera interna é bloqueada.
- Gravação de áudio é bloqueada.
- Câmera oculta é bloqueada.
- Decibelímetro só é permitido se não gravar áudio e for divulgado.

Tabelas sugeridas:

```text
devices
device_disclosures
data_processing_activities
privacy_notices
access_logs
```

---

### Épico E — Condomínio e vizinhança

Histórias:

1. Como operador, quero cadastrar regras do condomínio.
2. Como síndico, quero reportar uma ocorrência.
3. Como operador, quero responder e resolver uma ocorrência.
4. Como proprietário, quero ver histórico de multas e reclamações.

Critérios de aceite:

- Ocorrência gera protocolo.
- Ocorrência tem status e responsável.
- Ocorrência pode gerar alerta e tarefa.
- Dados sensíveis são protegidos.

Tabelas sugeridas:

```text
condominiums
condo_rules
neighbor_reports
incidents
incident_comments
incident_attachments
```

---

### Épico F — Operação, limpeza e manutenção

Histórias:

1. Como operador, quero checklist pré-check-in.
2. Como equipe de limpeza, quero registrar conclusão com fotos.
3. Como manutenção, quero receber tarefa crítica.
4. Como proprietário, quero ver pendências por imóvel.

Critérios de aceite:

- Check-in não fica verde se limpeza crítica estiver pendente.
- Fotos de vistoria ficam associadas à estadia.
- Tarefas têm responsável e prazo.

Tabelas sugeridas:

```text
reservations
checklists
checklist_items
tasks
maintenance_tickets
inspection_photos
```

---

### Épico G — Reviews, reputação e receita

Histórias:

1. Como operador, quero importar reviews.
2. Como operador, quero classificar reclamações por tema.
3. Como proprietário, quero ver impacto na nota e receita.
4. Como admin, quero configurar palavras-chave de risco.

Critérios de aceite:

- Review negativo gera alerta se mencionar tema crítico.
- Reclamações são classificadas por categoria.
- Dashboard mostra nota, ocupação, receita e tendências.

Tabelas sugeridas:

```text
reviews
review_topics
revenue_metrics
occupancy_snapshots
price_recommendations
```

---

## 3. Modelo inicial de dados

### Entidade: Property

```json
{
  "id": "prop_123",
  "name": "Apartamento Centro",
  "address": "...",
  "city": "São Paulo",
  "state": "SP",
  "country": "BR",
  "property_type": "apartment",
  "max_guest_capacity": 4,
  "condo_id": "condo_123",
  "owner_id": "owner_123",
  "status": "active"
}
```

### Entidade: Rule

```json
{
  "id": "rule_airbnb_no_indoor_camera",
  "name": "Proibição de câmera interna",
  "source_id": "airbnb_3061",
  "severity": "P0",
  "condition": "device.is_internal == true && device.records_video == true",
  "action": "block_device_and_create_alert",
  "human_review_required": true
}
```

### Entidade: Alert

```json
{
  "id": "alert_123",
  "property_id": "prop_123",
  "rule_id": "rule_airbnb_no_indoor_camera",
  "severity": "P0",
  "confidence": 95,
  "status": "open",
  "source_url": "https://www.airbnb.com/help/article/3061",
  "recommended_action": "Remover dispositivo e revisar anúncio/disclosure.",
  "human_review_required": true
}
```

---

## 4. Priorização por impacto

### Sprint 1

- Criar tabelas `properties`, `listings`, `sources`, `policy_rules`, `alerts`.
- Criar CRUD de imóveis.
- Criar CRUD de fontes oficiais.
- Criar primeira lista de regras manuais.
- Criar dashboard básico de alertas.

### Sprint 2

- Criar inventário de dispositivos.
- Implementar bloqueios de câmera interna, áudio e câmera oculta.
- Criar regras de festa/ruído.
- Criar Evidence Vault básico.

### Sprint 3

- Criar cadastro de condomínio.
- Criar portal simples de ocorrência.
- Criar alertas de vizinhança.
- Criar tarefas de resolução.

### Sprint 4

- Criar checklists de limpeza, check-in e manutenção.
- Criar análise de reviews por palavras-chave.
- Criar relatório por imóvel.

### Sprint 5

- Criar módulos de receita/ocupação.
- Criar score consolidado.
- Criar relatórios exportáveis.

---

## 5. Critérios de qualidade

Nenhuma regra deve entrar em produção se:

- não tiver fonte;
- não tiver severidade;
- não tiver ação recomendada;
- não tiver campo de confiança;
- não definir se exige revisão humana;
- violar privacidade ou permitir coleta excessiva.

Nenhum alerta deve ser exibido como violação confirmada se:

- a evidência for apenas inferência;
- a fonte for secundária;
- houver conflito entre regra local e interpretação;
- envolver sanção ao hóspede sem revisão humana.

---

## 6. Próximas tarefas recomendadas

1. Verificar stack atual do repositório.
2. Criar modelo de dados inicial.
3. Criar seed com fontes oficiais.
4. Criar seed com regras P0/P1.
5. Implementar dashboard de alertas.
6. Implementar cadastro de dispositivos.
7. Implementar portal de ocorrência.
8. Implementar Evidence Vault.
9. Implementar checklists operacionais.
10. Implementar camada de reviews e reputação.
