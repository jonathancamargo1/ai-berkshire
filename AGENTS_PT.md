# Biblioteca de AI Agents e Prompts

Este repositório contém múltiplos templates de Prompt otimizados e definições de AI Agent para uso em Claude Code e Codex.

## Agents Principais (19)

### Categoria Pesquisa de Investimento (7)

| Agent | Entrada | Saída | Tempo |
|-------|---------|-------|-------|
| `/investment-research` | Código da ação | Relatório estruturado de 12 dimensões | 8-12 minutos |
| `/investment-team` | Código da ação | Perspectiva dos 4 Mestres + resumo | 15-20 minutos |
| `/investment-checklist` | Código da ação | Checklist de 50 pontos | 4-6 minutos |
| `/thesis-tracker` | ID da empresa | Rastreamento contínuo da tese de investimento | Contínuo |
| `/earnings-review` | Transcrição de teleconferência de resultados | Análise de resultados (esperado vs real) | 3-5 minutos |
| `/management-deep-dive` | Código da ação | Análise profunda da gestão | 6-8 minutos |

E mais...

## Codex Prompts

No diretório `codex-prompts/`, são fornecidos templates de prompt que podem ser usados diretamente no Codex.

## Como Usar

### Em Claude Code

1. Instale skills: `bash scripts/install-claude-commands.sh`
2. Use o comando: `/investment-research PDD`

### Em Codex

1. Copie o prompt do diretório `codex-prompts/`
2. Cole no Codex
3. Modifique para o código da ação que você precisa

## Contribuir um Novo Prompt

Veja CONTRIBUTING.md