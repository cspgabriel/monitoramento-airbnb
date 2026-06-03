# 01 — Fontes oficiais e legislação

Este arquivo reúne as fontes oficiais que devem alimentar a plataforma de monitoramento Airbnb. A regra do produto deve ser: **nenhum alerta jurídico, regulatório ou de política deve existir sem fonte oficial vinculada**.

Data da curadoria: 03/06/2026.

---

## 1. Políticas oficiais do Airbnb

### 1.1 Câmeras, dispositivos de gravação, ruído e dispositivos inteligentes

Fonte oficial:

- Airbnb Help Center — Security cameras, recording devices, noise decibel monitors, and smart home devices: https://www.airbnb.com/help/article/3061
- Airbnb Help Center — Privacy and security policy reference: https://www.airbnb.com/help/article/2914

Relevância para a plataforma:

- Câmeras internas devem ser tratadas como risco crítico.
- Câmeras ocultas devem ser bloqueadas.
- Dispositivos que gravam áudio devem ser bloqueados.
- Monitores de decibéis só devem ser aceitos se não gravarem áudio.
- A existência e a localização de dispositivos permitidos devem ser informadas ao hóspede conforme a política aplicável.
- Dispositivos externos não podem invadir áreas de privacidade maior, como banheiros externos, saunas, chuveiros externos ou áreas similares.

Campos sugeridos:

```text
device_type
location
is_internal
is_external
records_audio
records_video
is_hidden
is_disclosed_to_guest
disclosure_text
allowed_by_airbnb_policy
allowed_by_local_law
risk_level
source_url
```

Alertas sugeridos:

- P0 — câmera interna cadastrada.
- P0 — dispositivo com gravação de áudio.
- P0 — câmera oculta.
- P1 — câmera externa não divulgada.
- P1 — monitor de decibéis não divulgado.
- P1 — câmera externa direcionada para área de privacidade.

---

### 1.2 Festas, eventos e perturbação da vizinhança

Fonte oficial:

- Airbnb Help Center — Disruptive gatherings and events policy: https://www.airbnb.com/help/article/2704
- Airbnb Help Center — How we assess risk for disruptive parties: https://www.airbnb.com/help/article/3280
- Airbnb Help Center — Neighborhood Support: https://www.airbnb.com/help/article/3290

Relevância para a plataforma:

- O produto deve identificar risco de festa, reunião disruptiva, ruído excessivo, lixo, fumo, estacionamento irregular, vandalismo, invasão de propriedade e reincidência.
- O produto deve oferecer um canal de vizinhança/condomínio para registrar ocorrências.
- O produto deve diferenciar alerta preventivo, ocorrência em andamento e reincidência.
- O produto não deve acusar automaticamente o hóspede; deve mostrar evidências, confiança e necessidade de revisão humana.

Sinais possíveis:

```text
reservation_length
reservation_start_day
reservation_over_weekend
approved_guest_count
max_guest_capacity
noise_peak_event
quiet_hours_violation
neighbor_complaint
condo_complaint
trash_complaint
parking_complaint
smoking_complaint
repeat_incident_count
```

Alertas sugeridos:

- P0 — festa em andamento com reclamação + pico de ruído + reserva ativa.
- P1 — possível perturbação no horário de silêncio.
- P1 — reserva de alto risco para reunião disruptiva.
- P2 — reincidência de reclamações por lixo, fumo, garagem ou visitas.

---

### 1.3 Regras para hóspedes

Fonte oficial:

- Airbnb Help Center — Ground rules for guests: https://www.airbnb.com/help/article/2894

Relevância para a plataforma:

- A plataforma deve transformar regras do hóspede em checklist pré-check-in, regras da casa e alertas durante a estadia.
- Deve monitorar excesso de hóspedes, desrespeito ao check-in/check-out, fumo, pets não autorizados, danos, sujeira grave e perturbação da comunidade.

Campos sugeridos:

```text
house_rules_version
max_guests
approved_guest_count
quiet_hours
smoking_allowed
pets_allowed
party_allowed
check_in_window
check_out_time
violation_type
evidence
source_url
```

---

### 1.4 Regras para anfitriões

Fonte oficial:

- Airbnb Help Center — Ground rules for Hosts: https://www.airbnb.com/help/article/2895

Relevância para a plataforma:

- A plataforma deve auditar precisão do anúncio, limpeza, comunicação, check-in, comodidades, localização, ruído externo, regras da casa e saúde/segurança.
- O anúncio deve ser tratado como uma fonte contratual/operacional que precisa bater com a realidade do imóvel.

Alertas sugeridos:

- P1 — anúncio promete comodidade inexistente.
- P1 — check-in sem instrução válida.
- P1 — review cita mofo, praga, sujeira grave ou risco de saúde.
- P2 — fotos ou descrições desatualizadas.
- P2 — tempo de resposta acima do SLA definido.

---

### 1.5 Hospedagem responsável no Brasil

Fonte oficial:

- Airbnb — Hospedagem responsável no Brasil: https://www.airbnb.com/help/article/1345

Relevância para a plataforma:

- O Airbnb orienta anfitriões a verificarem permissões, contratos, regras de moradia, restrições de condomínio, impostos e regulações locais.
- A plataforma deve ter módulo para cadastro de permissões, condomínio, impostos, documentos e riscos locais.

---

## 2. Legislação brasileira — fontes oficiais

### 2.1 LGPD — Lei Geral de Proteção de Dados Pessoais

Fontes oficiais:

- Planalto — Lei nº 13.709/2018: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm
- Câmara dos Deputados — Lei nº 13.709/2018: https://www2.camara.leg.br/legin/fed/lei/2018/lei-13709-14-agosto-2018-787077-publicacaooriginal-156212-pl.html
- ANPD/Gov.br: https://www.gov.br/anpd/pt-br

Relevância para a plataforma:

- Monitoramento de Airbnb envolve dados pessoais de hóspedes, anfitriões, vizinhos, porteiros, síndicos e prestadores.
- O produto deve aplicar minimização, finalidade, adequação, necessidade, transparência, segurança, prevenção, não discriminação e prestação de contas.
- O produto deve evitar áudio, vídeo interno, biometria e rastreamento individual desnecessário.
- Deve haver política de retenção por tipo de dado.

Campos sugeridos:

```text
data_category
personal_data_type
legal_basis
purpose
retention_period
controller
processor
shared_with
security_controls
titular_rights_flow
```

Alertas sugeridos:

- P0 — dispositivo grava áudio ou vídeo interno.
- P0 — coleta de biometria sem base legal robusta.
- P1 — ausência de finalidade documentada.
- P1 — ausência de prazo de retenção.
- P2 — ausência de aviso de privacidade para hóspede/prestador.

---

### 2.2 Código Civil — condomínio, vizinhança e propriedade

Fontes oficiais:

- Planalto — Código Civil, Lei nº 10.406/2002: https://www.planalto.gov.br/ccivil_03/leis/2002/l10406compilada.htm
- Câmara dos Deputados — Lei nº 10.406/2002: https://www2.camara.leg.br/legin/fed/lei/2002/lei-10406-10-janeiro-2002-432893-publicacaooriginal-1-pl.html

Tópicos relevantes:

- Direito de vizinhança: interferências prejudiciais à segurança, ao sossego e à saúde.
- Condomínio edilício: convenção, regimento interno, deveres do condômino, multas, uso da unidade, sossego, salubridade, segurança e papel do síndico.

Relevância para a plataforma:

- O produto deve cadastrar convenção, regimento, regras de uso, regras de garagem, elevador, lixo, festas, visitantes, pets e horário de silêncio.
- O produto deve gerar alertas para riscos de multa, reincidência e comportamento antissocial.

Campos sugeridos:

```text
condo_name
condo_rules_document
short_term_rental_allowed
minimum_stay_days
visitor_policy
quiet_hours
parking_rules
trash_rules
pet_rules
fine_policy
syndic_contact
admin_contact
```

Alertas sugeridos:

- P1 — regra condominial proíbe ou restringe locação curta.
- P1 — número de hóspedes/visitantes acima do limite condominial.
- P1 — ocorrência durante horário de silêncio.
- P2 — reincidência de lixo/garagem/fumo.

---

### 2.3 Lei do Inquilinato e locação por temporada

Fontes oficiais:

- Planalto — Lei nº 8.245/1991: https://www.planalto.gov.br/ccivil_03/leis/l8245.htm
- Câmara dos Deputados — Lei nº 8.245/1991: https://www2.camara.leg.br/legin/fed/lei/1991/lei-8245-18-outubro-1991-363084-normaatualizada-pl.html

Relevância para a plataforma:

- A locação por temporada é um dos enquadramentos possíveis, mas não resolve automaticamente questões de condomínio, legislação municipal, tributação, relação de consumo ou política de plataforma.
- A plataforma deve separar: locação por temporada, hospedagem, uso misto, condomínio residencial e exigências municipais.

Campos sugeridos:

```text
rental_legal_framework
stay_duration_days
is_furnished
is_seasonal_use
is_hospitality_service
municipal_registration_required
condo_restriction_exists
```

---

### 2.4 Lei Geral do Turismo e meios de hospedagem

Fontes oficiais:

- Planalto — Lei nº 11.771/2008: https://www.planalto.gov.br/ccivil_03/_ato2007-2010/2008/lei/l11771.htm
- Câmara dos Deputados — Lei nº 11.771/2008: https://www2.camara.leg.br/legin/fed/lei/2008/lei-11771-17-setembro-2008-580400-normaatualizada-pl.html
- Ministério do Turismo / Cadastur: https://cadastur.turismo.gov.br/

Relevância para a plataforma:

- O produto deve avaliar se determinado operador atua como meio de hospedagem, prestador turístico ou locador residencial, dependendo da configuração operacional.
- Em casos de operação profissionalizada, multiunidades, serviços adicionais ou cidade com regra específica, a plataforma deve pedir revisão jurídica/fiscal.

---

### 2.5 Defesa do Consumidor

Fonte oficial:

- Planalto — Código de Defesa do Consumidor, Lei nº 8.078/1990: https://www.planalto.gov.br/ccivil_03/leis/l8078compilado.htm

Relevância para a plataforma:

- Reviews ruins, reembolsos, propaganda enganosa, anúncio impreciso, falha de serviço, insegurança e limpeza inadequada podem se transformar em risco consumerista.
- O produto deve manter evidências de anúncio, comunicação, check-in, fotos de vistoria, manutenção e resposta a reclamações.

---

### 2.6 Tributos e reforma tributária

Fontes oficiais:

- Planalto — Lei Complementar nº 214/2025: https://www.planalto.gov.br/ccivil_03/leis/lcp/lcp214.htm
- Receita Federal: https://www.gov.br/receitafederal/pt-br

Relevância para a plataforma:

- A plataforma deve armazenar dados de receita, repasses, taxas, locação, eventual prestação de serviço, notas/documentos e enquadramento fiscal.
- A modelagem tributária deve ser modular porque pode variar por município, natureza da operação e evolução normativa.

---

## 3. Jurisprudência e decisões relevantes

### 3.1 STJ — Airbnb e condomínios residenciais

Fontes oficiais:

- STJ — portal oficial: https://www.stj.jus.br/
- STJ — consulta processual: https://processo.stj.jus.br/processo/pesquisa/

Referência para busca:

- REsp 1.819.075/RS — discussão sobre condomínio residencial e locação por plataforma.

Relevância para a plataforma:

- O produto deve tratar regras condominiais como fonte crítica.
- O sistema não deve presumir que todo condomínio residencial aceita aluguel de curta temporada.
- Deve haver campo específico para: convenção, regimento, assembleias, decisões internas, notificações e multas.

---

## 4. Benchmarks regulatórios internacionais

### 4.1 União Europeia — dados de locações de curta duração

Fonte oficial:

- EUR-Lex — Regulation (EU) 2024/1028: https://eur-lex.europa.eu/eli/reg/2024/1028/oj
- EUR-Lex — busca geral: https://eur-lex.europa.eu/

Relevância para a plataforma:

- Modelo de registro, compartilhamento de dados, número de registro, endereço, capacidade, tipo de unidade e dados operacionais.
- Serve como referência para um módulo regulatório que una anfitrião, unidade, anúncio, número de registro e autoridade competente.

Campos inspirados:

```text
registration_number
registration_status
registration_valid_until
host_identity_status
unit_address
unit_type
primary_residence
max_capacity
competent_authority
```

---

### 4.2 Nova York — short-term rental registration

Fontes oficiais:

- NYC Office of Special Enforcement — Registration Law: https://www.nyc.gov/site/specialenforcement/registration-law/registration.page
- NYC Office of Special Enforcement — Short-Term Rental Registration: https://www.nyc.gov/site/specialenforcement/registration-law/short-term-rental-registration.page
- NYC Office of Special Enforcement — Prohibited Buildings List: https://www.nyc.gov/site/specialenforcement/registration-law/prohibited-buildings-list.page

Relevância para a plataforma:

- Exemplo forte de integração entre cadastro, número de registro, verificação de prédio proibido e obrigação de plataforma.
- Inspirar módulo municipal para cidades brasileiras quando houver regras locais.

---

## 5. Fontes operacionais complementares

### 5.1 Corpo de Bombeiros e segurança predial

Fontes oficiais variam por estado. Exemplos:

- Corpo de Bombeiros Militar do Estado de São Paulo: https://www.corpodebombeiros.sp.gov.br/
- Portal Gov.br — serviços estaduais e municipais: https://www.gov.br/

Relevância para a plataforma:

- Detectores, rotas de fuga, extintores, AVCB/CLCB quando aplicável, capacidade e segurança do imóvel.

### 5.2 Prefeituras e legislação municipal

Cada cidade pode ter regras próprias para alvará, cadastro, ISS, zoneamento, turismo, condomínio, silêncio urbano e fiscalização.

Campos mínimos:

```text
city
state
municipal_law_url
registration_required
license_required
tourism_tax_required
short_term_rental_limits
quiet_hours_law_url
inspection_authority
```

---

## 6. Política de uso das fontes no produto

Cada fonte cadastrada deve ter:

```text
source_id
source_name
source_type
jurisdiction
url
last_checked_at
responsible_reviewer
summary
rules_derived
confidence
requires_legal_review
```

Tipos de fonte:

```text
official_airbnb_policy
federal_law
municipal_law
court_decision
regulator_guidance
condo_rule
contract
academic_reference
news_or_clipping
manual_evidence
```

Critérios:

- Fonte oficial > fonte secundária.
- Fonte vigente > fonte histórica.
- Fonte local específica > regra genérica.
- Decisão automatizada nunca deve depender apenas de notícia, post ou dado raspado.
- Quando a regra vier de interpretação jurídica, marcar `requires_legal_review = true`.
