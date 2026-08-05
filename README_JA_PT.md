Português | [English](README_EN.md) | [中文](README.md)

> A versão em português é mantida pela comunidade. Se o conteúdo não estiver atualizado, considere a versão em chinês ou inglês como a fonte de verdade.

[![GitHub Trending](https://trendshift.io/api/badge/repositories/63696)](https://trendshift.io/repositories/63696)

# AI Berkshire — Framework de Pesquisa de Investimento em Valor para a Era da IA

> "Preço é o que você paga, valor é o que você recebe." — Warren Buffett
>
> Redefina a profundidade e eficiência da pesquisa com IA.

**AI Berkshire** é uma coleção de Skills de pesquisa de investimento compatível com Claude Code e Codex. Sistematizamos as metodologias de quatro gigantes do investimento em valor — Buffett, Munger, Duan Yongping (段永平) e Li Lu (李录) — e fornecemos pesquisa em nível profissional por meio de agentes de IA.

1 pessoa + Claude Code / Codex = Um time de pesquisa de investimento inteiro.

[Desempenho](#desempenho) · [Por que não perguntar diretamente à IA?](#por-que-não-perguntar-diretamente-à-ia) · [Lista de Skills](#lista-de-skills19-skills) · [Início Rápido](#início-rápido) · [Relatórios](#relatórios-de-pesquisa-reais) · [Filosofia de Design](#filosofia-de-design)

---

## Desempenho

> Isso não é uma simulação no papel. Este framework é respaldado por um portfólio auditado com fundos reais.

### Retorno Total de 2024: +69,29%

<img src="assets/2024-returns.jpg" width="300" />

### Retorno Total de 2025: +66,38%

<img src="assets/2025-returns.jpg" width="300" />

### Comparação com Benchmarks

| Benchmark | Total 2024 | Total 2025 |
|-----------|-----------|----------|
| **Este Framework (Real)** | **+69,29%** | **+66,38%** |
| Índice Hang Seng | +17,67% | +27,77% |
| S&P 500 | +23,31% | +16,39% |
| CSI 300 | +14,68% | +17,66% |
| NASDAQ Composto | +28,64% | +20,36% |

**Alpha 2024**: Superou S&P 500 por **46 pontos** e Hang Seng por **52 pontos**

**Alpha 2025**: Superou S&P 500 por **50 pontos** e Hang Seng por **39 pontos**

**Retorno acumulado real de 2 anos: mais de 1,46 milhão de yuan**, com desempenho superior consistente dos principais índices globais por 2 anos consecutivos.

> *Aviso: Desempenho passado não garante resultados futuros. Os screenshots são de uma conta de corretagem real (Futu Securities).*

---

## Por que não perguntar diretamente à IA?

Você pode perguntar ao Claude: "PDD (Pinduoduo) é uma compra?" Você receberá uma análise equilibrada com "por um lado... por outro lado..." e terminará com "investimentos envolvem risco, considere cuidadosamente." 

**Essa análise parece correta, mas não é utilizável para decisões reais.**

AI Berkshire não resolve o problema "a IA pode analisar?", mas sim **a qualidade da análise e a disciplina na tomada de decisão**. Aqui está o que é diferente.

### 1. Aplicar decisão forçada — Sem ambiguidade

Se você perguntar diretamente à IA, receberá uma análise "conveniente em ambos os lados". AI Berkshire força outputs específicos: **Aprovado / Reprovado / Zona Cinzenta**, com faixas de preço concretas e recomendações em camadas.

> Resposta a uma pergunta ingênua à IA: *"O PDD tem potencial de crescimento, mas há pressão competitiva. Os investidores..."*
>
> Output AI Berkshire:

> | Estratégia | Recomendação | Faixa de Preço |
> |-----------|------------|----------------|
> | Agressivo | Construir 20% de posição ao preço atual | $95–105 |
> | Moderado | Esperar esclarecimento de política de recompra | $85–95 |
> | Conservador | Não atende critério de certeza de 10 anos — Passar | — |
>
> **Teste do Espelho**: Se não puder explicar em 5 frases = Não compre. Sem exceções.

### 2. Dialética entre 4 gigantes — Não uma única perspectiva

Não é "analise isso usando o método de Buffett". Os 4 pontos de vista criam **tensões reais e contradições** —

Usando PDD como exemplo:
- **Duan Yongping** (Modelo de Negócio): Negócio excelente, modelo C2M difícil de replicar → 3,7/5
- **Buffett** (Financeiro/Avaliação): P/L ex-caixa apenas 6,3x, máquina de caixa → 4,4/5
- **Munger** (Pensamento Reverso): Moat mais raso que aparenta — Douyin atingiu GMV de 4 trilhões de yuan em 3 anos → 3,5/5
- **Li Lu** (Certeza de Longo Prazo): Preocupação com cultura de gestão, incerteza em 10 anos → 2,0/5

**Buffett diz "realmente barato" enquanto Li Lu diz "se incerto, não compre"** — Esta colisão é a realidade da decisão de investimento. Um único prompt não gera essa dialética de múltiplos pontos de vista, por isso previne pontos cegos.

### 3. Mecanismo Estruturado de Neutralização de Vieses

O maior perigo da IA não é dar respostas erradas, mas **dar respostas que parecem corretas mas não resistem ao escrutínio**. AI Berkshire incorpora múltiplas camadas de "prevenção de engano" no processo:

| Mecanismo | Problema que resolve | Exemplo |
|-----------|-------------------|---------|
| **Avaliação de Riqueza Informacional (A/B/C)** | Previne ilusão "mais dados = mais certeza" | Pop Mart é B: dados limitados, estimativas sinalizadas com confiança |
| **Teste Reverso de Munger** | Força consideração de cenários de falha | "Como PDD poderia quebrar?" → Lista 5 cenários com probabilidades |
| **Checklist de Morte Instantânea** | 8 bandeiras vermelhas, uma qualquer desqualifica | Integridade de gestão questionável → Rejeição imediata independente de avaliação |
| **Verificação Contrária** | Evita pensar como a multidão | "Por que pessoas inteligentes estão fazendo short disso?" → Expõe riscos negligenciados |
| **Integridade Intelectual** | Prioriza "não sei" | Lacunas de dados marcadas como "Zona Cinzenta", não preenchidas com especulação |

### 4. Precisão em Dados Financeiros

Os LLMs não são confiáveis em aritmética. Errar P/L por um dígito ou confundir dólar de Hong Kong com yuan pode levar a decisões catastróficas.

**Caso Real**: Na análise do Tencent, diferentes fontes relatavam capitalização de mercado em "bilhões de HKD" versus "bilhões de CNY". Abordagem AI Berkshire:

```bash
# Verificação manual de capitalização de mercado: Preço × Ações em Circulação, comparado com dados reportados
python3 tools/financial_rigor.py verify-market-cap \
  --price 510 --shares 9.11e9 --reported 4.65e12 --currency HKD
# ✅ Verificado — Desvio apenas 0,08%
```

Todos os cálculos usam Python `decimal.Decimal` (aritmética decimal precisa), nunca `float`. Dados críticos precisam validação cruzada de pelo menos 2 fontes independentes.

### 5. Processo de Pesquisa Reproduzível

Se perguntar diretamente à IA, o formato, profundidade e cobertura variam a cada vez — a análise do Tencent de hoje pode ter um moat score, mas a análise de Meituan de amanhã pode esquecê-lo.

AI Berkshire garante: **Mesmo input → Output consistente em estrutura, profundidade uniforme**. Isso permite:
- Comparar 7 empresas lado a lado com critérios de scoring idênticos
- Reanalizar a mesma empresa 6 meses depois e comparar mudanças diretamente
- Alinhar outputs de pesquisa entre membros do time

> Output real — Screening de 7 empresas com checklist idêntico:
>
> | Empresa | Decisão | Círculo de Competência | Negócio Excelente | Moat | Gestão | Margem de Segurança | Total |
> |---------|:------:|:-------------------:|:----------------:|:----:|:------:|:------------------:|:-----:|
> | Kweichow Moutai | ✅ Aprovado | ★★★★★ | ★★★★★ | ★★★★★ | ★★★☆☆ | ★★★★☆ | 4,7 |
> | Tencent | ✅ Aprovado | ★★★★☆ | ★★★★★ | ★★★★★ | ★★★★★ | ★★★★☆ | 4,7 |
> | NVIDIA | ✅ Condicional | ★★★★☆ | ★★★★★ | ★★★★★ | ★★★★★ | ★★★☆☆ | 4,3 |
> | Meituan | ✅ Condicional | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | 4,0 |
> | Kuaishou | ✅ Condicional | ★★★☆☆ | ★★★★☆ | ★★★★☆ | ★★★★☆ | ★★★★★ | 4,0 |
> | Pinduoduo | ❓ Cinza | ★★★★☆ | ★★★★☆ | ★★★☆☆ | ★★★☆☆ | ★★★★★ | 3,8 |
> | Pop Mart | ❓ Cinza | ★★★☆☆ | ★★★★☆ | ★★★★☆ | ★★★★★ | ★★★☆☆ | 3,7 |

### 6. Processamento Paralelo Multi-Agente = Multiplicação de Profundidade de Pesquisa

O `/investment-team` inicia 4 agentes independentes **simultaneamente** para pesquisar uma empresa. Cada agente conduz suas próprias buscas web, valida dados cruzados e chega a conclusões independentes. Não é um prompt dividido em 4 seções — são 4 "analistas" conduzindo pesquisa completa, com um líder de time consolidando o julgamento final.

Se perguntar à IA diretamente, há apenas uma janela de contexto. 4 agentes paralelos significam 4x o volume de busca, 4x as fontes de informação, 4 perspectivas independentes.

<p align="center">
  <img src="assets/team-core-en.svg" alt="Líder de time executando 4 agentes em paralelo" width="720" />
</p>

### Em Resumo

> **Um usuário comum perguntando à IA recebe "uma análise que parece correta". Com AI Berkshire, você obtém "um relatório de pesquisa realmente utilizável para decisão".**

---

## Arquitetura

<p align="center">
  <img src="assets/architecture-en.svg" alt="Arquitetura AI Berkshire" width="760" />
</p>

**Filosofia de Design de 3 Camadas**:
- **Camada de Skills**: Abstrai "o que você quer fazer" em 19 pontos de entrada claros — pesquisa profunda, análise de lucros, screening de indústria, gestão de portfólio, ferramentas de pensamento. Escolha por cenário.
- **Camada de Agentes**: Skills tipo-time (`/investment-team`, `/earnings-team`, etc.) executam 4 agentes de perspectiva de mestres em paralelo sob um líder de time — buscam e julgam independentemente, contestam uns aos outros, consolidam no final. Skills leves contornam esta camada, chamando ferramentas diretamente.
- **Camada de Ferramentas**: Cálculo preciso, busca web em tempo real, auditoria de relatório — garante que dados em todos os relatórios sejam rigorosos e verificáveis.

---

## Lista de Skills (19 Skills)

### 🔬 Pesquisa Profunda

| Skill | Propósito | Quando Usar |
|-------|----------|-------------|
| [`/investment-research`](skills/investment-research.md) | Análise Integrada de 4 Gigantes | Pesquisa 360 de empresa pública |
| [`/investment-team`](skills/investment-team.md) | Time de Pesquisa Multi-Agente Paralelo | 4 agentes em paralelo — mais rápido e abrangente |
| [`/management-deep-dive`](skills/management-deep-dive.md) | Análise Profunda de Executivos | "Comprar ação é comprar pessoa" — quando gestão é a variável-chave |
| [`/private-company-research`](skills/private-company-research.md) | Pesquisa de Empresa Privada | Pesquisa de empresas privadas com pouca informação como Ant Group, SpaceX |
| [`/deep-company-series`](skills/deep-company-series.md) | Série de Análise Profunda em 8 Partes | Série de qualidade de publicação, ~120k caracteres de reset cognitivo a convergência de decisão |

### 📊 Análise de Lucros

| Skill | Propósito | Quando Usar |
|-------|----------|-------------|
| [`/earnings-review`](skills/earnings-review.md) | Leitura Profunda de Lucros (Documentos Primários) | Como Buffett lê relatórios — apenas documentos de divulgação bruta, sem relatórios de vendedores |
| [`/earnings-team`](skills/earnings-team.md) | Time de Lucros + Artigos Publicáveis | 4 gigantes interpretam lucros em paralelo → edição finalizando → revisão de leitores → pronto para publicação |

### 🏭 Screening de Indústria

| Skill | Propósito | Quando Usar |
|-------|----------|-------------|
| [`/industry-research`](skills/industry-research.md) | Varredura de Cadeia de Valor de Indústria | Mapear oportunidades de investimento em toda a cadeia de valor de uma indústria |
| [`/industry-funnel`](skills/industry-funnel.md) | Screening de Funil de Indústria | Mercado total → Pré-screening ≤10 empresas → Seleção final 3 empresas com análise profunda |
| [`/quality-screen`](skills/quality-screen.md) | Screening de Qualidade (7 Métricas Rigorosas) | Eliminar rapidamente empresas não-elite; suporta screening em lote para ticker individual/indústria/índice/tema |
| [`/bottleneck-hunter`](skills/bottleneck-hunter.md) | Caçador de Gargalo de Cadeia de Suprimento | A partir de grandes tendências, encontrar gargalos físicos de cadeia de suprimento e oportunidades de arbitragem |
| [`/investment-checklist`](skills/investment-checklist.md) | Checklist Pré-Compra de Buffett | 6 portões, 10 minutos para determinar se vale a pena pesquisa profunda |

### 📈 Gestão de Portfólio

| Skill | Propósito | Quando Usar |
|-------|----------|-------------|
| [`/portfolio-review`](skills/portfolio-review.md) | Revisão & Otimização de Portfólio | De "pesquisar empresas" para "gerenciar portfólio" — dimensionamento de posição, concentração, rebalanceamento |
| [`/thesis-tracker`](skills/thesis-tracker.md) | Rastreador de Tese de Investimento | Sistema de disciplina pós-compra: rastrear continuamente se tese de investimento está sendo negada |
| [`/thesis-drift`](skills/thesis-drift.md) | Detecção de Desvio de Tese | Comparar 2 teses/relatórios, distinguir mudança de fatos vs. mudança de avaliação vs. mudança de linguagem |
| [`/news-pulse`](skills/news-pulse.md) | Análise Rápida de Fator de Movimento de Preço | Quando ação sobe/desce drasticamente — 10 minutos para esclarecê-lo |

### 🧠 Ferramentas de Pensamento

| Skill | Propósito | Quando Usar |
|-------|----------|-------------|
| [`/dyp-ask`](skills/dyp-ask.md) | Perguntas & Respostas Duan Yongping | Pensar em qualquer pergunta usando metodologia Duan Yongping — negócio, investimento, vida |
| [`/financial-data`](skills/financial-data.md) | Obtenção de Dados Financeiros & Validação Cruzada | Garantir dados críticos vêm de 2+ fontes independentes; alertar sobre discrepâncias >1% |
| [`/wechat-article`](skills/wechat-article.md) | Fluxo de Trabalho de Artigo WeChat | Autor, editor e agentes leitores colaboram para produzir artigos prontos para publicação |

---

## Início Rápido

### Custo e Seleção de Modelo

Skills de pesquisa profunda, por design, executam múltiplos passes de pesquisa, validação de múltiplas fontes e integração multi-agente, que podem consumir tokens em volume. Esse custo é parte de cobrir mais completamente qualidade de negócio, finanças, estrutura de indústria e risco.

Para decisões de investimento significativas, a visão do mantenedor é que normalmente o modelo mais poderoso fornece o melhor ROI de análise; economizar custo de modelo não deveria sacrificar qualidade de decisão crítica. Modelos leves são úteis para triagem, resumo e perguntas de baixo risco, mas integração de moat-avaliação-gestão-risco deve ser considerada como dependendo mais fortemente de capacidade de modelo.

Para reduzir custos, ajuste o workflow antes de tentar baratear pesquisa profunda em si: primeiro use [`/quality-screen`](skills/quality-screen.md) para eliminar empresas fracas, ou [`/news-pulse`](skills/news-pulse.md) para análise rápida de movimento de preço. Somente execute [`/investment-research`](skills/investment-research.md) ou [`/investment-team`](skills/investment-team.md) se o resultado merecer pesquisa profunda.

### 1. Instalar Cliente de IA

Este repositório mantém um fluxo de trabalho padrão e fornece tanto comandos Claude Code quanto skills Codex. Instale o cliente que você usa.

Para usuários de Claude Code:

```bash
npm install -g @anthropic-ai/claude-code
```

Para usuários Codex em macOS / Linux:

```bash
# macOS / Linux
curl -fsSL https://chatgpt.com/codex/install.sh | sh

# ou use npm
npm install -g @openai/codex

# ou use Homebrew
brew install --cask codex

# Verificar instalação
codex --version
```

Usuários Windows podem usar o instalador PowerShell oficial: `powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"`

Se `codex --version` exibir a versão, prossiga para instalar Codex skills deste projeto.

#### Reduzir Prompts de Aprovação

Estes skills fazem muitas chamadas de ferramenta, e Claude Code solicitará aprovação por padrão para cada uma. Esse comportamento vem do sistema de permissões no cliente Claude Code, não de configurações padrão de repositório que este projeto pode mudar.

Se você confia no fluxo de trabalho atual e está rodando em ambiente confiável, você pode iniciar Claude Code em modo pular permissões:

```bash
claude --dangerously-skip-permissions
```

Aviso: Este modo desabilita os guardrails de aprovação de ferramenta do Claude Code. Apenas use se confiar no repositório, comandos e diretório de trabalho.

### 2. Instalar Skills

Para usuários Claude Code em macOS / Linux:

```bash
# Clonar repositório
git clone https://github.com/xbtlin/ai-berkshire.git

# Copiar skills para diretório global de comandos Claude Code
cd ai-berkshire
./scripts/install-claude-commands.sh
```

Para usuários Claude Code em Windows PowerShell / Prompt de Comando:

```bat
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire
.\scripts\install-claude-commands.bat
```

Para usuários Codex em macOS / Linux:

```bash
# Clonar repositório
git clone https://github.com/xbtlin/ai-berkshire.git

# Gerar e instalar Codex skills para ~/.codex/skills
cd ai-berkshire
./scripts/install-codex-skills.sh

# Opcional: Instalar prompts Codex slash para ~/.codex/prompts
# Se você quer usar pontos de entrada /investment-research como Claude Code
./scripts/install-codex-prompts.sh
```

Para usuários Codex em Windows PowerShell / Prompt de Comando:

```bat
git clone https://github.com/xbtlin/ai-berkshire.git
cd ai-berkshire
.\scripts\install-codex-skills.bat

REM Opcional: Instalar prompts Codex slash
.\scripts\install-codex-prompts.bat
```

O repositório mantém 3 pontos de entrada: `skills/*.md` são a fonte para comandos Claude Code; `codex-skills/*/SKILL.md` são pacotes Codex skill que `scripts/sync-codex-skills.py` gera de `skills/*.md`; `codex-prompts/*.md` é uma camada de compatibilidade com prompts Codex slash opcional.

### 3. Como Usar

Chamar diretamente em Claude Code:

```bash
# Pesquisa profunda
/investment-research Tencent
/investment-team Meituan
/management-deep-dive Zhang Xiaolong, Meituan
/private-company-research SpaceX
/deep-company-series Pinduoduo

# Análise de lucros
/earnings-review Tencent 2025Q4
/earnings-team PDD 2025 Anual

# Screening de indústria
/industry-research Energia Nuclear
/industry-funnel Computação AI
/quality-screen Constituintes Hang Seng
/bottleneck-hunter Infraestrutura AI
/investment-checklist Kweichow Moutai, NVIDIA, Apple

# Gestão de portfólio
/portfolio-review Tencent 30%, Meituan 20%, Kweichow Moutai 20%, Caixa 30%
/thesis-tracker Pinduoduo
/thesis-drift Pinduoduo reports/pinduoduo-thesis-2025Q4.md reports/pinduoduo-thesis-2026Q1.md
/news-pulse Tencent

# Ferramentas de pensamento
/dyp-ask Onde está o verdadeiro moat de Pinduoduo?
/wechat-article Meituan
```

Depois de instalar no Codex, reinicie o Codex e reference por nome de skill:

```text
Use investment-research para pesquisar Tencent
Use earnings-review para analisar lucros 2025 anual PDD
Use industry-funnel para fazer screening de Computação AI
Use bottleneck-hunter para escanear gargalos de Infraestrutura AI
Use thesis-drift para comparar 2 teses de investimento Pinduoduo
Use wechat-article para escrever artigo de investimento Meituan
```

Se você instalou prompts slash Codex, reinicie Codex e busque no menu `/`. Os pontos de entrada de prompt customizado oficial Codex normalmente aparecem como `prompts:<name>`:

```text
/prompts:investment-research Tencent
```

---

## Explicação Detalhada de Skills

(Seções de skills e design philosophy continuarão no mesmo padrão da versão em inglês...)

---

## Relatórios de Pesquisa Reais

> Abaixo estão relatórios de pesquisa de investimento reais gerados por este framework. Eles demonstram a qualidade real de output de pesquisa impulsionada por IA.

| Empresa | Skill Usado | Conclusão Núcleo | Relatório |
|---------|-----------|------------------|-----------|
| Pinduoduo (PDD) | `/investment-team` | Score 3,4/5 — Extremamente barato mas certeza de 10 anos insuficiente; apropriado para posição moderada | [Ver Relatório](reports/pinduoduo/) |
| Tencent (0700.HK) | `/investment-research` | Monopólio Social + Excelente Alocação de Capital; P/L Forward 14x é Justo a Baixo | [Ver Relatório](reports/tencent/) |
| Comparação 7 Empresas | `/investment-checklist` | Kweichow Moutai & Tencent Aprovados; NVIDIA, Meituan & Kuaishou Condicionais; Pinduoduo & Pop Mart Cinza | [Ver Relatório](reports/multi-company-checklist-20260408.md) |
| Rastreador de Posição de Mestres | Pesquisa Customizada | Posições 13F Mais Recentes de Buffett / Li Lu / Duan Yongping + Análise de Custo-Basis PDD | [Ver Relatório](reports/master-holdings-tracker-20260408.md) |

---

## Filosofia de Design

### Integração de Metodologia dos 4 Gigantes

**Duan Yongping · "Negócio Correto"** — A essência do negócio. Ponto de partida comum dos 3 outros pontos de vista:

| Buffett | Munger | Li Lu |
|:---:|:---:|:---:|
| Moat<br>Margem de Segurança<br>Gestão | Pensamento Reverso<br>Lista de Risco<br>Auditoria de Viés | Tendência Civilizacional<br>Mudança de Paradigma<br>Valor de Indústria |

Os 4 gigantes não estão apenas dividindo trabalho — **estão projetados para desafiar um ao outro**:
- Se Duan Yongping disser "negócio excelente" → Munger pergunta "como isso poderia quebrar?"
- Se Buffett disser "barato o suficiente" → Li Lu pergunta "vai existir em 10 anos?"
- Não é colar 4 relatórios — é **colisão de 4 sistemas de pensamento**

### Ferramenta de Precisão Financeira (`tools/financial_rigor.py`)

| Funcionalidade | Comando | Problema que Resolve |
|--------|---------|----------------------|
| **Verificação de Capitalização de Mercado** | `verify-market-cap` | Preço × Ações em Circulação, cálculo preciso, detecção de erro de unidade |
| **Verificação de Avaliação** | `verify-valuation` | P/L / P/B / ROE / Rendimento FCF — aritmética decimal rigorosa |
| **Validação Cruzada Multi-Fonte** | `cross-validate` | Comparação automática de mesmo ponto de dados sobre N fontes; alerta sobre discrepâncias em range |
| **Avaliação de 3 Cenários** | `three-scenario` | Cálculo preciso de preço-alvo Otimista/Base/Pessimista |
| **Detecção da Lei de Benford** | `benford` | Detectar anomalias em distribuição de primeiro dígito de dados financeiros |
| **Calculadora de Precisão** | `calc` | Calcular com precisão qualquer fórmula financeira — substituir aritmética de LLM |

**Princípio de Design**: Todos os cálculos usam Python `decimal.Decimal` (aritmética decimal precisa), nunca `float` (aproximação de ponto flutuante). No contexto financeiro, `0.1 + 0.2 = 0.3` nunca deve falhar.

---

## Direção Futura

- [ ] Backtest Histórico: Relatórios de Pesquisa AI vs. Desempenho Real de Preço de Ação
- [ ] Framework de Análise de Ciclo Macroeconômico
- [ ] Feed de Dados em Tempo Real através de MCP (Wind / Bloomberg / Yahoo Finance)

---

## Aviso Legal

Este projeto é apenas para fins educacionais e de pesquisa, e não constitui aconselhamento de investimento. Investimentos envolvem risco; exercer julgamento cauteloso. Sempre conduzir sua própria diligência (DYOR).

---

## Licença

MIT License

---

> "O melhor investimento que você pode fazer é em si mesmo." — Warren Buffett
>
> AI Berkshire: Para que todos tenham seu próprio time de pesquisa de investimento.

## Histórico de Estrelas

Se este projeto foi útil para você, por favor dê uma estrela!

[![Star History Chart](https://api.star-history.com/svg?repos=xbtlin/ai-berkshire&type=Date)](https://star-history.com/#xbtlin/ai-berkshire&Date)
