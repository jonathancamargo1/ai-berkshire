---
name: earnings-team
description: "AI Berkshire skill: 财报精读团队：四大师并行解读 + 公众号发布. Source: skills/earnings-team.md."
---

## Nota do adaptador Codex

Esta habilidade é gerada a partir de `skills/earnings-team.md` para que usuários de Claude Code e Codex compartilhem um fluxo de trabalho canônico.

- Trate `$ARGUMENTS` como o pedido do usuário na thread atual do Codex.
- Quando a fonte menciona superfícies somente do Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca na web quando necessário, comandos shell para ferramentas locais e edições normais de arquivo para arquivos do workspace.
- Use ferramentas de projeto compartilhado de `tools/` neste repositório. Prefira executar comandos da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje.

# Equipe de Leitura Cuidadosa de Relatórios Financeiros: Quatro Mestres em Paralelo + Publicação em Conta Pública

Realizar análise de leitura cuidadosa de relatório financeiro em equipe para `$ARGUMENTS`. Quatro mestres leem relatórios financeiros em paralelo, o editor aperfeiçoa a redação, avaliadores de leitores garantem qualidade e produzem artigos de conta pública diretamente publicáveis.

**Formatos de entrada suportados**: `nome da empresa trimestre`, por exemplo: `Tencent 2025Q4`, `PDD 2025 relatório anual`, `Meituan mais recente`

## Filosofia de Design

Uma análise boa de relatório financeiro resolve dois problemas:
1. **Você mesmo consegue entender o futuro** — requer pesquisa profunda com quatro perspectivas diferentes
2. **Leitores conseguem entender o valor** — requer edição e revisão de qualidade da perspectiva do leitor

O fluxo desta Habilidade é dividido em três fases:
- **Fase 1·Pesquisa**: Quatro mestres leem cuidadosamente o relatório financeiro em paralelo (Duan Yongping vê a essência do negócio, Buffett avalia qualidade financeira, Munger lê mudanças competitivas, Li Lu caça sinais de risco)
- **Fase 2·Síntese**: Team Lead sintetiza quatro perspectivas, produz rascunho do relatório de pesquisa
- **Fase 3·Publicação**: Editor Agent reescreve como artigo de conta pública + Reader Review Agent apresenta sugestões de modificação → Team Lead redação final