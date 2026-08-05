---
name: thesis-drift
description: "AI Berkshire skill: Detecção de mudança de tese de investimento: Distinguir mudança de fato vs mudança de redação. Fonte: skills/thesis-drift.md."
---

## Nota do adaptador Codex

Esta skill é gerada a partir de `skills/thesis-drift.md` para que usuários de Claude Code e Codex compartilhem um único fluxo de trabalho canônico.

- Trate `$ARGUMENTS` como o pedido do usuário na thread Codex atual.
- Quando a fonte mencionar superfícies apenas de Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca web quando necessário, comandos shell para ferramentas locais e edições normais de arquivos para arquivos do workspace.
- Use ferramentas de projeto compartilhadas de `tools/` neste repositório. Prefira executar comandos a partir da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`; se a thread atual começar fora do repo, localize o caminho de checkout real em vez de assumir um caminho fixo no diretório home.
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje; trate como a base de dados "mais recentes" e declare a data de corte de dados no cabeçalho do relatório. Nunca assuma a data atual a partir de dados de treinamento.
- Preserve as regras de qualidade de pesquisa de `AGENTS.md`: verificação cruzada de dados financeiros, uso de ferramentas aritméticas exatas para avaliação/matemática e marcação clara de incerteza e lacunas de fonte.

# Detecção de Mudança de Tese de Investimento: Distinguir Mudança de Fato vs Mudança de Redação

Execute detecção de mudança de tese de investimento para $ARGUMENTS.

**Formato de entrada suportado**:
- `nome empresa caminho relatório antigo caminho relatório novo` — especifique dois relatórios de pesquisa ou snapshot de tese para comparação
- `nome empresa reports/{nome empresa}-thesis-data antiga.md reports/{nome empresa}-thesis-data nova.md` — compare dois snapshots de tese com data
- `nome empresa` — localize automaticamente `reports/{nome empresa}-thesis.md` e snapshots históricos no mesmo diretório; se não tiver baseline converta para processamento sem baseline

> "Quando fatos mudam, mudo minha ideia. E você?" —— Keynes
>
> "Flutuação de preço não é mudança de tese, fato mudou é." —— AI Berkshire

## Filosofia de Design

Manter posição longo prazo é mais difícil que ler notícias todo dia, e é distinguir três coisa:
- **Fato mudou**: Receita, margem lucro, paisagem competição, comportamento administração, alocação capital tem mudança verificável
- **Preço mudou**: Emoção de mercado ou múltiplo de avaliação mudou, mas negócio em si não mudou
- **Redação mudou**: Dois relatórios forma de escrever diferente, mas prova e julgamento no fundo não mudaram

Alvo de detecção de mudança de tese de investimento é: **só quando prova muda admita mudança de tese**. Não consegue porque relatório reformulou criar mudança falsa, também não consegue porque preço oscilou julgamento errado de base.

Esta Skill depende de `/thesis-tracker` saída de dimensão estruturada: lista de suposição-chave, lista de linha vermelha, ponto âncora de avaliação, tabela de rastreamento. Quando sem estas estruturas, primeiro complete baseline, depois execute detecção de mudança.

## Fluxo de Execução

### Passo Um: Julgar modo de operação

Analise `$ARGUMENTS`:
- Se forneceu dois caminhos de relatório → entra **modo comparação relatório especificado**
- Se só forneceu nome empresa → pesquise `reports/{nome empresa}-thesis.md` e snapshots históricos, entra **modo comparação snapshot automático**
- Se encontrou só um relatório ou sem baseline histórico → entra **modo processamento sem baseline**
- Se dois relatórios não é mesma empresa → pare e solicite confirmação usuário, não faça julgamento de mudança entre empresas

---

## Modo A: Comparação Relatório Especificado

### A1: Ler e validar dois relatórios

Leia relatório antigo e novo, extraia:
- Data de relatório, nome empresa, código ação
- Tese-chave (5 sentença)
- Lista de suposição-chave
- Lista de linha vermelha
- Ponto âncora de avaliação
- Tabela de rastreamento
- Julgamento de qualidade de administração
- Julgamento de fosso competição
- Recomendação de ação atual (compre / segure / observe / reduza / saia)

Se relatório falta estrutura-chave, primeiro marca "estrutura faltando", mas ainda tenta extrair prova de fundo; não consegue extrair dimensão marca como "não consegue julgar", não consegue inventar conclusão.

### A2: Normalização de prova

Organize prova factual de dois relatórios em mesma tabela:

| Dimensão | Prova relatório antigo | Prova relatório novo | Fonte dados | Consegue verificar? |
|------|-----------|-----------|---------|----------|
| Ponto âncora avaliação | | | | |
| Suposição-chave | | | | |
| Linha vermelha | | | | |
| Qualidade administração | | | | |
| Fosso competição | | | | |

**Só compare prova, não compare redação.** Se relatório novo e antigo só é reformulação sinônima, mudança de ordem, mudança de tom, mas fato de dados e limiar de julgamento não mudaram, julgue como Sem mudança.

### A3: Verificação de valor e avaliação

Todas mudança de valor deve usar `tools/financial_rigor.py` para cálculo exato, proibido cálculo mental de LLM:

```bash
python3 tools/financial_rigor.py verify-valuation \
  --price {preço atual} \
  --eps {EPS} \
  --bvps {valor livro por ação} \
  --fcf-per-share {FCF por ação}
```

Se precisa calcular capitalização, percentagem mudança, diferença preço alvo ou avaliação cenário, use:

```bash
python3 tools/financial_rigor.py verify-market-cap --price {preço} --shares {ações} --reported {capitalização do relatório} --currency {moeda}
python3 tools/financial_rigor.py cross-validate --field {campo} --values '{JSON}' --unit {unidade}
python3 tools/financial_rigor.py three-scenario --price {preço} --eps {EPS} --shares {bilhões de ações} --growth {otimista} {neutro} {pessimista} --pe {PE otimista} {PE neutro} {PE pessimista}
python3 tools/financial_rigor.py calc --expr '{fórmula exata'
```

Dados financeiros-chave devem verificação cruzada de pelo menos dois lugar independente. Fonte insuficiente, calibre inconsistente, não consegue revisar número deve marcar como "baixa confiança / aguardando revisão".

### A4: Julgamento de mudança por dimensão

Use fixamente seguintes dimensões, não aumente/diminua temporário:

| Dimensão | Foco de julgamento | Melhorado | Sem mudança | Enfraquecido |
|------|---------|----------|-----------|----------|
| Ponto âncora avaliação | Valor intrínseco, PE/PB/FCF Yield, margem segurança, intervalo preço alvo | Margem segurança expande ou valor intrínseco melhora e verificado por ferramenta | Intervalo avaliação e margem segurança sem mudança essencial | Margem segurança estreita, valor intrínseco piora ou suposição avaliação falha |
| Lista suposição-chave | Velocidade receita, margem lucro, fluxo caixa, usuário/pedido/capacidade etc suposição verificável | Mais suposição é reforçada por prova novo | Status suposição consistente com prova | Suposição enfraquecida, danificada ou quebrada |
| Lista linha vermelha | Integridade, regulação, queda negócio, quebra competição, ação anormal administração | Risco de linha vermelha original resolvido ou queda significante | Não disparou e nível risco não mudou | Linha vermelha disparou ou probabilidade disparo sobe |
| Qualidade administração | Integridade, alocação capital, recompra dividendo, execução, amizade acionista | Comportamento novo aumenta confiança | Comportamento continua julgamento antigo | Comportamento danifica confiança ou alocação capital piora |
| Fosso competição | Participação mercado, poder preço, efeito rede, vantagem custo, ameaça substituto | Fosso alarga ou vantagem competição é verificada | Paisagem sem mudança essencial | Fosso é enfraquecido ou concorrente quebra |

Cada dimensão só consegue três tipo conclusão: **Melhorado / Sem mudança / Enfraquecido**.

### A5: Regra guiada por prova

Cada conclusão não Sem mudança deve citar prova novo específico que causa mudança:
- Item linha financeira: como velocidade receita, margem lucro, fluxo caixa operacional, quantidade recompra, caixa líquido
- Divulgação regulação: como 10-K/20-F, relatório anual, relatório meio ano, anúncio bolsa, filing SEC
- Evento notícia: como mudança administração, multa regulação, perda cliente principal, quebra competidor
- Preço e avaliação: deve esclarecer isto é "mudança avaliação" ou "mudança base real", não consegue misturar

Se não encontra prova que explica mudança, deve julgar como **Sem mudança** ou **Não consegue julgar**, não consegue usar diferença redação inferir mudança.

### A6: Saída relatório de mudança

#### Estrutura de relatório

```
Um. Objeto comparação e horizonte tempo
Dois. Conclusão geral: tese é mudança?
Três. Tabela mudança de dimensão
Quatro. Detalhe diferença de prova
Cinco. Verificação de valor e número
Seis. Migração de recomendação ação
Sete. Incerto e necessário suplementar fonte
Oito. Próximo foco rastreamento
```

#### Tabela mudança de dimensão

| Dimensão | Julgamento antigo | Julgamento novo | Direção mudança | Prova disparo | Confiança |
|------|-------|-------|:--------:|---------|:------:|
| Ponto âncora avaliação | | | Melhorado / Sem mudança / Enfraquecido | | Alto/Meio/Baixo |
| Lista suposição-chave | | | Melhorado / Sem mudança / Enfraquecido | | Alto/Meio/Baixo |
| Lista linha vermelha | | | Melhorado / Sem mudança / Enfraquecido | | Alto/Meio/Baixo |
| Qualidade administração | | | Melhorado / Sem mudança / Enfraquecido | | Alto/Meio/Baixo |
| Fosso competição | | | Melhorado / Sem mudança / Enfraquecido | | Alto/Meio/Baixo |

**Linha Sem mudança prova disparo escreve `-`, não invente prova para preencher tabela.**

#### Conclusão geral deve responder

1. **Tese é mudança?** Não mudou / Mudança positiva / Mudança negativa / Prova insuficiente não consegue julgar
2. **Mudança vem de onde?** Avaliação / Base real / Administração / Paisagem competição / Evento linha vermelha
3. **É mudança de fato ou mudança de preço?** Claramente separe explicação
4. **Como migração ação recomendada?** Exemplo: Observe → Compre, Compre → Segure, Segure → Reduza, Reduza → Saia
5. **Próximo passo que prova precisa?** Próximo relatório financeiro / Divulgação regulação / Explicação administração / Dados competidor

---

## Modo B: Comparação Snapshot Automático

### B1: Localizar snapshot

Em `reports/` localize:
- `reports/{nome empresa}-thesis.md`
- `reports/{nome empresa}-thesis-*.md`
- Diretório `reports/{nome empresa}/` contém "thesis", "tese", "rastreamento" relatório

Selecione arquivo mais antigo e mais completo como relatório antigo, mais novo como relatório novo. Se usuário especificou data, use especificado.

### B2: Prevenir emparelhamento errado

Antes comparação deve confirmar:
- Nome empresa ou código ação consistente
- Data relatório diferente
- Dois relatórios ambos contém estrutura de tese ou conclusão pesquisa extrável

Se não conseguir confirmar mesma empresa, pare e solicite caminho explícito ao usuário.

### B3: Executar Modo A

Depois localizar dois snapshots válidos, execute completamente Modo A.

---

## Modo C: Processamento Sem Baseline

Se só encontrou um relatório ou não encontrou snapshot antigo:

1. Claramente diga: **Não consegue executar detecção de mudança de tese: falta baseline histórico comparável**
2. Não tente inventar tese antigo com base memória ou impressão de mercado
3. Guie usuário primeiro usar `/thesis-tracker {nome empresa} estabelecer tese` estabelecer baseline estruturado
4. Se relatório atual já bastante completo, consegue sugerir salve como `reports/{nome empresa}-thesis.md` como baseline futuro para detecção mudança

Formato saída:

```
Não consegue executar detecção mudança de tese: falta baseline histórico.

Já localizou:
- Relatório atual: {caminho / não localizou}
- Baseline histórico: não localizou

Sugestão:
1. Primeiro execute /thesis-tracker {nome empresa} estabelecer tese
2. Próximo vez novo relatório financeiro ou evento importante, depois execute /thesis-drift {nome empresa} relatório antigo relatório novo
```

---

## Princípios-Chave

- **Prova prioridade a redação** — Reformulação sinônima não é mudança, só mudança de prova de fato é mudança
- **Base real prioridade a preço** — Oscilação de preço só afeta ponto âncora avaliação, não muda base real de negócio
- **Número deve verificado** — Todos percentagem, múltiplo avaliação, diferença preço alvo devem `tools/financial_rigor.py` verificação
- **Incerto então marca incerto** — Fonte falta, calibre inconsistente, não consegue revisar, não consegue fazer julgamento forte
- **Linha vermelha processa separado** — Disparo de linha vermelha prioridade maior que avaliação barato, não consegue ser coberido por PE baixo
- **Saída deve replicável** — Cada conclusão Melhorado / Enfraquecido deve conseguir rastreamento a prova específica