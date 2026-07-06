# CLAUDE.md - Instruções e Arquitetura do Projeto AI Berkshire

## Visão Geral do Projeto

Coleção de Skills de pesquisa de investimento em valor baseada em Claude Code. Estrutura dos Quatro Mestres: Buffett, Munger, Tan Yongping, Li Lu.

**GitHub**: https://github.com/xbtlin/ai-berkshire

## Estrutura do Projeto

```
skills/          — Definições de Skills de pesquisa (.md)
tools/           — Ferramentas auxiliares (financial_rigor.py cálculo preciso)
reports/         — Saída de relatórios de pesquisa de investimento
assets/          — Recursos estáticos como imagens
codex-skills/    — Definições de Codex Skills
codex-prompts/   — Biblioteca de Codex Prompts
```

## Estrutura do Diretório de Relatórios

Todos os relatórios são organizados em pastas por **nome da empresa**, com todos os relatórios relacionados colocados na pasta correspondente.

## Princípios Fundamentais da Análise de Pesquisa de Investimento (Prioridade Máxima)

- **Objetivo, objetivo, objetivo** — Toda análise de pesquisa de investimento deve ser baseada em fatos e dados, proibindo especulação subjetiva
- Distinção rigorosa entre "fatos" e "opiniões": fatos são sustentados por dados, opiniões devem ser claramente marcadas
- **Não predefina posição**: não presuma tendência de alta ou baixa, apresente dados primeiro, depois deduza lógica, finalmente chegue a conclusões
- Proibido usar expressões subjetivas como "meu acho", "na minha opinião", etc.
- **Apresente ambos os lados**: cada julgamento central deve ser acompanhado de evidências contrárias
- Seja honesto sobre incertezas, diga "incerto" ou "dados insuficientes", não preencha com especulações

## Operações no GitHub

- Caminho de clonagem local: `~/ai-berkshire/`
- Repositório remoto: `https://github.com/xbtlin/ai-berkshire.git`
- Antes de enviar, execute `git pull --rebase origin main`
- Mensagem de commit em chinês, descrevendo claramente o que foi alterado