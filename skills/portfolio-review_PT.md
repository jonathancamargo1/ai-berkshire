# Gestão Carteira: De "Pesquisar Empresa" Para "Gerenciar Carteira"

Execute auditoria carteira investimento e otimização para $ARGUMENTS.

**Formatos entrada suportado**:
- Carteira posição, ex: `Tencent 30%, Meituan 20%, Maotai 20%, Nvidia 15%, Caixa 15%`
- Ou: `Tencent 500 ações @480 Hong Kong, Meituan 1000 ações @130 Hong Kong, ...`
- Ou: `Minha carteira` (se arquivo carteira `reports/portfolio-latest.md` já salvo)

&gt; "Diversificação é proteção contra ignorância. Se sabe que está fazendo, diversificação não é significativo." —— Buffett
&gt;
&gt; "Nos meus anos vivi, verdadeiras boas oportunidades investimento, dez dedos conseguem contar." —— Li Lu

## Filosofia Design

Pesquisar empresa é apenas metade investimento. Outra metade é **decisão nível carteira**:
- Compra quanto? (Posição)
- Usa que dinheiro compra? (Fonte capital)
- Conflita com posição atual? (Correlação)
- Carteira ótimo que tipo? (Custo oportunidade)

Buffett nunca observa isoladamente — sempre está pensando "essa é melhor coisa que conseguo fazer?".

## Fluxo Execução

### Passo Um: Analisa Carteira

De entrada analisa posição atual, padroniza como formato abaixo:

| Alvo | Código | Quantidade | Preço Custo | Preço Atual | Valor Mercado | Proporção | L/P |
|------|------|--------|-------|------|------|------|------|

Se entrada só tem proporção sem montante, análise por proporção é ok.

Verifica se existe arquivo carteira existente (`reports/portfolio-latest.md`).

### Passo Dois: Pega Dados Mais Recentes

Use Task tool inicia Agent background, por WebSearch paralela pega cada posição:
1. Preço ação atual e indicadores avaliação (PE, PB, taxa dividendo)
2. Mudança financeiro trimestral mais recente
3. Evento recente
4. Expectativa analista consenso

Cada posição use `tools/financial_rigor.py verify-valuation` validate dados. Marca riqueza informação (A/B/C).

### Passo Três: Health Check Posição Único

Cada posição faz rápido health check:

| Alvo | PE Atual | Lógica Mudou? | Saúde Tese | Recomendação |
|------|:------:|:--------------:|:---------:|----------|
| Tencent | 18x | Não | 8/10 | Razoável |
| Meituan | 25x | Sim | 6/10 | Levemente alto |

Cada posição responde:
- [ ] Se hoje sem posição, ainda compraria?
- [ ] Se amanhã sem trocar, segura 5 anos?
- [ ] Tese compra ainda intacta?

**Dyo Yupeng**: "Se não quer 10 anos, um dia também não."

### Passo Quatro: Análise Nível Carteira

#### 4.1 Concentração

| Indicador | Valor Atual | Intervalo Recomendado |
|------|-------|----------|
| Maior posição | | &lt;40% |
| 3 maiores | | 50-80% |
| Total quantidade | | 5-15 |
| Proporção caixa | | 10-30% |

**Li Lu**: 3-5 posições núcleo, &gt;80% em 3 primeiras. Mas exige pesquisa profunda.

#### 4.2 Correlação

| Posição A | Posição B | Tipo | Risco |
|-------|-------|---------|------|
| Tencent | Kuaishou | Internet China | Regulação conjunta |
| Nvidia | TSMC | Cadeia IA | Capex síncrono |
| Meituan | Pinduoduo | Consumo China | Macro síncrono |

#### 4.3 Custo Oportunidade

Classifica por expectativa retorno anualizado:

| Rank | Alvo | Proporção | Retorno Esperado | Certeza | Retorno×Certeza |
|:----:|------|:-------:|:----------:|:------:|:--------------:|
| 1 | | | | | |

**Pergunta-chave**: Posição último ranking, retorno esperado &gt; caixa (4%)? Se não, vender.

#### 4.4 Teste Pressão

| Cenário | Suposição | Impacto |
|------|------|----------|
| Recessão | Lucro -20-30% | |
| Conflito China-EUA | Desconto 50% | |
| Taxa Sobe | 10-ano → 6% | |
| Bolha Tech | PE -40% | |

### Passo Cinco: Recomendação

#### 5.1 Troca Posição

| Ação | Alvo | Atual | Recomendado | Razão |
|------|------|:-------:|:-------:|----------|
| Aumentar | | | | |
| Reduzir | | | | |
| Liquidar | | | | |
| Novo | | | | |
| Não mexe | | | | |

#### 5.2 Alternativas

Use `/industry-research` ou `/investment-checklist` não recomenda stock direto aqui.

#### 5.3 Caixa

| Atual | Recomendado | Razão |
|:----------:|:----------:|----------|

**Buffett**: $382B caixa hoje, &gt;25% do total.

### Passo Seis: Relatório

#### Estrutura

```
Um. Resumo (Tabela+Pizza)
Dois. Health Posições
Três. Análise
   - Concentração
   - Correlação
   - Custo Oportunidade
   - Stress Test
Quatro. Recomendações
Cinco. Próxima Auditoria
```

#### Conclusão

1. **Saúde**: Excelente/Bom/Ajuste/Grave
2. **Ação Principal**: Aumentar X/Reduzir Y/Não Mexe
3. **Risco Máximo**

### Passo Sete: Salva

Escreve `reports/portfolio-latest.md`, inclui:
- Tabela posição
- Data auditoria
- Histórico troca
- Próxima auditoria