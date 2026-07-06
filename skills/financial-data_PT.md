# Norma de Aquisição e Validação Cruzada de Dados Financeiros

Esta norma se aplica a todas as pesquisas envolvendo dados financeiros empresariais. **Cada dado principal deve vir de duas fontes independentes, desvios >1% devem ser marcados.**

---

## Hierarquia de Fontes de Dados

### Ações dos EUA (PDD, ADR da Tencent, ADR da NetEase etc.)

| Prioridade | Fonte | URL | Método de Obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **macrotrends** | macrotrends.net/stocks/charts/{ticker} | Acesso direto, sem cadastro |
| 2 (Secundária) | **stockanalysis** | stockanalysis.com/stocks/{ticker}/financials | Acesso direto, sem cadastro |
| Original de Primeira Mão | SEC EDGAR | sec.gov/cgi-bin/browse-edgar | 10-K / 10-Q texto original |

### Ações de Hong Kong (Tencent 0700, NetEase 9999, Meituan 3690 etc.)

| Prioridade | Fonte | URL | Método de Obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **aastocks** | aastocks.com/tc/stocks/analysis/company-fundamental | Acesso direto |
| 2 (Secundária) | **macrotrends** (código ADR) | Tencent usa TCEHY, NetEase usa NTES | Acesso direto |
| Original de Primeira Mão | HKEx Disclosure | hkexnews.hk | PDF de Relatório Anual |

### Ações A da China (37 Interactive, Gibbit etc.)

| Prioridade | Fonte | URL | Método de Obtenção |
|--------|------|-----|----------|
| 1 (Principal) | **Eastmoney** | eastmoney.com → procurar código → Tabelas Financeiras | Acesso direto |
| 2 (Secundária) | **Juchai** | cninfo.com.cn | PDF original de Anual/Trimestral |

---

## Norma de Execução

### Primeira Etapa: Obter Dados

Para cada indicador financeiro (receita, lucro líquido, margem bruta, fluxo operacional, taxa de alavancagem etc.), obter dados **da fonte 1** e **da fonte 2** separadamente.

### Segunda Etapa: Cálculo de Desvio e Marcação

```
Taxa de Desvio = |Valor Fonte 1 - Valor Fonte 2| / Valor Fonte 1 × 100%
```

| Desvio | Método de Processamento |
|------|----------|
| ≤ 1% | ✅ Consistente, usar valor da fonte 1, marcar ambas as fontes |
| 1% ~ 5% | ⚠️ Marcar "dados com variação", anotar ambos os valores, explicar possível causa (taxa de câmbio/método contábil) |
| > 5% | ❌ Marcar "dados com grande variação", deve-se verificar relatório original antes de usar |

### Terceira Etapa: Formato de Apresentação de Dados

Cada dado principal deve ser anotado assim:

```
Receita: R$1.239 bilhões ✅
  - macrotrends: R$1.241 bilhões
  - stockanalysis: R$1.237 bilhões
  - Desvio: 0,3%
```

Exemplo de Variação:
```
Lucro Líquido: R$245 bilhões ⚠️ Dados com Variação
  - macrotrends: R$245 bilhões (GAAP)
  - stockanalysis: R$278 bilhões (Non-GAAP)
  - Desvio: 13,5% — Razão: Método contábil diferente (GAAP vs Non-GAAP)
```

---

## Causas Comuns de Variação (Não Necessariamente Erros de Dados)

| Razão | Explicação |
|------|------|
| GAAP vs Non-GAAP | Mais comum, especialmente em dados de lucro |
| Conversão de Taxa de Câmbio | Hong Kong/RMB/USD diferentes datas |
| Definição de Ano Fiscal | Ano natural vs Ano fiscal (ex: Apple termina outubro) |
| Escopo de Consolidação | Inclui participação de minoritários? |
| Defasagem de Atualização | Plataforma ainda não atualizou período mais recente |

---

## Regras Especiais

1. **Empresas Não-Listadas** (miHoYo, Lilith etc.): Com apenas uma fonte de dados, marcar `[Estimado]` antes do dado, não executar validação cruzada
2. **Dados Trimestrais vs Anuais**: Preferir usar dados anuais para validação cruzada, dados trimestrais de algumas fontes podem ter defasagem
3. **Prioridade de Relatório Original**: Se ambas as fontes diferem do relatório original (10-K/Anual PDF), usar relatório original como correto, marcar erro da fonte

---

## Índice Rápido

| Cenário | Fonte Principal | Fonte de Backup |
|------|---------|----------|
| PDD / Pinduoduo | macrotrends.net/stocks/charts/PDD | stockanalysis.com/stocks/pdd |
| Tencent | macrotrends.net/stocks/charts/TCEHY | aastocks（0700.HK） |
| NetEase | macrotrends.net/stocks/charts/NTES | aastocks（9999.HK） |
| 37 Interactive | eastmoney.com（002555） | cninfo.com.cn |
| Gibbit | eastmoney.com（603444） | cninfo.com.cn |
| Nintendo | macrotrends.net/stocks/charts/NTDOY | stockanalysis.com/stocks/ntdoy |
| Capcom | macrotrends（CCOEY） | stockanalysis（CCOEY） |