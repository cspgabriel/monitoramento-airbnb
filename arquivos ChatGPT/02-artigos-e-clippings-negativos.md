# 02 — Artigos, pesquisas e clippings negativos

Este arquivo organiza artigos, pesquisas e ciclos negativos que a plataforma deve monitorar. O objetivo não é apenas colecionar notícias, mas transformar riscos recorrentes em módulos, alertas e tarefas de prevenção.

Data da curadoria: 03/06/2026.

---

## 1. Política editorial da aba Artigos

A plataforma deve ter uma aba chamada **Artigos** com curadoria por tema:

1. Legislação e regulação.
2. Condomínios e jurisprudência.
3. Privacidade, câmeras e sensores.
4. Festas, ruído e perturbação comunitária.
5. Segurança, golpes e incidentes.
6. Tributação e profissionalização da operação.
7. Mercado, preço, ocupação e previsão de receita.
8. Impacto urbano, turismo e moradia.
9. Dados, IA e qualidade de informação.
10. Boas práticas operacionais para anfitriões.

Cada artigo deve ter:

```text
title
author_or_source
source_type
url
jurisdiction
published_at
captured_at
tags
summary
risk_relevance
product_rules_created
confidence
requires_human_review
```

Tipos de fonte:

```text
official_policy
official_law
official_court
official_regulator
academic_paper
industry_report
news_clipping
blog_or_commentary
internal_incident
```

Regra editorial:

- Links oficiais sempre têm prioridade.
- Notícias e blogs podem servir como sinais, mas não como única base para alerta jurídico.
- Artigos acadêmicos servem para embasar modelos, limitações de dados e boas práticas, mas não substituem legislação local.

---

## 2. Artigos e pesquisas relevantes

### 2.1 Qualidade de dados em bases públicas de Airbnb

Fonte:

- arXiv — Problems with reproducing results from Inside Airbnb data: https://arxiv.org/abs/2007.03019

Por que é relevante:

Bases públicas e raspadas de anúncios podem ter problemas de atualização, coordenadas aproximadas, inconsistência, reprodutibilidade e completude. A plataforma deve evitar tratar dados externos como prova absoluta.

Aplicação no produto:

- Criar campo `data_quality_score`.
- Criar campo `confidence` em todos os alertas.
- Separar evidência direta, inferência e fonte secundária.
- Exigir revisão humana para decisões críticas.

Regra sugerida:

```text
Se alerta for baseado apenas em dado externo não verificado, marcar como "possível risco" e exigir revisão humana antes de ação punitiva.
```

---

### 2.2 Identificação de possíveis violações regulatórias em Airbnb

Fonte:

- arXiv — Identifying potential regulatory violations in Airbnb listings: https://arxiv.org/abs/2211.16617

Por que é relevante:

Pesquisas sobre violações regulatórias em anúncios mostram que é possível detectar padrões suspeitos, mas também destacam limitações importantes: localização, ocupação e dados públicos nem sempre são precisos.

Aplicação no produto:

- Criar módulo de detecção de risco regulatório.
- Classificar alertas como `possible_violation`, `likely_violation` ou `confirmed_violation`.
- Exigir evidência oficial para status confirmado.

Regra sugerida:

```text
Nenhum imóvel deve ser marcado como irregular confirmado sem fonte oficial, documento do imóvel, regra municipal ou revisão jurídica.
```

---

### 2.3 Previsão de demanda, receita e ocupação

Fonte:

- arXiv — pesquisas sobre Airbnb, previsão de receita, mobilidade, acessibilidade urbana e dados de anúncios: https://arxiv.org/search/?query=Airbnb+revenue+forecasting&searchtype=all

Por que é relevante:

A plataforma pode evoluir de monitoramento de risco para inteligência operacional: previsão de ocupação, receita, preço, demanda por bairro, sazonalidade, eventos locais e performance relativa.

Aplicação no produto:

- Score de oportunidade de receita.
- Previsão de ocupação futura.
- Alerta de preço fora do padrão.
- Comparação com imóveis semelhantes.
- Eventos locais e calendário de alta demanda.

---

### 2.4 Turismo, pressão urbana e capacidade de carga

Fontes:

- EUR-Lex — Regulation (EU) 2024/1028 sobre coleta e compartilhamento de dados de locações de curta duração: https://eur-lex.europa.eu/eli/reg/2024/1028/oj
- arXiv — pesquisas sobre turismo, crowding, previsão geotemporal e capacidade de carga: https://arxiv.org/search/?query=tourism+crowding+forecasting+capacity&searchtype=all

Por que é relevante:

O Airbnb pode gerar pressão sobre bairros, condomínios, segurança, moradia, ruído e turismo. A plataforma deve permitir análise não apenas por imóvel, mas por região.

Aplicação no produto:

- Mapa de concentração de imóveis.
- Reclamações por bairro.
- Incidentes por região.
- Heatmap de risco regulatório.
- Score de saturação turística.
- Relatórios para operadores, condomínios e eventualmente poder público.

---

### 2.5 Segurança, IoT e smart apartments

Fontes:

- arXiv — pesquisas sobre smart apartments, IoT, segurança e privacidade: https://arxiv.org/search/?query=smart+apartment+security+privacy+IoT&searchtype=all
- ANPD/Gov.br — Autoridade Nacional de Proteção de Dados: https://www.gov.br/anpd/pt-br

Por que é relevante:

A plataforma pode integrar fechaduras inteligentes, sensores de ruído, vazamento, fumaça, temperatura e ocupação indireta. Isso exige segurança técnica, minimização de dados e prevenção contra abuso.

Aplicação no produto:

- Inventário de dispositivos.
- Status de bateria/conectividade.
- Permissões de acesso.
- Logs de acesso administrativo.
- Retenção limitada.
- Política de privacidade por dispositivo.

Regra sugerida:

```text
Todo dispositivo deve ter finalidade, localização, tipo de dado coletado, retenção, divulgação ao hóspede e avaliação de permissão Airbnb/LGPD.
```

---

## 3. Clippings negativos — categorias prioritárias

A aba **Clippings Negativos** deve funcionar como radar de risco. Os casos não precisam sempre ser do mesmo país, mas devem ser classificados por aplicabilidade ao Brasil, ao condomínio e às políticas do Airbnb.

### 3.1 Festas, eventos e perturbação

Fontes oficiais relacionadas:

- Airbnb — Disruptive gatherings and events policy: https://www.airbnb.com/help/article/2704
- Airbnb — How we assess risk for disruptive parties: https://www.airbnb.com/help/article/3280
- Airbnb — Neighborhood Support: https://www.airbnb.com/help/article/3290

Riscos monitoráveis:

- Festa não autorizada.
- Excesso de convidados.
- Ruído durante horário de silêncio.
- Lixo excessivo.
- Danos.
- Estacionamento irregular.
- Fumo e incômodo a vizinhos.
- Reincidência em mesmo imóvel.

Sinais de produto:

```text
neighbor_complaint_count
noise_peak_count
quiet_hours_violation_count
reservation_weekend
reservation_one_night
approved_guest_count
max_capacity
trash_incident_count
parking_incident_count
```

Ações sugeridas:

- Mensagem automática preventiva antes do check-in.
- Alerta ao operador durante a estadia.
- Checklist pós-incidente.
- Bloqueio temporário de datas críticas.
- Revisão das regras da casa.
- Relatório ao proprietário/condomínio.

---

### 3.2 Câmeras, áudio e invasão de privacidade

Fontes oficiais relacionadas:

- Airbnb — Cameras, recording devices, noise decibel monitors, and smart home devices: https://www.airbnb.com/help/article/3061
- LGPD — Lei nº 13.709/2018: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm
- ANPD: https://www.gov.br/anpd/pt-br

Riscos monitoráveis:

- Câmera interna.
- Câmera oculta.
- Dispositivo que grava áudio.
- Divulgação incompleta de câmera externa.
- Retenção excessiva de dado.
- Acesso indevido por funcionário ou prestador.

Sinais de produto:

```text
device_records_audio
device_is_internal
device_is_hidden
device_disclosure_missing
privacy_notice_missing
retention_policy_missing
```

Ações sugeridas:

- Bloqueio de cadastro de dispositivo proibido.
- Tarefa de remoção imediata.
- Revisão LGPD.
- Atualização do anúncio e aviso ao hóspede.
- Auditoria de acesso.

---

### 3.3 Condomínio, vizinhança e multas

Fontes oficiais relacionadas:

- Código Civil — Lei nº 10.406/2002: https://www.planalto.gov.br/ccivil_03/leis/2002/l10406compilada.htm
- STJ — consulta processual: https://processo.stj.jus.br/processo/pesquisa/
- STJ — portal oficial: https://www.stj.jus.br/

Riscos monitoráveis:

- Convenção proíbe ou restringe locação curta.
- Regimento define horário de silêncio incompatível com operação.
- Visitantes e hóspedes não seguem regras de identificação.
- Uso de áreas comuns por hóspedes não autorizado.
- Multas por garagem, lixo, pets, ruído ou uso irregular.

Sinais de produto:

```text
condo_short_term_rental_allowed
condo_minimum_stay_days
condo_guest_identification_required
condo_common_area_restriction
condo_fine_count
condo_repeat_incident_count
```

Ações sugeridas:

- Cadastro completo de convenção/regimento.
- Checklist condominial antes de publicar o anúncio.
- Mensagem de regras do prédio no pré-check-in.
- Relatório mensal ao proprietário.
- Revisão jurídica quando houver conflito.

---

### 3.4 Golpes, fraudes e segurança do hóspede/anfitrião

Fontes oficiais relacionadas:

- Airbnb Help Center — Central de ajuda e segurança: https://www.airbnb.com/help
- Airbnb — AirCover e suporte: https://www.airbnb.com/aircover
- Delegacias e órgãos de segurança locais, quando houver caso real.

Riscos monitoráveis:

- Anúncio falso em canal externo.
- Pagamento por fora.
- Phishing.
- Hóspede com comportamento suspeito.
- Prestador sem autorização.
- Roubo de itens.
- Dano ou violação de acesso.

Sinais de produto:

```text
external_payment_request
suspicious_message_terms
unverified_channel_contact
smart_lock_unusual_access
maintenance_vendor_unapproved
inventory_missing_after_checkout
```

Ações sugeridas:

- Alerta de pagamento por fora.
- Bloqueio de link suspeito.
- Inventário antes/depois.
- Registro de acesso de fechadura.
- Tarefa de troca de senha/código.

---

### 3.5 Limpeza, saúde e manutenção

Fontes oficiais relacionadas:

- Airbnb — Ground rules for Hosts: https://www.airbnb.com/help/article/2895
- Código de Defesa do Consumidor — Lei nº 8.078/1990: https://www.planalto.gov.br/ccivil_03/leis/l8078compilado.htm

Riscos monitoráveis:

- Mofo.
- Pragas.
- Sujeira grave.
- Roupa de cama inadequada.
- Banheiro/cozinha fora de padrão.
- Falha de ar-condicionado, Wi-Fi, energia ou fechadura.
- Vazamento.
- Falha em detector de fumaça/CO quando aplicável.

Sinais de produto:

```text
review_mentions_mold
review_mentions_pest
review_mentions_dirty
cleaning_checklist_failed
maintenance_ticket_open
critical_amenity_offline
pre_checkin_inspection_missing
```

Ações sugeridas:

- Bloqueio preventivo de calendário.
- Tarefa urgente de limpeza/manutenção.
- Comunicação proativa com hóspede.
- Revisão de fotos e descrição do anúncio.

---

### 3.6 Tributação, profissionalização e documentação

Fontes oficiais relacionadas:

- Receita Federal: https://www.gov.br/receitafederal/pt-br
- Lei Complementar nº 214/2025: https://www.planalto.gov.br/ccivil_03/leis/lcp/lcp214.htm
- Cadastur: https://cadastur.turismo.gov.br/
- Lei Geral do Turismo — Lei nº 11.771/2008: https://www.planalto.gov.br/ccivil_03/_ato2007-2010/2008/lei/l11771.htm

Riscos monitoráveis:

- Operação multiunidade sem enquadramento claro.
- Receita não conciliada.
- Documentos fiscais pendentes.
- Serviços adicionais que aproximam a operação de hospedagem profissional.
- Cadastro turístico exigível em determinados contextos.

Sinais de produto:

```text
monthly_revenue
number_of_units_managed
additional_services_offered
invoice_required
cadastur_status
municipal_tax_rule
```

Ações sugeridas:

- Relatório fiscal mensal.
- Exportação para contabilidade.
- Revisão de enquadramento.
- Cadastro de documentos e vencimentos.

---

## 4. Modelo de registro de clipping negativo

```json
{
  "title": "Festa não autorizada gera reclamação de vizinhos",
  "source_type": "official_policy_or_news_clipping",
  "source_url": "https://www.airbnb.com/help/article/2704",
  "country": "BR",
  "city": "São Paulo",
  "risk_category": "party_disturbance",
  "affected_modules": ["party_risk", "neighbor_portal", "condo_rules"],
  "summary": "Caso ou categoria de risco relacionada a ruído, convidados extras e reclamações.",
  "signals_to_monitor": ["noise_peak", "neighbor_complaint", "quiet_hours_violation"],
  "recommended_rules": ["Criar alerta P0 quando houver reclamação + pico de ruído durante reserva ativa."],
  "confidence": 80,
  "requires_human_review": true
}
```

---

## 5. Abas recomendadas na plataforma

### Aba Artigos

Filtros:

- Fonte oficial.
- Acadêmico.
- Jurisprudência.
- Legislação.
- Mercado.
- Segurança.
- Privacidade.
- Condomínio.
- Cidade.

### Aba Clippings Negativos

Filtros:

- Festa/ruído.
- Câmera/privacidade.
- Golpe/fraude.
- Acidente/segurança.
- Condomínio/multa.
- Review negativo.
- Regulação municipal.
- Tributação.
- Dados/IA.

### Aba Regras Derivadas

Cada artigo ou clipping pode gerar:

- uma nova regra;
- um novo alerta;
- um checklist;
- uma tarefa de compliance;
- uma alteração de score;
- uma exigência de documentação;
- uma recomendação de revisão jurídica.

---

## 6. Priorização

Alta prioridade:

1. Políticas oficiais do Airbnb.
2. LGPD e privacidade.
3. Código Civil, condomínio e vizinhança.
4. Festas, ruído e suporte de vizinhança.
5. Limpeza, manutenção e segurança.
6. Registro/licença municipal quando aplicável.
7. Decisões judiciais e convenções condominiais.

Média prioridade:

1. Artigos acadêmicos sobre dados e previsão.
2. Benchmarks internacionais.
3. Mercado, precificação e ocupação.
4. Relatórios setoriais.

Baixa prioridade:

1. Notícias sem fonte primária.
2. Posts opinativos.
3. Conteúdo sem data ou sem jurisdição clara.
