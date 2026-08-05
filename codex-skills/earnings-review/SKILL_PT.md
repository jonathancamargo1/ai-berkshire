---
name: earnings-review
description: "AI Berkshire skill: Leitura profunda de relatórios: interpretação profunda de fontes primárias. Source: skills/earnings-review.md."
---

## Nota do adaptador Codex

Esta skill é gerada a partir de `skills/earnings-review.md` para que usuários de Claude Code e Codex compartilhem um fluxo de trabalho canonical.

- Trate `$ARGUMENTS` como o pedido do usuário no thread Codex atual.
- Quando a fonte mencionada superfícies exclusivas do Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca web quando necessário, comandos de shell para ferramentas locais e edições normais de arquivo para arquivos de workspace.
- Use ferramentas de projeto compartilhadas de `tools/` neste repositório. Prefira executar comandos a partir da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`; se o thread atual começar fora do repositório, localize primeiro o caminho do checkout real em vez de assumir um caminho fixo de diretório home.
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje; trate como a linha de base para dados "mais recentes" e declare a data de corte dos dados no cabeçalho do relatório. Nunca assuma a data atual a partir dos dados de treinamento.
- Preserve as regras de qualidade de pesquisa de `AGENTS.md`: verificação cruzada de dados financeiros, use ferramentas de aritmética exata para avaliação/matemática e rotule claramente a incerteza e as lacunas de origem.

# Leitura Profunda de Relatórios: Interpretação Profunda de Fontes Primárias

Conducta análise de leitura profunda de relatórios para $ARGUMENTS.

**Formatos de entrada suportados**: `Nome da empresa trimestre`, por exemplo: `Tencent 2025Q4`, `PDD 2025 relatório anual`, `Meituan mais recente` (padrão lê período mais recente)

> "Nunca leio relatórios de vendedor, apenas leio relatórios financeiros originais." —— Li Lu
>
> "Leio 500 páginas por dia. Conhecimento se acumula assim, como juros compostos." —— Buffett

## Filosofia de Design

Maior parte das ferramentas AI de pesquisa depende de informação secundária (notícias, resumos de relatórios, sites de dados). Mas a habilidade central de Buffett e Li Lu é **ler fontes primárias** — relatórios anuais, trimestres, transcrições de chamadas de telefone.

Problema de informação secundária:
- Já foi selecionada — analistas apresentam dados de forma tendenciosa para apoiar sua visão
- Há atraso — quando terceiros terminam digestão, alpha desapareceu
- Falta contexto — "receita cresceu 15%" desvinculada de discussão sobre qualidade do crescimento

Esta Skill lê diretamente fontes primárias, focando no que Buffett e Li Lu realmente leriam.

## Processo de execução

### Pré-requisito: Avaliação de disponibilidade de material

| Nível | Características | Impacto |
|------|------|--------|
| Nível A | Obtém texto completo original (10-K/relatório anual/transcrição de chamada) | Executa todos os passos normalmente |
| Nível B | Obtém apenas parte original ou resumo de terceiro | Marque "fonte não original", reduz peso de análise de anexos |
| Nível C | Apenas notícias e resumo de site de dados | Foca em dados financeiros principais, pula análise de anexos, marque "fonte primária insuficiente" |

### Primeira etapa: Obtenha fontes primárias

Use ferramenta Task para iniciar múltiplos Agent **em paralelo** para obter materiais originais:

1. **Texto de relatório**: De página IR da empresa, SEC EDGAR (10-K/10-Q americana), HKEX Disclosure (HK), CNINFO (A-shares)
2. **Transcrição de chamada telefônica / gravação**: De Seeking Alpha, página IR da empresa, Xueqiu etc.
3. **Carta do gerenciador aos acionistas** (se houver relatório anual): Leia completamente
4. **Materiais de dia de investidor/analista** (se houver recentemente)

Se não conseguir obter texto completo original, use padrão de `skills/financial-data.md` para montar usando fontes de dados padrão (EUA: macrotrends+stockanalysis; HK: aastocks+macrotrends; A-share: Eastmoney+CNINFO), mas DEVE marcar "não original, de resumo de terceiro", e principais dados disparidade >1% DEVE marcar.

### Segunda etapa: Extração e verificação de dados financeiros principais

#### 2.1 Demonstração de resultados

| Indicador | Este período | Período anterior | Variação YoY | Orientação de gestão | Alcançou |
|------|------|------|---------|-----------|-------|

MUST cobrir:
- Receita total e decomposição por negócio/região
- Lucro bruto, variação de margem bruta
- Lucro operacional, variação de margem operacional (diferenciar GAAP e Non-GAAP)
- Lucro líquido (atente para impacto de itens extraordinários)
- EPS (básico vs diluído)

#### 2.2 Demonstração de fluxo de caixa (mais importante para Buffett)

| Indicador | Este período | Período anterior | Variação | Ponto de atenção |
|------|------|------|------|--------|

MUST cobrir:
- Fluxo de caixa operacional vs lucro líquido ratio (>100% é bom, <80% alerta)
- Despesa de capital e composição (manutenção vs expansão)
- Fluxo de caixa livre = fluxo operacional - despesa de capital
- Montante de recompra, montante de dividendo
- Saldo de caixa período final

#### 2.3 Saúde de balanço patrimonial

MUST cobrir:
- Caixa + investimento curto prazo vs passivo com juros
- Variação de tendência de caixa líquido / passivo líquido
- Variação de dias de rotação de contas a receber (está relaxando condições de crédito para inflacionar receita?)
- Variação de dias de rotação de estoque (está acumulando?)
- Proporção de goodwill e ativo intangível (tem risco de redução?

**Verificação de dados**: Use `tools/financial_rigor.py` para validar dados principais:

```bash
# Verificação cruzada de receita e lucro líquido (pelo menos 2 fontes)
python3 tools/financial_rigor.py cross-validate \
  --metric "revenue" --values 108.3e9 107.9e9 --sources "relatório da empresa" "Yahoo Finance"

# Verificação de capitalização
python3 tools/financial_rigor.py verify-market-cap \
  --price 101 --shares 1.488e9 --reported 1.44e11 --currency USD

# Verificação de indicador de avaliação
python3 tools/financial_rigor.py verify-valuation \
  --price 101 --eps 9.6 --bvps 26.5 --fcf-per-share 10.2
```

### Terceira etapa: Leitura detalhada de discussão de gestão (MD&A)

Este é o lugar onde Buffett e Li Lu gastam mais tempo. Não é ver número, é **ouvir como gestão fala**.

#### 3.1 Análise de tom de gestão

Leia parágrafo por parágrafo discussão de gestão/chamada de telefone, marque sinais:

| Tipo de sinal | Manifestação concreta | Exemplo |
|---------|---------|------|
| 🟢 **Sinal de honestidade** | Reconheça ativamente problema, dê razão concreta | "Queda de margem trimestral principalmente porque nosso investimento em área X excedeu previsão" |
| 🟢 **Sinal claro** | Estratégia expressão concreta, tem objetivo quantificado | "Planejamos nos próximos 12 meses aumentar participação de negócio X de 15% para 20%" |
| 🔴 **Sinal nebuloso** | Muita "acreditamos", "longo prazo" sem conteúdo substancial | "Temos confiança no futuro" |
| 🔴 **Sinal de transferência** | Evite pergunta direta, mude tópico | Perguntado sobre margem, conversa sobre velocidade de receita |
| 🔴 **Sinal de atribuição externa** | Atribua problema completamente a macro/indústria/competidor | "Por causa de ambiente macro..." |

#### 3.2 Rastreamento de compromisso

Extraia compromisso específico de gestão de período anterior, compare com situação real neste período:

| Compromisso anterior | Situação de implementação este período | Avaliação |
|---------|------------|------|
| "Margem lucro 2º semestre vai recuperar para X%" | Real Y% | ✅ Atingiu / ❌ Não atingiu / ⚠️ Parcialmente atingiu |

**Duan Yongping**: "Maneira mais simples de saber se gestão é confiável é ver se coisa que disse antes conseguiu fazer."

#### 3.3 Identificação de questão-chave

Extraia pergunta mais afiada de analista de Q&A de chamada, assim como qualidade de resposta de gestão:

| Pergunta de analista | Resposta de gestão | Qualidade resposta (1-5) | Evitou |
|-----------|-----------|:-----:|:-------|

### Quarta etapa: Escavação de informação em anexos e oculta

Anexos de relatório têm informação que gestão não quer você ver facilmente:

#### 4.1 Itens de anexo que MUST verificar

- [ ] **Transação relacionada**: Transação com grande acionista/parte relacionada tem condição justa?
- [ ] **Incentivo acionário**: Efeito diluição de opção/RSU quanto? Preço de exercício quanto?
- [ ] **Passivo contingente**: Litígio, garantia, compromisso etc. risco fora de relatório
- [ ] **Mudança de política contábil**: Mudança de reconhecimento de receita, anos de depreciação etc.?
- [ ] **Informação de divisão**: Margem de lucro diferente negócio, "negócio bom subsidiando ruim"?
- [ ] **Concentração cliente/fornecedor**: TOP 5 cliente/fornecedor proporção

#### 4.2 Detecção de sinal anômalo

- [ ] Velocidade crescimento contas a receber > velocidade crescimento receita (talvez está entupindo canal)
- [ ] Velocidade crescimento estoque > velocidade crescimento receita (talvez está acumulando)
- [ ] Fluxo caixa operacional < lucro líquido e disparidade está ampliando (qualidade lucro questionável)
- [ ] Despesa capital subitamente aumenta (talvez está embelezando lucro)
- [ ] Proporção receita extraordinária subitamente sobe

### Quinta etapa: Comparação com dados históricos

#### 5.1 Análise de tendência

Coloque indicadores principais deste período em série temporal de pelo menos 4 trimestres (ou 3 relatórios anuais):

| Indicador | Q-4 | Q-3 | Q-2 | Q-1 | Este período | Julgamento de tendência |
|------|-----|-----|-----|-----|------|---------|

Foco em:
- Margem lucro está melhorando ou piorando?
- Velocidade crescimento receita está acelerando ou desacelerando?
- Qualidade fluxo caixa está melhorando ou piorando?
- Intensidade despesa capital está aumentando ou diminuindo?

#### 5.2 Comparação com orientação de gestão anterior

| Indicador | Orientação gestão anterior | Resultado real | Disparidade | Interpretação |
|------|--------------|---------|------|------|

### Sexta etapa: Saída de relatório de leitura profunda

#### Estrutura de relatório

```
Um. Resumo de dados principais (uma página tabela)
Dois. Os 3 mudanças mais importantes deste período (não exceda 500 palavras)
Três. Tom de gestão e rastreamento de compromisso
Quatro. Informação oculta em anexos
Cinco. Questão-chave (Q&A de chamada selecionados)
Seis. Relação com tese de investimento (se houver posição)
Sete. Conclusão: este relatório mudou o quê?
```

#### Conclusão MUST responder claramente

1. **Este relatório é acima previsão, dentro previsão, ou abaixo previsão?** (Não pode dizer "mais ou menos dentro" então listar duas discussões)
2. **Impacto para tese de investimento**: Fortaleça / Sem impacto / Enfraqueça / Quebra
3. **Próximo catalisador que precisa observar qual?**
4. **Se você já tem posição, deve ampliar/manter/reduzir?**

### Sétima etapa: Salve relatório

Escreva relatório em `reports/{nome-empresa}-earnings-{período}.md`, por exemplo `reports/tencent-earnings-2025Q4.md`

### Oitava etapa: Verificação de dados de amostra (processo de verificação)

Após escrever relatório, execute verificação de amostra, pode apenas publicar se passar:

```bash
# Passo 1 — Extrair lista de verificação
python3 tools/report_audit.py extract \
  --report reports/{nome-empresa}-earnings-{período}.md

# Passo 2 — Para cada item lista, obter número de fonte confiável (veja skills/financial-data.md)

# Passo 3 — Saída decisão de verificação/rejeição
python3 tools/report_audit.py verdict \
  --results '<JSON preenchido>' \
  --report {nome arquivo relatório}
```

**【Verificado】** tudo passou → publicar; **【Rejeitado】** tem não passou → corrigir depois reauditar.

## Princípios-chave

- **Leia original, não resumo**: Faça tudo possível para obter fonte primária
- **Veja mudança, não valor absoluto**: Tendência mais importante que número
- **Ouça tom, não apenas conteúdo**: Como gestão fala é tão importante quanto o quê fala
- **Verifique anexos, não apenas corpo**: Demônio está em detalhes
- **Dê conclusão, não faça resumo**: Propósito leitura profunda é formar julgamento, não repetir relatório