# 🧭 WBM Planner AI — Assistente Estratégico de Planejamento e Execução

> **Projeto final | Trilha: Planejamento de Projetos com IA**  
> **Autor:** Washington Brito ([@WashingtonBM](https://github.com/WashingtonBM)) — *WBM Análises*

O WBM Planner AI transforma objetivos vagos em planos de execução realistas. A proposta combina bases relacionais no Notion com cinco habilidades reutilizáveis para definir metas SMART, decompor entregáveis, planejar a rotina, antecipar obstáculos e revisar o progresso.

## 🎯 Problema e proposta

Pessoas e pequenos empreendedores podem ter dificuldade para executar projetos por causa de metas pouco específicas e cronogramas que não consideram a rotina real. O WBM Planner AI atua como um **arquiteto de execução**: conecta objetivos, tarefas, disponibilidade semanal e riscos, mantendo uma margem para imprevistos e permitindo recalcular o plano sem julgamentos.

## 🛠️ Arquitetura

| Ferramenta | Recursos previstos | Papel no projeto |
| --- | --- | --- |
| **Notion** | Quatro bases relacionais; relações, fórmulas e rollups; habilidades reutilizáveis | Centralizar o planejamento e acompanhar a relação entre tarefas e objetivos. |
| **ChatGPT** | Instruções personalizadas ou GPT; conector com Notion ou transferência estruturada | Fazer perguntas de esclarecimento, avaliar a viabilidade do plano e organizar os dados para o Notion. |

> A integração pode ser feita por conector, quando disponível, ou por transferência estruturada. A arquitetura não pressupõe uma automação já configurada.

## 🗄️ Bases de dados do Notion

As quatro bases formam um fluxo rastreável do objetivo até a execução e a contingência.

### 1. 🎯 Objetivos (Master)

| Propriedade | Tipo sugerido | Uso |
| --- | --- | --- |
| Nome do Objetivo | Título | Identificar o objetivo. |
| Categoria | Seleção | Estudo, carreira ou negócio. |
| Critério SMART | Texto | Registrar o objetivo específico e mensurável. |
| Prazo Final | Data | Definir o limite de conclusão. |
| Progresso | Rollup | Calcular o avanço a partir das tarefas relacionadas. |
| Status | Status/seleção | Não iniciado, em andamento ou concluído. |

### 2. ⚡ Plano de Ação (Tarefas)

| Propriedade | Tipo sugerido | Uso |
| --- | --- | --- |
| Ação / Entregável | Título | Descrever uma próxima ação concreta. |
| Objetivo Pai | Relação | Vincular a tarefa ao objetivo correspondente. |
| Fase / Sprint | Seleção | Agrupar tarefas em etapas. |
| Tempo Estimado (h) | Número | Estimar a duração da tarefa. |
| Prioridade | Seleção | Classificar pela matriz de Eisenhower. |
| Concluído | Checkbox | Registrar a conclusão. |

### 3. 📅 Rotina & Alocação Semanal

| Propriedade | Tipo sugerido | Uso |
| --- | --- | --- |
| Bloco de Foco | Título | Nomear o bloco de trabalho. |
| Dia da Semana | Seleção | Informar o dia disponível. |
| Turno / Horário | Texto | Registrar o horário livre. |
| Capacidade (h) | Número | Informar a capacidade do bloco. |
| Tarefas Vinculadas | Relação | Relacionar blocos às tarefas do plano de ação. |

### 4. 🛡️ Obstáculos & Contingência (Matriz Se-Então)

| Propriedade | Tipo sugerido | Uso |
| --- | --- | --- |
| Risco Mapeado | Título | Nomear o possível obstáculo. |
| Objetivo Afetado | Relação | Vincular o risco ao objetivo. |
| Probabilidade | Seleção | Alta, média ou baixa. |
| Gatilho (Se...) | Texto | Descrever quando o risco se manifesta. |
| Plano B (Então...) | Texto | Definir uma resposta mínima e prática. |

## 🧠 Habilidades reutilizáveis

As habilidades abaixo podem ser usadas como instruções no ChatGPT ou no Notion AI. Cada uma cobre uma etapa específica do ciclo de planejamento.

### 🔍 [WBM-01] Clarificador de Objetivos (SMART)

**Quando usar:** ao receber uma ideia ou meta ainda vaga.  
**Função:** esclarecer o resultado mensurável, o prazo, a capacidade semanal e os recursos ou conhecimentos disponíveis antes de montar o plano.

```text
Atue como um consultor de planejamento estratégico. Quando o usuário apresentar um objetivo vago, não gere um plano de ação ainda. Faça no máximo 4 perguntas objetivas para descobrir: (1) qual é o entregável final mensurável; (2) qual é o prazo limite; (3) quantas horas reais por semana estão disponíveis; e (4) qual é o nível atual de conhecimento e quais recursos estão disponíveis. Após as respostas, sintetize o objetivo no formato SMART em uma tabela curta.
```

### 🏗️ [WBM-02] Engenheiro de Plano de Ação

**Quando usar:** depois que o objetivo SMART for aprovado.  
**Função:** dividir o objetivo em fases e microtarefas executáveis de até duas horas.

```text
Com base no objetivo SMART definido, divida o projeto em 3 a 4 fases lógicas. Para cada fase, liste microtarefas práticas começando com um verbo no infinitivo. Nenhuma tarefa pode ter duração estimada maior que 2 horas; se for maior, divida-a. Entregue o resultado em uma tabela com as colunas: Fase | Tarefa | Tempo Estimado (h) | Prioridade.
```

### ⏱️ [WBM-03] Alocador de Rotina Realista

**Quando usar:** ao encaixar as tarefas na disponibilidade semanal.  
**Função:** distribuir as tarefas nos blocos livres, usando no máximo 80% da capacidade informada e preservando 20% para imprevistos.

```text
Receba a lista de tarefas do plano de ação e os horários livres informados pelo usuário. Distribua as tarefas da Fase 1 nos blocos semanais disponíveis. Utilize no máximo 80% da capacidade de horas informada, deixando 20% de margem. Se o volume não couber no prazo desejado, alerte o usuário e sugira reduzir o escopo ou estender o prazo.
```

### 🛡️ [WBM-04] Antecipador de Obstáculos (Se-Então)

**Quando usar:** antes de iniciar a primeira semana de execução.  
**Função:** prever gargalos e preparar respostas simples para preservar o andamento do projeto.

```text
Analise o objetivo e a rotina do usuário e identifique os 3 obstáculos comportamentais ou técnicos mais prováveis. Para cada um, escreva uma regra no formato: “SE [gatilho do problema acontecer], ENTÃO [ação mínima de 15 minutos para manter o progresso]”. Considere exemplos como cansaço após o trabalho, falta de dados ou imprevistos familiares.
```

### 📊 [WBM-05] Auditor de Progresso Semanal

**Quando usar:** na revisão semanal, no domingo ou na segunda-feira.  
**Função:** avaliar o que foi planejado e concluído e reorganizar as prioridades sem julgamentos.

```text
Analise o status das tarefas da semana passada fornecido pelo usuário e calcule a taxa de execução (%). Reconheça objetivamente o que foi entregue, identifique padrões por trás do que atrasou sem julgamentos e reorganize as tarefas pendentes na agenda da próxima semana. Destaque as 3 principais prioridades inegociáveis.
```

## 🧪 Demonstração — estudo de caso fictício

> **Este cenário é fictício e foi elaborado apenas para demonstrar o fluxo.**

**Cenário:** Carla Mendes é proprietária da cafeteria artesanal *Café & Grão*. Ela quer criar um dashboard financeiro de fluxo de caixa e margem por produto para separar as contas pessoais das contas da empresa.

### 1. Clarificar o objetivo

**Entrada:** “Quero organizar as finanças da minha cafeteria usando planilhas e gráficos.”

**Objetivo SMART de exemplo:** construir e validar um dashboard de fluxo de caixa diário e margem de contribuição no Excel ou Power BI em até 30 dias, dedicando quatro horas semanais e usando extratos bancários e registros do ponto de venda dos últimos três meses.

### 2. Gerar o plano de ação

| Fase | Tarefa | Tempo estimado | Prioridade |
| --- | --- | ---: | --- |
| 1. Saneamento | Exportar extratos bancários e vendas do PDV dos últimos 90 dias | 1,5 h | Alta |
| 1. Saneamento | Separar despesas pessoais dos custos fixos e variáveis da loja | 2 h | Alta |
| 2. Modelagem | Estruturar a tabela de movimentações e um plano de contas simples | 2 h | Alta |
| 2. Modelagem | Calcular o CMV dos 10 itens mais vendidos | 2 h | Média |
| 3. Visualização | Criar indicadores de faturamento, lucro líquido e ticket médio | 1,5 h | Média |

### 3. Alocar a rotina

Carla tem quatro horas livres por semana: terça-feira, das 19h às 21h, e sábado, das 8h às 10h. Aplicando o limite de 80%, são **3,2 horas úteis planejáveis** e **48 minutos de margem**.

- **Terça, 19h–20h30:** exportar extratos bancários e vendas do PDV (1,5 h).
- **Sábado, 8h–9h42:** iniciar a separação das despesas pessoais e dos custos da loja (1,7 h); concluir o restante em outro bloco.
- **Margem preservada:** 48 minutos para imprevistos ou fechamento de caixa mais demorado.

### 4. Antecipar obstáculos

1. **SE** o movimento da cafeteria atrasar o fechamento na terça e restarem apenas 30 minutos, **ENTÃO** baixar o extrato bancário em CSV e deixar a categorização para sábado.
2. **SE** faltar uma nota fiscal de fornecedor antigo, **ENTÃO** registrar o valor como “Ajuste Histórico” e continuar a organização, sinalizando o dado para validação posterior.
3. **SE** surgir um imprevisto no bloco de sábado, **ENTÃO** fazer ao menos 15 minutos de organização dos arquivos para manter o projeto em andamento.

## 📸 Evidências visuais

Adicione capturas de tela com dados fictícios à pasta `assets/` antes da publicação final. Revise as imagens para não expor e-mails, informações pessoais ou projetos reais.

- `assets/01-planner-notion-geral.png` — visão geral do planner.
- `assets/02-bases-relacionais.png` — bases de dados e relações.
- `assets/03-execucao-habilidade.png` — exemplo de execução de uma habilidade.

## 🚀 Próximas evoluções

- Conectar a base **Rotina & Alocação Semanal** ao Google Agenda via Make ou n8n para enviar lembretes nos blocos de foco.
- Criar a **[WBM-06] Estimador de ROI**, voltada a objetivos de negócio e projetos de análise de dados.

## ✅ Checklist para publicação

- [ ] Confirmar o nome do repositório e manter o README atualizado.
- [ ] Adicionar à pasta `assets/` duas ou três capturas de tela do ambiente fictício.
- [ ] Conferir que as capturas não exibem dados pessoais ou reais.
- [ ] Revisar as instruções e adaptar as bases às necessidades do usuário.

---

*WBM Análises — planejamento realista, execução consistente.*
