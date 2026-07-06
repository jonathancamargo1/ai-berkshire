# Análise Detalhada de Relatórios Financeiros: Interpretação de Dados Primários

Execute análise detalhada de relatórios financeiros para $ARGUMENTS.

**Formatos de entrada suportados**: `Nome da empresa Período`, por exemplo: `Tencent 2025Q4`, `PDD 2025 Anual`, `Meituan Mais recente` (padrão: período mais recente)

> "Nunca leio relatórios de vendedores, apenas leio relatórios financeiros originais." —— Li Lu
>
> "Leio 500 páginas por dia. É assim que o conhecimento se acumula, como juros compostos." —— Warren Buffett

## Filosofia de Design

A maioria das ferramentas de análise de investimentos com IA dependem de informações secundárias (notícias, resumos de relatórios, sites de dados). Mas a competência central de Buffett e Li Lu é **ler materiais de primeira mão** - relatórios anuais, relatórios trimestrais, transcrições de chamadas.

Problemas com informações secundárias:
- Filtradas - analistas selecionam dados que favorecem seu ponto de vista
- Defasadas - até que outros processem, o alpha já desapareceu
- Sem contexto - "crescimento de receita 15%" separado da discussão do CEO sobre qualidade

Este Skill lê diretamente materiais de primeira mão, focando no que Buffett e Li Lu realmente observam.

## Fluxo de Execução

### Etapa Preliminar: Classificação de Disponibilidade de Dados

| Nível | Características | Impacto |
|------|------|------|  
| Nível A | Acesso a texto completo (10-K/Anual/Transcrições) | Executar todas as etapas normalmente |
| Nível B | Apenas texto parcial ou resumos de terceiros | Marcar "fonte não original", reduzir peso de análises complementares |
| Nível C | Apenas notícias e resumos de sites | Focar em mudanças de dados financeiros principais, pular análises complementares, marcar "dados de primeira mão insuficientes" |

### Primeira Etapa: Obter Dados de Primeira Mão

Use a ferramenta Task para iniciar múltiplos Agents **em paralelo** obtendo materiais originais:

1. **Relatório Financeiro Original**: De páginas IR da empresa, SEC EDGAR (10-K/10-Q dos EUA), HKExnews (Hong Kong), Juchai.com.cn (China A-shares)
2. **Transcrições/Gravações de Chamadas de Resultado**: De Seeking Alpha, páginas IR da empresa, Snowball etc.
3. **Carta de Gestão aos Acionistas** (se houver anual): Leitura completa
4. **Materiais de Investor Day/Analyst Day** (se recente): Quando disponível

Se não conseguir texto completo, seguir normas em `skills/financial-data.md` usando fontes padrão (EUA: macrotrends+stockanalysis; Hong Kong: aastocks+macrotrends; China: Eastmoney+Juchai), mas marcar "não é relatório original, agregado de terceiros", e dados com diferença >1% entre fontes devem ser marcados.

### Segunda Etapa: Extração e Verificação de Dados Financeiros Principais

#### 2.1 Demonstração de Resultado e Lucro

| Indicador | Este Período | Período Anterior | Variação YoY | Orientação da Gestão | Atingiu Meta |
|------|------|------|---------|-----------|----------|

Deve cobrir:
- Receita total e decomposição por negócio/região
- Lucro bruto, mudança de margem bruta
- Lucro operacional, mudança de margem operacional (GAAP vs Non-GAAP)
- Lucro líquido (nota: efeito de itens não-recorrentes)
- EPS (básico vs diluído)

#### 2.2 Fluxo de Caixa (o que Buffett mais observa)

| Indicador | Este Período | Período Anterior | Variação | Ponto de Atenção |
|------|------|------|------|--------|

Deve cobrir:
- Fluxo operacional vs lucro líquido: relação >100% é boa, <80% precisa de alerta
- Despesa de capital e composição (manutenção vs expansão)
- Fluxo livre = Fluxo operacional - Despesa capital
- Recompra de ações, dividendos
- Saldo final de caixa e equivalentes

#### 2.3 Saúde do Balanço Patrimonial

Deve cobrir:
- Caixa + Investimentos curto prazo vs Passivo com juros
- Mudança de caixa líquido/passivo líquido
- Dias de rotação de contas a receber (está soltando crédito para impulsionar receita?)
- Dias de rotação de estoque (acumulação?)
- Ágio e ativos intangíveis (risco de redução?)

**Verificação de Dados**: Use `tools/financial_rigor.py` para validar dados principais:

```bash
# Validação cruzada de receita e lucro líquido
python3 tools/financial_rigor.py cross-validate \
  --metric "revenue" --values 108.3e9 107.9e9 --sources "Relatório Empresa" "Yahoo Finance"

# Validação de valor de mercado
python3 tools/financial_rigor.py verify-market-cap \
  --price 101 --shares 1.488e9 --reported 1.44e11 --currency USD

# Cálculo de indicadores de avaliação
python3 tools/financial_rigor.py verify-valuation \
  --price 101 --eps 9.6 --bvps 26.5 --fcf-per-share 10.2
```

### Terceira Etapa: Leitura Detalhada de Discussão de Gestão (MD&A)

Esta é a parte onde Buffett e Li Lu gastam mais tempo. Não é sobre números, é sobre **como a gestão fala**.

#### 3.1 Análise de Tom da Gestão

Leia parágrafo por parágrafo a discussão da gestão/fala em chamadas, marcando:

| Tipo de Sinal | Manifestação Específica | Exemplo |
|---------|---------|------|
| 🟢 **Sinal de Honestidade** | Reconhecer ativamente problemas, dar razões específicas | "Nossa margem de lucro caiu este trimestre principalmente porque investimentos em domínio X excederam expectativas" |
| 🟢 **Sinal Claro** | Estratégia expressa concretamente, com metas quantificadas | "Planejamos aumentar participação de mercado de domínio X de 15% para 20% nos próximos 12 meses" |
| 🔴 **Sinal Vago** | Muito uso de "acreditamos", "a longo prazo" sem substância | "Somos otimistas com o futuro" |
| 🔴 **Sinal de Desvio** | Evitar perguntas diretas, mudar para outro tópico | Perguntado sobre margem, desvia falando sobre crescimento de receita |
| 🔴 **Culpa Externa** | Responsabilizar tudo ao macro/indústria/concorrentes | "Devido ao ambiente macro..." |

#### 3.2 Rastreamento de Promessas

Extraia promessas específicas do relatório/chamada anterior, compare com situação atual:

| Promessa Anterior | Execução Atual | Avaliação |
|---------|------------|------|
| "Margem de lucro H2 será X%" | Realizou Y% | ✅Atingida / ❌Não atingida / ⚠️Parcialmente atingida |

**Duan Yongping**: "A forma mais simples de julgar se uma gestão é confiável é ver se cumpriam o que disseram antes."

#### 3.3 Identificação de Questões Principais

Extraia as perguntas mais aguçadas dos analistas, qualidade das respostas da gestão:

| Pergunta do Analista | Resposta da Gestão | Qualidade(1-5) | Desviou? |
|-----------|-----------|:----------:|:-----:|

### Quarta Etapa: Escavação de Notas e Informações Ocultas

As notas dos relatórios contêm o que a gestão não quer que você veja facilmente:

#### 4.1 Itens de Notas que Deve Verificar

- [ ] **Transações Relacionadas**: Os termos de transações com acionistas/partes relacionadas são justos?
- [ ] **Incentivos de Ações**: Qual é o efeito de diluição de opções/RSU? Qual é o preço de exercício?
- [ ] **Passivos Contingentes**: Litígios, garantias, compromissos fora do balanço
- [ ] **Mudanças de Política Contábil**: Mudanças em reconhecimento de receita, vida útil de depreciação?
- [ ] **Informação de Segmento**: Diferenças de margem entre negócios - algum negócio bom subsidiando ruim?
- [ ] **Concentração Clientes/Fornecedores**: Os 5 maiores clientes/fornecedores representam quanto?

#### 4.2 Detecção de Sinais Anormais

- [ ] Crescimento de contas a receber > crescimento de receita (está entupindo canal?)
- [ ] Crescimento de estoque > crescimento de receita (acumulação?)
- [ ] Fluxo operacional < lucro líquido e diferença crescente (qualidade de lucro suspeita?)
- [ ] Capitalização de despesas de repente aumenta (embelezando lucro?)
- [ ] Renda não-recorrente salta repentinamente

### Quinta Etapa: Comparação com Dados Históricos

#### 5.1 Análise de Tendência

Coloque indicadores-chave em série temporal de pelo menos 4 trimestres (ou 3 anos de anuais):

| Indicador | Q-4 | Q-3 | Q-2 | Q-1 | Este Período | Julgamento de Tendência |
|------|-----|-----|-----|-----|------|----------|

Foco especial:
- Margem de lucro está melhorando ou piorando?
- Crescimento de receita está acelerando ou desacelerando?
- Qualidade de fluxo de caixa está melhorando ou piorando?
- Intensidade de despesa de capital está aumentando ou reduzindo?

#### 5.2 Comparação com Orientação da Gestão

| Indicador | Orientação Anterior da Gestão | Resultado Real | Desvio | Interpretação |
|------|--------------|---------|------|------|

### Sexta Etapa: Saída do Relatório de Análise Detalhada

#### Estrutura do Relatório

```
Um, Visão Rápida de Dados Principais (tabela de uma página)
Dois, Os 3 Maiores Mudanças deste Período (não mais de 500 palavras)
Três, Tom de Gestão e Rastreamento de Promessas
Quatro, Informações Ocultas nas Notas
Cinco, Questões Principais (seleções de P&R de chamadas)
Seis, Relação com Tese de Investimento (se houver posição)
Sete, Conclusão: O Que Mudou?
```

#### Conclusão Deve Responder Claramente

1. **Este Relatório é Acima/Em/Abaixo das Expectativas?** (não pode dizer "basicamente em padrão" e depois ficar ambíguo)
2. **Impacto na Tese de Investimento**: Reforça / Sem Impacto / Enfraquece / Quebra
3. **Qual é o Próximo Catalisador a Observar?**
4. **Se Você Já Tem Posição, Deve Aumentar/Manter/Reduzir?**

### Sétima Etapa: Salvar Relatório

Escreva relatório em `reports/{Nome Empresa}-earnings-{Período}.md`, exemplo `reports/Tencent-earnings-2025Q4.md`

### Oitava Etapa: Verificação de Dados (Fluxo de Saída)

Após escrever relatório, execute verificação de dados, apenas passar se aprovar:

```bash
# Etapa 1 — Extrair lista de verificação
python3 tools/report_audit.py extract \
  --report reports/{Nome Empresa}-earnings-{Período}.md

# Etapa 2 — Para cada item, obter dados de fonte confiável (ver skills/financial-data.md)

# Etapa 3 — Saída de aprovação/rejeição
python3 tools/report_audit.py verdict \
  --results '<JSON preenchido>' \
  --report {nome arquivo relatório}
```

**【APROVADO】** Tudo passou → Publicar; **【REJEITADO】** Algum falhou → Corrigir e reanalisar.

## Princípios Principais

- **Ler original, não resumo**: Faça tudo possível para obter dados de primeira mão
- **Ver mudança, não valor absoluto**: Tendência é mais importante que números
- **Ouvir tom, não apenas conteúdo**: Como a gestão fala é tão importante quanto o que fala
- **Verificar notas, não apenas texto**: O diabo está nos detalhes
- **Dar conclusão, não resumo**: O propósito da análise detalhada é formar julgamento, não repetir o relatório