# 03 — Especificação da plataforma de monitoramento Airbnb

Data da especificação: 03/06/2026.

## 1. Visão do produto

A plataforma deve ser um sistema de monitoramento operacional, jurídico, reputacional e ambiental para imóveis anunciados no Airbnb e em locações de curta temporada.

A proposta não é apenas controlar reservas. O objetivo é prevenir problemas antes que eles se tornem multa, suspensão do anúncio, reclamação de vizinho, processo, review negativo, risco de privacidade ou perda de receita.

Frase de posicionamento:

> A plataforma que mantém seu Airbnb rentável, seguro, regular, respeitoso com vizinhos e protegido contra riscos de suspensão, multa e reputação.

## 2. Usuários principais

### 2.1 Administrador da plataforma

Responsável por configurar regras, fontes, score, integrações, usuários, permissões e visão geral dos imóveis.

Necessidades:

- ver risco consolidado da carteira;
- gerenciar imóveis, anúncios, reservas e dispositivos;
- configurar regras por cidade, condomínio e política do Airbnb;
- auditar alertas e evidências;
- exportar relatórios.

### 2.2 Proprietário

Responsável pelo resultado financeiro e pela regularidade do imóvel.

Necessidades:

- ver receita, ocupação e risco;
- receber alertas objetivos;
- entender por que uma ação foi recomendada;
- acompanhar multas, reclamações, reviews e manutenção.

### 2.3 Operador / gestor de locação

Responsável pelo dia a dia da hospedagem.

Necessidades:

- saber o que fazer antes, durante e depois da estadia;
- acompanhar check-in, limpeza, manutenção e comunicação;
- resolver incidentes rapidamente;
- registrar evidências.

### 2.4 Síndico / condomínio / vizinhança

Responsável por reportar ocorrências e acompanhar resolução sem exposição indevida de dados.

Necessidades:

- registrar reclamação de ruído, lixo, garagem, fumo ou visitantes;
- anexar evidências não invasivas;
- acompanhar status;
- preservar privacidade dos envolvidos.

### 2.5 Compliance / jurídico / contabilidade

Responsável por revisar regras, documentação e enquadramento.

Necessidades:

- ver fontes oficiais;
- revisar regras interpretativas;
- validar documentos;
- exportar trilha de auditoria.

## 3. Princípios de design

1. Monitorar a operação, não vigiar hóspedes.
2. Todo alerta deve mostrar fonte, evidência, confiança e ação recomendada.
3. Alertas críticos exigem revisão humana quando envolverem inferência, privacidade, sanção ou irregularidade jurídica.
4. Dados pessoais devem seguir LGPD: minimização, finalidade, transparência, segurança, prevenção, retenção limitada e prestação de contas.
5. Política oficial do Airbnb deve virar regra operacional.
6. Regra condominial e municipal deve ser configurável por imóvel.
7. Notícia ou clipping negativo não deve ser fonte única para decisão crítica.
8. O sistema deve separar "risco possível", "risco provável" e "violação confirmada".
9. O produto deve gerar tarefas, não apenas alarmes.
10. A plataforma deve ser útil para anfitrião, operador, proprietário e condomínio.

## 4. Módulos do produto

### 4.1 Cadastro de imóveis e anúncios

Campos mínimos:

```text
property_id
owner_id
address
city
state
country
property_type
building_type
condo_id
listing_urls
platforms
max_guest_capacity
bedrooms
bathrooms
amenities
house_rules
photos_last_updated_at
listing_accuracy_status
```

Funcionalidades:

- cadastro de imóvel;
- cadastro de anúncio por plataforma;
- capacidade máxima;
- regras da casa;
- comodidades;
- fotos e última vistoria;
- associação a condomínio;
- status de documentação.

Alertas:

- anúncio sem regras da casa;
- capacidade anunciada maior que capacidade autorizada;
- comodidade prometida sem evidência;
- fotos antigas;
- endereço ou tipo de imóvel inconsistentes.

---

### 4.2 Legal & Registration Intelligence

Objetivo:

Avaliar se o imóvel pode operar como locação de curta temporada naquele contexto jurídico, municipal e condominial.

Campos:

```text
city_rules_status
municipal_registration_required
municipal_registration_number
municipal_registration_valid_until
license_required
license_status
condo_short_term_rental_allowed
condo_minimum_stay_days
contract_restrictions
court_references
legal_review_status
```

Funcionalidades:

- cadastro de leis municipais;
- cadastro de fontes oficiais;
- cadastro de convenção/regimento;
- controle de vencimento de registro/licença;
- status jurídico por imóvel;
- recomendação de revisão jurídica.

Alertas:

- P0: operação em cidade com registro obrigatório sem registro cadastrado;
- P1: regra de condomínio proíbe ou restringe locação curta;
- P1: registro vencido ou ausente;
- P2: documento pendente de revisão.

---

### 4.3 Airbnb Policy Monitor

Objetivo:

Converter políticas oficiais do Airbnb em regras monitoráveis.

Fontes principais:

- https://www.airbnb.com/help/article/3061
- https://www.airbnb.com/help/article/2704
- https://www.airbnb.com/help/article/2894
- https://www.airbnb.com/help/article/2895
- https://www.airbnb.com/help/article/3280
- https://www.airbnb.com/help/article/3290

Funcionalidades:

- políticas versionadas;
- regras derivadas;
- verificação automática de anúncios, dispositivos, house rules e ocorrências;
- alertas de risco de festa, privacidade, limpeza, check-in e precisão do anúncio.

Alertas:

- P0: câmera interna;
- P0: dispositivo com áudio;
- P0: câmera oculta;
- P1: decibelímetro não divulgado;
- P1: anúncio sugere festa/evento;
- P1: review recente menciona mofo, praga ou sujeira grave;
- P2: house rules incompletas.

---

### 4.4 Privacy & LGPD Center

Objetivo:

Controlar dados pessoais, sensores, acesso, retenção e transparência.

Campos:

```text
data_processing_activity
personal_data_type
purpose
legal_basis
retention_period
data_subject_type
access_roles
sharing_parties
privacy_notice_url
risk_assessment_status
```

Funcionalidades:

- inventário de dados pessoais;
- inventário de dispositivos;
- política de retenção;
- registros de acesso;
- aviso de privacidade;
- revisão de base legal;
- bloqueios para coleta invasiva.

Alertas:

- P0: gravação de áudio;
- P0: câmera interna;
- P0: biometria sem revisão jurídica;
- P1: ausência de finalidade/base legal;
- P1: ausência de retenção definida;
- P2: aviso de privacidade desatualizado.

---

### 4.5 Party & Disturbance Risk

Objetivo:

Prevenir festas, eventos disruptivos, ruído, lixo, fumo, estacionamento irregular e reclamações.

Sinais:

```text
reservation_length
reservation_weekend
reservation_holiday
approved_guest_count
max_capacity
noise_peak_count
quiet_hours_violation
neighbor_complaint
condo_complaint
trash_incident
parking_incident
smoking_incident
repeat_incident_count
```

Score sugerido:

```text
party_risk_score =
  reservation_risk
+ capacity_pressure
+ timing_risk
+ property_history_risk
+ noise_signal_risk
+ neighbor_complaint_risk
- preventive_actions_completed
```

Funcionalidades:

- score pré-reserva;
- score durante estadia;
- alertas em horário de silêncio;
- mensagem preventiva para hóspede;
- workflow de incidente;
- relatório para proprietário/condomínio.

Alertas:

- P0: reclamação + pico de ruído + reserva ativa;
- P1: pico de ruído em horário de silêncio;
- P1: reserva de alto risco por padrões de duração/data/capacidade;
- P2: reincidência de perturbação no imóvel.

---

### 4.6 Neighbor & Condo Portal

Objetivo:

Criar canal estruturado para vizinhos, porteiros, síndicos e administradoras registrarem problemas.

Campos de ocorrência:

```text
incident_type
property_unit
reported_by_type
reported_at
incident_started_at
severity
description
evidence_attachment
privacy_sensitive
status
assigned_to
resolution
```

Tipos de incidente:

- ruído;
- festa;
- lixo;
- garagem;
- fumo;
- visitantes;
- pet;
- dano;
- uso indevido de área comum;
- segurança.

Funcionalidades:

- formulário externo;
- protocolo de ocorrência;
- anexos;
- status;
- SLA;
- resposta sem exposição indevida de hóspedes;
- relatório mensal.

---

### 4.7 Listing Accuracy & Trust Monitor

Objetivo:

Garantir que o anúncio corresponde ao imóvel real.

Checagens:

- comodidades prometidas versus inventário;
- fotos versus vistoria;
- capacidade;
- regras da casa;
- ruído externo relevante;
- privacidade;
- tipo de imóvel;
- check-in;
- acesso a áreas comuns.

Alertas:

- P1: comodidade anunciada indisponível;
- P1: check-in sem instrução válida;
- P1: anúncio omite limitação relevante;
- P2: fotos antigas;
- P2: regras incompletas.

---

### 4.8 Cleanliness, Maintenance & Safety

Objetivo:

Reduzir reviews negativos, reembolsos, riscos de saúde e falhas críticas.

Funcionalidades:

- checklist de limpeza;
- checklist de manutenção;
- fotos de vistoria;
- controle de tarefas;
- detector de palavras negativas em review;
- sensores permitidos: vazamento, fumaça, temperatura, ruído sem áudio, bateria de fechadura.

Alertas:

- P1: review menciona mofo, praga, sujeira grave ou risco de saúde;
- P1: limpeza não confirmada antes do check-in;
- P1: fechadura inteligente com bateria baixa;
- P1: vazamento detectado;
- P2: manutenção recorrente.

---

### 4.9 Reputation & Revenue Intelligence

Objetivo:

Monitorar reputação e desempenho econômico.

Métricas:

```text
average_rating
review_count
negative_review_rate
response_time
cancellation_rate
occupancy_rate
ADR
RevPAR
revenue
future_occupancy
price_gap_to_competitors
```

Funcionalidades:

- análise de reviews;
- categorias de reclamação;
- previsão de ocupação;
- previsão de receita;
- comparação com mercado;
- recomendações de preço;
- impacto de incidentes na receita.

Alertas:

- P1: queda brusca de nota;
- P1: sequência de reviews negativos;
- P2: ocupação futura baixa;
- P2: preço fora do padrão;
- P3: oportunidade de reajuste em evento local.

---

### 4.10 Evidence Vault

Objetivo:

Guardar evidências, fontes, decisões e auditoria.

Cada alerta deve ter:

```text
alert_id
property_id
rule_id
source_url
evidence_type
evidence_payload
generated_at
confidence
severity
human_review_required
reviewed_by
review_decision
action_taken
outcome
```

Princípios:

- evidência não é prova automática;
- evidência sensível deve ter retenção curta;
- acesso deve ser logado;
- decisões críticas precisam de revisão humana;
- toda fonte legal/política deve ser versionada.

## 5. Score principal

Score consolidado:

```text
Airbnb Monitoring Score =
  Legal/Registration Risk
+ Airbnb Policy Risk
+ Privacy/LGPD Risk
+ Party/Disturbance Risk
+ Condo/Neighbor Risk
+ Listing Accuracy Risk
+ Cleanliness/Safety Risk
+ Reputation Risk
+ Revenue Risk
- Mitigation Actions Completed
```

Escala:

```text
0-20   baixo risco
21-40  atenção
41-60  risco médio
61-80  risco alto
81-100 risco crítico
```

Cada componente deve ter:

```text
score
severity
confidence
source_count
open_alerts
last_updated_at
recommended_actions
```

## 6. Severidade dos alertas

### P0 — Crítico

Usar quando houver risco imediato de violação grave, suspensão, privacidade, segurança ou irregularidade relevante.

Exemplos:

- câmera interna;
- áudio gravado;
- câmera oculta;
- festa ativa com reclamação e ruído;
- operação sem registro obrigatório em cidade que exige cadastro;
- incidente de segurança grave.

### P1 — Alto

Usar quando houver risco relevante, mas com possibilidade de correção rápida.

Exemplos:

- decibelímetro não divulgado;
- regra condominial conflitante;
- review com mofo/praga/sujeira;
- check-in inválido;
- anúncio com comodidade falsa.

### P2 — Médio

Usar para reincidência, pendência documental, inconsistência ou risco operacional.

Exemplos:

- documento próximo do vencimento;
- fotos antigas;
- reclamações recorrentes;
- SLA de resposta ruim.

### P3 — Oportunidade

Usar para melhoria de receita, experiência, copy, precificação e eficiência.

Exemplos:

- preço abaixo do mercado;
- baixa ocupação futura;
- regras da casa pouco claras;
- oportunidade de melhoria de fotos.

## 7. Diferenciais competitivos

1. Compliance + operação + receita na mesma plataforma.
2. Fontes oficiais vinculadas a cada alerta.
3. Módulo específico para condomínio e vizinhança.
4. Privacy by design para sensores e LGPD.
5. Evidence Vault para auditoria.
6. Scores interpretáveis, sem caixa-preta.
7. Curadoria de artigos e clippings negativos transformada em regras.
8. Adaptação por cidade, condomínio e imóvel.
9. Tarefas práticas, não apenas dashboards.
10. Visão de carteira para operadores com muitos imóveis.

## 8. MVP recomendado

MVP de maior valor:

1. Cadastro de imóveis/anúncios.
2. Cadastro de condomínio e regras.
3. Fontes oficiais e motor básico de regras.
4. Alertas P0/P1.
5. Portal de ocorrências de vizinhos/condomínio.
6. Inventário de dispositivos e bloqueios de privacidade.
7. Checklists de limpeza/check-in.
8. Evidence Vault simples.
9. Dashboard de risco por imóvel.
10. Relatórios exportáveis.

## 9. Métricas de sucesso

Produto:

- imóveis cadastrados;
- regras cadastradas por imóvel;
- alertas resolvidos;
- tempo médio de resolução;
- redução de incidentes reincidentes;
- redução de reviews negativos;
- redução de multas;
- aumento de ocupação/receita;
- fontes oficiais atualizadas;
- alertas com evidência completa.

Qualidade:

- falsos positivos;
- falsos negativos;
- alertas sem fonte;
- alertas sem evidência;
- decisões automatizadas revertidas;
- regras vencidas/desatualizadas.

Privacidade:

- dispositivos bloqueados por violação;
- atividades de tratamento com finalidade definida;
- dados com retenção vencida eliminados;
- acessos auditados;
- incidentes de privacidade.
