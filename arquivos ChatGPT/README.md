# Arquivos ChatGPT — Plataforma de Monitoramento Airbnb

Criado pelo ChatGPT em 03/06/2026 para consolidar a pesquisa, as fontes oficiais, os artigos, os clippings negativos, a legislação, a especificação de produto e o backlog técnico da plataforma de monitoramento Airbnb.

Esta pasta complementa a pasta já existente `material-complementar-criado-pelo-chatgpt`, mas organiza o material em um pacote mais direto para evolução do produto.

## Objetivo

Transformar o projeto `monitoramento-airbnb` em uma plataforma completa de monitoramento de aluguel de curta temporada, com foco em:

- conformidade com políticas oficiais do Airbnb;
- legislação brasileira aplicável;
- regras de condomínio e vizinhança;
- privacidade e LGPD;
- sensores permitidos e limites de monitoramento;
- prevenção de festas, ruído, lixo, uso irregular e reclamações;
- reputação, reviews, limpeza, manutenção e segurança;
- evidência auditável para cada alerta;
- inteligência de receita, ocupação e risco regulatório.

## Arquivos criados

1. `01-fontes-oficiais-e-legislacao.md`
   - Lista de fontes oficiais e legais que devem alimentar a plataforma.
   - Inclui Airbnb, legislação federal brasileira, jurisprudência, União Europeia, Nova York e ANPD.

2. `02-artigos-e-clippings-negativos.md`
   - Curadoria de artigos acadêmicos e eventos/ciclos negativos relevantes.
   - Mostra como transformar esses materiais em abas de conteúdo, alertas e regras de produto.

3. `03-especificacao-plataforma-monitoramento-airbnb.md`
   - Visão de produto, módulos, scores, alertas, diferenciais e regras de privacidade.

4. `04-roadmap-backlog-tecnico.md`
   - Roadmap por fases, épicos, histórias de usuário, critérios de aceite e próximos passos técnicos.

5. `05-matriz-alertas-regras-fontes.json`
   - Estrutura inicial em JSON para importar fontes, regras, alertas e componentes de score na plataforma.

## Princípios do produto

1. Monitorar a operação, não vigiar o hóspede.
2. Não gravar áudio.
3. Não permitir câmera interna.
4. Não usar reconhecimento facial.
5. Não tratar inferência como prova.
6. Todo alerta deve ter fonte, evidência, nível de confiança e ação recomendada.
7. Toda regra legal ou de política deve ter link oficial.
8. Decisões críticas devem exigir revisão humana.
9. Dados pessoais devem seguir minimização, finalidade, transparência, segurança e retenção limitada.
10. O produto deve ajudar anfitriões, administradores, condomínios e vizinhos a resolver problemas antes de virarem multa, suspensão, processo ou review negativo.

## Nota jurídica

Este material é uma curadoria técnica e estratégica. Ele não substitui parecer jurídico, análise local de legislação municipal ou avaliação final de advogado. Antes de automatizar decisões, publicar conteúdo jurídico ou aplicar sanções, conferir a redação vigente das normas oficiais e as regras específicas de cada cidade, condomínio e contrato.
