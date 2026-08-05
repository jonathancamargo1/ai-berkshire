---
name: news-pulse
description: "公司新闻脉搏：股价异动时快速归因。用 4 个并行 Agent 侦察公司事件/监管政策/行业对手/市场情绪，产出'事件时间线 + 异动主因判断 + 是否触发论文重审'。"
---

## Nota do adaptador Codex

Esta habilidade é gerada a partir de `skills/news-pulse.md` para que usuários de Claude Code e Codex compartilhem um fluxo de trabalho canônico.

# Pulso de Notícias da Empresa: Atribuição Rápida de Anomalias de Preço de Ações

Realizar inspeção recente de notícias e atribuição de anomalias para `$ARGUMENTS`. **Esta não é pesquisa profunda, é resposta rápida de inteligência** — o objetivo é responder em 10 minutos: "O que aconteceu recentemente com esta empresa? A verdadeira causa da anomalia de preço é qual? Preciso reexaminar a tese de investimento?"

## Cenários Aplicáveis

- Ações em carteira/observação aumentam/diminuem drasticamente (linha gatilho geral: ±5% por dia, ±10% por semana)
- Anomalia de preço de ação após relatório financeiro, quer entender rapidamente o que o mercado está refletindo
- Ver manchete de notícia, mas não tem certeza se é ruído ou sinal verdadeiro
- **Não aplicável**: Pesquisa completa (usar `/investment-team`), leitura profunda de relatório (usar `/earnings-review`), rastreamento de tese de longo prazo (usar `/thesis-tracker`)