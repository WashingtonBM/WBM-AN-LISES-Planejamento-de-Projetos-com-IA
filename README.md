# 🧭 WBM Planner AI — Assistente Estratégico de Planejamento e Execução

> **Projeto final | Trilha: Planejamento de Projetos com IA**  
> **Autor:** Washington Brito ([@WashingtonBM](https://github.com/WashingtonBM)) — *WBM Análises*  
> **Status:** estrutura operacional criada no Notion; arquivos e modelos disponíveis neste repositório.

O WBM Planner AI transforma objetivos vagos em planos de execução realistas. No Notion, o sistema já conta com quatro bases relacionais e cinco Skills reutilizáveis para definir metas SMART, decompor entregáveis, planejar a rotina, antecipar obstáculos e revisar o progresso.

## 🔗 Acesso e downloads

- **Abrir o Planner no Notion:** [WBM Planner AI](https://app.notion.com/p/42134e17d856803d8dbae7c7bebfc5ef). O acesso depende das permissões da sua conta no workspace.
- **Baixar todos os arquivos do repositório (.zip):** [Download do projeto](https://github.com/WashingtonBM/WBM-AN-LISES-Planejamento-de-Projetos-com-IA/archive/refs/heads/main.zip).
- **Ver a estrutura e relações do Notion:** [docs/estrutura-notion.md](docs/estrutura-notion.md).

### Arquivos para download

**Skills (Markdown):**
- [WBM-01 — Clarificador SMART](docs/skills/WBM-01-Clarificador-SMART.md)
- [WBM-02 — Plano de Ação](docs/skills/WBM-02-Plano-de-Acao.md)
- [WBM-03 — Alocador de Rotina](docs/skills/WBM-03-Alocador-de-Rotina.md)
- [WBM-04 — Prevenção de Obstáculos](docs/skills/WBM-04-Prevencao-de-Obstaculos.md)
- [WBM-05 — Revisão Semanal](docs/skills/WBM-05-Revisao-Semanal.md)

**Modelos CSV para preencher e importar:**
- [Objetivos](templates/objetivos.csv)
- [Plano de Ação](templates/plano-de-acao.csv)
- [Rotina Semanal](templates/rotina-semanal.csv)
- [Obstáculos e Contingência](templates/obstaculos-contingencia.csv)

> Os CSVs são modelos de dados. Relações entre bases precisam ser conectadas no Notion após a importação; um CSV não cria relações automaticamente.

## 🎯 Problema e proposta

Pessoas e pequenos empreendedores podem travar na execução por causa de metas vagas e cronogramas que ignoram a rotina real. O WBM Planner AI atua como um **arquiteto de execução**: conecta objetivos, tarefas, capacidade semanal e riscos, preserva 20% de margem para imprevistos e permite recalcular o plano sem julgamentos.

## 🛠️ Arquitetura e estado atual

| Componente | Estado | Função |
| --- | --- | --- |
| **Notion** | Implementado | Quatro bases relacionais, cinco Skills e rollup de progresso por tarefa concluída. |
| **Skills do Notion AI** | Implementadas | Clarificação SMART, decomposição do plano, alocação semanal, contingências e revisão. |
| **ChatGPT/GPT personalizado** | Não configurado neste escopo | Pode usar as instruções dos arquivos em `docs/skills/`; a integração automática é uma evolução opcional. |
| **Google Agenda / Make** | Não configurado | Próxima evolução possível para lembretes dos blocos de foco. |

## 🗄️ Modelo de dados do Notion

1. **🎯 Objetivos (Master):** nome, categoria, critério SMART, prazo, status e progresso. O progresso é calculado como percentual de tarefas concluídas relacionadas.
2. **⚡ Plano de Ação (Tarefas):** ação/entregável, objetivo pai, fase, estimativa em horas, prioridade Eisenhower, checkbox de conclusão e relação com blocos semanais.
3. **📅 Rotina & Alocação Semanal:** bloco de foco, dia, horário, capacidade em horas e tarefas vinculadas.
4. **🛡️ Obstáculos & Contingência:** risco, objetivo afetado, probabilidade, gatilho “Se...” e plano “Então...”.

Relações: **Objetivos ↔ Tarefas**, **Objetivos ↔ Riscos** e **Blocos Semanais ↔ Tarefas**. Veja os detalhes em [docs/estrutura-notion.md](docs/estrutura-notion.md).

## 🧠 As cinco habilidades

- **WBM-01 — Clarificador SMART:** pergunta pelo resultado mensurável, prazo, horas disponíveis e recursos antes de planejar.
- **WBM-02 — Plano de Ação:** divide o objetivo aprovado em fases e tarefas de até duas horas.
- **WBM-03 — Alocador de Rotina:** agenda somente dentro dos horários informados, usando até 80% da capacidade.
- **WBM-04 — Prevenção de Obstáculos:** registra até três riscos com gatilhos e respostas “Se/Então”.
- **WBM-05 — Revisão Semanal:** calcula a execução, identifica atrasos sem julgamento e seleciona prioridades para a próxima semana.

Os arquivos completos estão em [`docs/skills/`](docs/skills/).

## 🧪 Demonstração — caso fictício

**Café & Grão:** Carla, proprietária de uma cafeteria fictícia, quer criar em 30 dias um dashboard de fluxo de caixa e margem por produto, dedicando quatro horas semanais e usando dados dos últimos três meses. O plano reserva no máximo 3,2 horas semanais para tarefas e mantém 48 minutos como margem.

Este caso é apenas demonstrativo e **não foi inserido como dado real** nas bases do Notion.

## 🚀 Próximos passos

- Inserir objetivos e disponibilidade reais no Planner.
- Adicionar capturas de tela com dados fictícios à pasta `assets/`.
- Opcionalmente configurar um GPT personalizado ou automação de lembretes via Make/Google Agenda.

---

*WBM Análises — planejamento realista, execução consistente.*
