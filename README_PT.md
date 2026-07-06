Português | [English](README_EN.md) | [中文](README.md) | [日本語](README_JA.md)

[![GitHub Trending](https://trendshift.io/api/badge/repositories/63696)](https://trendshift.io/repositories/63696)

# AI Berkshire - Framework de Pesquisa de Investimento em Valor na Era da IA

> "Price is what you pay, value is what you get." — Warren Buffett
>
> Redefina a profundidade e eficiência da pesquisa de investimento com IA.

**AI Berkshire** é um conjunto de Skills de pesquisa de investimento compatíveis simultaneamente com Claude Code e Codex que sistematizam e estruturam as metodologias dos quatro mestres do investimento em valor — Warren Buffett, Charlie Munger, Tan Yongping e Li Lu — realizando pesquisa de investimento em nível profissional por meio de AI Agent.

Uma pessoa + Claude Code / Codex = um time de pesquisa de investimento.

[Desempenho Real](#desempenho-real) · [Por que não pode perguntar diretamente à IA](#por-que-não-pode-perguntar-diretamente-à-ia) · [Visão Geral de Skills](#visão-geral-de-skills19-skills) · [Início Rápido](#início-rápido) · [Relatórios Práticos](#relatórios-de-pesquisa-prática) · [Filosofia de Design](#filosofia-de-design) · [Conta Pública](#pesquisa-selecionada-lançada-primeiro-na-conta-pública)

---

## Desempenho Real

> Não é teoria pura. Este framework é apoiado por um sistema de investimento verificado com dinheiro real.

### Retorno Total em 2024: +69,29%

<img src="assets/2024-returns.jpg" width="300" />

### Retorno Total em 2025: +66,38%

<img src="assets/2025-returns.jpg" width="300" />

### Comparação com Principais Índices

| Métrica | 2024 Total | 2025 Total |
|---------|-----------|-----------|
| **Este Framework (Real)** | **+69,29%** | **+66,38%** |
| Índice Hang Seng | +17,67% | +27,77% |
| S&P 500 | +23,31% | +16,39% |
| CSI 300 | +14,68% | +17,66% |
| NASDAQ | +28,64% | +20,36% |

**2024 Retorno em Excesso**: Superou S&P 500 em **46 pontos percentuais**, Hang Seng em **52 pontos percentuais**

**2025 Retorno em Excesso**: Superou S&P 500 em **50 pontos percentuais**, Hang Seng em **39 pontos percentuais**

**Lucro Real Acumulado em Dois Anos acima de 1,46 milhão**, superando consistentemente os principais índices globais por dois anos consecutivos.

> *Isenção de Responsabilidade: Retornos históricos não indicam desempenho futuro. Screenshots são de contas reais da Futu Securities.*

### Pesquisa em Destaque Lançada Primeiro em Nossa Conta Pública

O repositório contém o framework completo e todos os relatórios, enquanto a conta pública apresenta **seleções** — pesquisas aprofundadas reais sobre as empresas que realmente valem a pena investir, além do meu próprio julgamento e decisões além dos relatórios:

<img src="assets/wechat-qr.png" width="160" alt="WeChat Public Account: 复利炼丹炉" />

**复利炼丹炉** —— Usando IA para refinar a pesquisa de investimentos.

---

## Por que não pode perguntar diretamente à IA?

Você certamente pode perguntar diretamente ao Claude: "Analise se a PDD vale a pena comprar". Você receberá uma análise "equilibrada" com "por um lado... por outro lado..." terminando com "investimento tem risco, julgue por si mesmo".

**Essa análise parece certa, mas não serve para tomar decisões.**

AI Berkshire não resolve o problema "pode analisar", mas sim a **qualidade da análise e disciplina de decisão**. Aqui estão as diferenças principais:

### 1. Força conclusões, não mede-meias

Perguntar diretamente à IA, você obtém análise "dos dois lados". AI Berkshire força a saída: **Passar/Não passar/Zona cinzenta**, com faixas de preço específicas e recomendações em camadas.

> Resposta de IA comum: *"PDD tem potencial de crescimento mas também enfrenta pressão competitiva, investidores precisam pesar..."*
>
> Saída de AI Berkshire:

> | Estratégia | Recomendação | Faixa de Preço |
> |------|------|---------|
> | Agressiva | Pode construir 20% na posição atual | $95-105 |
> | Conservadora | Aguarde esclarecimento da política de recompra | $85-95 |
> | Muito Conservadora | Não atende ao padrão de certeza de 10 anos, observar | — |
>
> **Teste do Espelho**: Não conseguir explicar em 5 frases = Não comprar, sem exceções.

### 2. Quatro Perspectivas de Mestres em Conflito, não Análise Única

Não é tão simples quanto "analisar usando método Buffett". Quatro perspectivas criam **conflitos e tensão reais** —

Usando PDD como exemplo:
- **Tan Yongping** (Modelo de Negócio): Bom negócio, modelo C2M é difícil copiar → Pontuação 3.7/5
- **Warren Buffett** (Avaliação Financeira): PE com desconto de caixa apenas 6,3x, máquina impressora → Pontuação 4.4/5
- **Charlie Munger** (Pensamento Inverso): Fosso é mais raso do que imaginamos, Douyin atingiu 4 trilhões GMV em 3 anos → Pontuação 3.5/5
- **Li Lu** (Certeza em Longo Prazo): Cultura de gestão tem riscos ocultos, incerteza em 10 anos → Pontuação 2.0/5

**Buffett diz "muito barato", Li Lu diz "se incerto não compre"** — esse conflito é o verdadeiro estado da decisão de investimento. Um único prompt não pode criar esse conflito multi-perspectiva, e é exatamente isso que evita pontos cegos.

### 3. Mecanismo de Prevenção de Viés Estruturado

O mais perigoso com IA não é dar respostas erradas, mas dar uma **resposta que parece muito certa mas não aguenta crítica**. AI Berkshire possui múltiplas camadas de "detecção de fraude" embutidas no processo:

| Mecanismo | Que problema resolve | Exemplo |
|------|------------|------|
| **Imposição de citação** | Alucinações sem suporte | Exigir que cada afirmação cite fonte/ano |
| **Teste de inversão** | Viés de confirmação | "Refute seu próprio argumento principal" |
| **Checagem de inconsistência** | Lógica contraditória | Comparar conclusão com análise linha por linha |
| **Validação de dados** | Erros de cálculo | Recalcular PE/ROE/Free Cash Flow com python |

---

## Visão Geral de Skills (19 Skills)

| Skill | Entrada | Saída | Tempo |
|------|---------|--------|--------|
| `/investment-research` | Símbolo de ticker | Relatório estruturado (12 dimensões) | 8-12 min |
| `/investment-team` | Símbolo de ticker | 4 perspectivas de mestres + relatório executivo | 15-20 min |
| `/investment-checklist` | Símbolo de ticker | Checklist de 50 pontos (go/no-go) | 4-6 min |
| `/earnings-review` | Transcript de call de ganhos | Análise de ganhos (estimativa vs real) | 3-5 min |
| `/earnings-team` | Transcript de call | 4 perspectivas + artigo público | 8-10 min |
| `/management-deep-dive` | Símbolo de ticker | Análise aprofundada de gestão (estilo, trilha) | 6-8 min |
| `/thesis-tracker` | ID da empresa | Acompanhamento contínuo de tese ao longo do tempo | Contínuo |
| `/industry-research` | Setor/tema | Análise de indústria, tamanho de mercado, dinâmica | 8-12 min |
| `/industry-funnel` | N/A | Funil de triagem: mercado → setor → company top-N | 10-15 min |
| `/portfolio-review` | Lista de holdings | Revisão trimestral, alocação, rebalanceamento | 5-8 min |
| `/private-company-research` | Nome/descrição | Pesquisa de empresa privada (sem dados públicos) | 6-10 min |
| `/quality-screen` | Símbolo | Filtro de qualidade: ROE >15%, débito <40%, livre de dívida | 2-3 min |
| `/news-pulse` | Lista de empresas | Resumo de notícias da semana + impacto em tese | 3-5 min |
| `/bottleneck-hunter` | Empresa/setor | Identifica gargalo crítico, como corrigir | 4-6 min |
| `/dyp-ask` | Pergunta | Perspective de Tan Yongping sobre questão | 2-3 min |
| `/financial-data` | Símbolo | Extração estruturada de dados financeiros chave | 1-2 min |
| `/thesis-drift` | ID da tese | Detecção: a tese ainda é válida? Disparadores de venda | 3-4 min |
| `/deep-company-series` | Símbolo | Série profunda multi-artigo sobre empresa | 20-30 min |
| `/wechat-article` | Relatório | Transforma relatório técnico em artigo para público | 2-3 min |

---

## Início Rápido

### Instalação

```bash
# Clone o repositório
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire

# Instale as skills no Claude Code
bash scripts/install-claude-commands.sh

# OU instale os prompts Codex
bash scripts/install-codex-prompts.sh
bash scripts/install-codex-skills.sh
```

### Primeiro Uso

```bash
# Use diretamente no Claude Code com /investment-research
/investment-research PDD

# OU use como Codex Prompt
# Copie o prompt de codex-prompts/investment-research.md para seu Codex
```

---

## Relatórios de Pesquisa Prática

> Estes não são relatórios de modelo, mas pesquisa real com dinheiro real em risco. Cada relatório é auditado pela estratégia de inversão.

### Relatórios em Destaque (2025-2026)

- **Tencent Research** — Análise detalhada de ganhos 2025Q4, recomendação de venda
- **PDD Research** — Modelo de negócio vs avaliação, análise de 4 mestres
- **ADP Deep Dive** — Por que um "software sem IA" é a máquina de impressão mais segura

### Banco de Dados Completo

Todos os relatórios em `reports/`. Cada empresa tem sua pasta com:
- Análise de 4 mestres
- Acompanhamento de tese
- Análise de ganhos
- Análise de gestão

---

## Filosofia de Design

### 1. Rigor em Vez de Velocidade

> Uma análise errada rápida é pior que uma análise correta lenta.

- Não confiamos em resumos de LLM — todos os dados são validados
- Requer fontes para cada afirmação — sem alucinações
- Reconhece incerteza em vez de disfarçá-la com confiança falsa

### 2. Perspectivas Múltiplas Superam Expertise Única

> Você não quer um especialista que concorda consigo; quer uma mesa de divergência.

- 4 mestres de investimento, filosofias diferentes — **não harmonia, contraste**
- Cada perspectiva tem seu próprio critério de aprovação/rejeição
- O conflito entre eles é o sinal mais importante

### 3. Trate Investimento Como Ciência, Não Arte

> Mensurável, replicável, auditável — senão não é investimento, é aposta.

- Cada decisão tem critério de entrada/saída claro
- Raciocínio documentado — não "sensação de mercado"
- Histórico rastreável — para melhorar o processo continuamente

### 4. Estrutura Escalável

> Um sistema que só funciona para Warren Buffett não é útil para você.

- Framework agnóstico — funciona para qualquer mercado, setor, classe de ativos
- Skills são compostas — combine conforme necessário
- Saídas são estruturadas — legível por máquina para automação

---

## Seleção de Pesquisa Lançada Primeiro na Conta Pública

A conta de mídia social em destaque é **复利炼丹炉** no WeChat. Primeira publicação de:

- **Pesquisa temática** — Por que a inteligência artificial está em transição? Quem se beneficia?
- **Análise de oportunidade** — Top 3 empresas hoje por faixa de preço
- **Insights de fundação de portfolio** — Reequilíbrio trimestral e raciocínio

> Siga a conta para:
> - Insights de pesquisa antes do repositório
> - Contexto que não entra em relatório
> - Discussão em tempo real sobre mercado/macro

---

## Contribuições

Sim, aceitamos contribuições. Veja `CONTRIBUTING.md`.

Se você criou uma análise 4 mestres legal sobre uma empresa — de uma **verdadeira perspectiva divergente, não cópia** — abra um PR.

---

## Licença

MIT License — código aberto e uso livre. Veja `LICENSE`.

---

## Renúncia de Responsabilidade

Este framework é educacional. Nenhum relatório é recomendação de investimento. Faça sua própria pesquisa, sempre.

> "Em Wall Street, a manada é recompensada. Mas o dinheiro é feito pelos que pensam diferente." — Mark Spiegel
