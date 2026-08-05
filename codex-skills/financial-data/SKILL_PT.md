---
name: financial-data
description: "AI Berkshire skill: Obtenção de dados financeiros e padrão de verificação cruzada. Source: skills/financial-data.md."
---

## Nota do adaptador Codex

Esta skill é gerada a partir de `skills/financial-data.md` para que usuários de Claude Code e Codex compartilhem um fluxo de trabalho canonical.

- Trate `$ARGUMENTS` como o pedido do usuário no thread Codex atual.
- Quando a fonte mencionada superfícies exclusivas do Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca web quando necessário, comandos de shell para ferramentas locais e edições normais de arquivo para arquivos de workspace.
- Use ferramentas de projeto compartilhadas de `tools/` neste repositório. Prefira executar comandos a partir da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`; se o thread atual começar fora do repositório, localize primeiro o caminho do checkout real em vez de assumir um caminho fixo de diretório home.
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje; trate como a linha de base para dados "mais recentes" e declare a data de corte dos dados no cabeçalho do relatório. Nunca assuma a data atual a partir dos dados de treinamento.
- Preserve as regras de qualidade de pesquisa de `AGENTS.md`: verificação cruzada de dados financeiros, use ferramentas de aritmética exata para avaliação/matemática e rotule claramente a incerteza e as lacunas de origem.

# Obtenção de Dados Financeiros e Padrão de Verificação Cruzada

Este padrão se aplica a toda pesquisa envolvendo dados financeiros corporativos. **Cada dado-chave deve vir de duas fontes independentes, disparidade >1% deve ser marcada.**

---

## Prioridade de fonte de dados

### EUA (PDD, Tencent ADR, NetEase ADR etc.)

| Prioridade | Fonte | URL | Método de obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **macrotrends** | macrotrends.net/stocks/charts/{ticker} | Acesso direto, sem registro necessário |
| 2 (Secundária) | **stockanalysis** | stockanalysis.com/stocks/{ticker}/financials | Acesso direto, sem registro necessário |
| Original primária | SEC EDGAR | sec.gov/cgi-bin/browse-edgar | Texto 10-K / 10-Q original |

### Hong Kong (Tencent0700, NetEase9999, Meituan3690 etc.)

| Prioridade | Fonte | URL | Método de obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **aastocks** | aastocks.com/tc/stocks/analysis/company-fundamental | Acesso direto |
| 2 (Secundária) | **macrotrends** (código ADR) | Tencent use TCEHY, NetEase use NTES | Acesso direto |
| Original primária | HKEX Disclosure | hkexnews.hk | Relatório anual PDF |

### China A-share (37 Interaction, Gibit etc.)

| Prioridade | Fonte | URL | Método de obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **Eastmoney** | eastmoney.com → buscar código ação → tabela financeira | Acesso direto |
| 2 (Secundária) | **CNINFO** | cninfo.com.cn | Relatório original anual/trimestral PDF |

---

## Padrão de execução

### Primeira etapa: Obtenha dados

Para cada indicador financeiro (receita, lucro líquido, margem bruta, fluxo caixa operacional, taxa alavancagem etc.), obtenha separadamente de **fonte 1** e **fonte 2**.

### Segunda etapa: Cálculo de disparidade e marcação

```
Taxa disparidade = |Valor fonte 1 - Valor fonte 2| / Valor fonte 1 × 100%
```

| Disparidade | Método de tratamento |
|------|----------|
| ≤ 1% | ✅ Consistente, use valor fonte 1, marque ambas fontes |
| 1% ~ 5% | ⚠️ Marque "dados têm disparidade", anote ambos valores, explique possível razão (taxa cambial/metodologia contábil) |
| > 5% | ❌ Marque "dados têm disparidade importante", MUST verificar relatório financeiro original, não pode usar diretamente |

### Terceira etapa: Formato de apresentação de dados

Cada dado-chave deve ser marcado conforme formato abaixo:

```
Receita: 123,9 bilhões de yuan ✅
  - macrotrends: 124,1 bilhões de yuan
  - stockanalysis: 123,7 bilhões de yuan
  - Disparidade: 0,3%
```

Exemplo de disparidade:
```
Lucro líquido: 24,5 bilhões de yuan ⚠️ Dados têm disparidade
  - macrotrends: 24,5 bilhões de yuan (GAAP)
  - stockanalysis: 27,8 bilhões de yuan (Non-GAAP)
  - Disparidade: 13,5% — Razão: Metodologia contábil diferente (GAAP vs Non-GAAP)
```

---

## Razões comuns de disparidade (não é necessariamente erro de dados)

| Razão | Explicação |
|------|------|
| GAAP vs Non-GAAP | Mais comum, especialmente em dados de lucro |
| Conversão cambial | Diferença no ponto temporal de conversão Yuan/HKD/USD |
| Definição de ano fiscal | Ano civil vs ano fiscal (ex: Apple ano fiscal termina outubro) |
| Metodologia de consolidação | Se inclui direitos de acionista minoritário |
| Atraso de atualização de dados | Plataforma ainda não atualizou último período financeiro |

---

## Regras especiais

1. **Empresa não listada** (miHoYo, Lilith etc.): Quando há apenas uma fonte de dados primária, marque dado com `[Estimado]`, não execute verificação cruzada
2. **Dados trimestrais vs dados anuais**: Prefira dados anuais para verificação cruzada, dados trimestrais em algumas fontes podem ter atraso
3. **Relatório financeiro original tem prioridade**: Se ambas fontes diferem do relatório original (10-K/relatório anual PDF), use relatório original como padrão, marque erro de fonte

---

## Referência rápida

| Cenário | Fonte principal | Fonte de backup |
|------|---------|----------|
| PDD / Pinduoduo | macrotrends.net/stocks/charts/PDD | stockanalysis.com/stocks/pdd |
| Tencent | macrotrends.net/stocks/charts/TCEHY | aastocks (0700.HK) |
| NetEase | macrotrends.net/stocks/charts/NTES | aastocks (9999.HK) |
| 37 Interaction | eastmoney.com (002555) | cninfo.com.cn |
| Gibit | eastmoney.com (603444) | cninfo.com.cn |
| Nintendo | macrotrends.net/stocks/charts/NTDOY | stockanalysis.com/stocks/ntdoy |
| Capcom | macrotrends (CCOEY) | stockanalysis (CCOEY) |