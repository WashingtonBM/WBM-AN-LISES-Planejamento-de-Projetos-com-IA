# Estrutura do WBM Planner AI no Notion

A página inicial do sistema é o [WBM Planner AI](https://app.notion.com/p/42134e17d856803d8dbae7c7bebfc5ef). O acesso depende das permissões do workspace.

## Bases e propriedades principais

### 🎯 Objetivos (Master)
- **Nome do Objetivo** — título.
- **Categoria** — Estudo, Carreira ou Negócio.
- **Critério SMART** — texto.
- **Prazo Final** — data.
- **Status** — Não Iniciado, Em Andamento ou Concluído.
- **Tarefas** — relação com Plano de Ação.
- **Riscos** — relação com Obstáculos & Contingência.
- **Progresso** — rollup de percentual das tarefas relacionadas marcadas como concluídas.

### ⚡ Plano de Ação (Tarefas)
- **Ação / Entregável** — título.
- **Objetivo Pai** — relação com Objetivos.
- **Fase / Sprint** — Fase 1 a Fase 4.
- **Tempo Estimado (h)** — número; mantenha cada tarefa em até duas horas.
- **Prioridade** — Fazer agora, Agendar, Delegar ou Eliminar (matriz Eisenhower).
- **Concluído** — checkbox usado pelo rollup de progresso.
- **Blocos Semanais** — relação com Rotina & Alocação Semanal.

### 📅 Rotina & Alocação Semanal
- **Bloco de Foco** — título.
- **Dia da Semana** — segunda-feira a domingo.
- **Turno / Horário** — texto.
- **Capacidade (h)** — número de horas disponíveis.
- **Tarefas Vinculadas** — relação com Plano de Ação.

### 🛡️ Obstáculos & Contingência
- **Risco Mapeado** — título.
- **Objetivo Afetado** — relação com Objetivos.
- **Probabilidade** — Alta, Média ou Baixa.
- **Gatilho (Se...)** — texto.
- **Plano B (Então...)** — texto.

## Fluxo de uso

1. Clarifique e aprove o objetivo SMART.
2. Decomponha em tarefas acionáveis; não estime tarefas acima de duas horas.
3. Registre horários reais e use até 80% da capacidade semanal, mantendo 20% de folga.
4. Vincule tarefas aos blocos de foco e riscos ao objetivo.
5. Atualize os checkboxes de conclusão; o rollup reflete o progresso.
6. Faça a revisão semanal e reorganize tarefas sem culpa.

## Importação de CSV

Os arquivos em `templates/` contêm cabeçalhos para preparar dados. Ao importar um CSV no Notion, confirme os tipos das propriedades e recrie as relações entre bases. CSV não transporta relações, fórmulas ou rollups; esses recursos já estão configurados nas bases criadas no workspace.
