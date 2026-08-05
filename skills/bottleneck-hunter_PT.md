# Caçador de Gargalos da Cadeia de Suprimentos: Arbitragem de Gargalos Impulsionada por IA

Execute verificação de gargalos da cadeia de suprimentos e descoberta de oportunidades de arbitragem para $ARGUMENTS.

## Conceito Principal

Não pergunte "que ação a IA recomenda", pergunte "se esta tendência continuar expandindo, qual elo ficará sem capacidade?"

A pesquisa de investimento tradicional se concentra em líderes e em setores conhecidos. Este sistema funciona ao contrário: **partindo da gargalo físico da cadeia de suprimentos, encontrando empresas que ninguém nota mas que toda a indústria precisaria parar se ficassem sem estoque**.

O excesso de retorno vem de: o primeiro nível de gargalos (GPU, HBM, energia) já está totalmente precificado. O verdadeiro alfa está no **segundo e terceiro níveis** — módulos ópticos, lasers, substratos InP, wafers SOI, equipamento de epitaxia, teste em nível de wafer, placas IC, fibra de vidro especial, etc.

## Etapa 1: Confirmação de Supertendências

### 1.1 Critérios de Seleção de Tendências

Não procure ilusões em pequenas tendências, apenas persiga supertendências que atendem a TODOS os critérios:

| Critério | Requisito | Método de Verificação |
|----------|-----------|----------------------|
| Continuidade | Crescimento garantido de 3-5 anos | Pesquise previsões da indústria, planos de despesas de capital |
| Físico | Requer construção real de hardware/materiais/equipamento | Diferencie "atualização de software" de "expansão física" |
| Escala | Despesas globais de capital > $50 bilhões/ano | Pesquise planos de capex dos principais atores |
| Aceleração | Crescimento da demanda > velocidade de expansão de capacidade | Compare taxa de crescimento de demanda vs planos de expansão de capacidade |

### 1.2 Lista Atual de Supertendências Rastreadas

Atualize a cada execução, lista inicial:

1. **Construção de Infraestrutura de IA** — data centers, clusters GPU, interconexão de rede, energia
2. **Transição Energética** — reinício nuclear, atualização de rede, armazenamento
3. **Modernização de Defesa** — ciclo de aumento de gastos militares ocidentais, reestruturação de cadeia de suprimentos
4. **Reindustrialização de Semicondutores** — subsídios EUA/Europa/Japão para construção de fábricas, gargalos de equipamento/materiais
5. **Economia Espacial** — Internet via satélite, aumento de frequência de lançamento

Se o usuário especificar uma tendência específica (como "Infraestrutura de IA"), concentre-se apenas nessa tendência.

### 1.3 Saída de Verificação de Tendências

```
Nome da Tendência:
Força motriz principal: (uma frase)
Eventos de verificação que já ocorreram (pelo menos 3):
  1. [Data] [Evento] [Fonte]
  2.
  3.
Escala de despesas de capital: aproximadamente $XX bilhões/ano, crescimento YY%
Avaliação de lacuna oferta-demanda: Crescimento de demanda > expansão de capacidade de suprimento? Sim/Não/Incerto
Confirmação de tendência: ✅ Rastreável / ❌ Evidência insuficiente, não rastrear ainda
```

## Etapa 2: Decomposição Física da Cadeia de Suprimentos

### 2.1 Estrutura de Decomposição em Camadas

**Não se fixe em conceitos, decomponha em entidades físicas**.

```
Camada 0 (Terminal): Produto/serviço final
    |
Camada 1 (Componentes Principais): Componentes principais já bastante observados
    |                 ⬆ Preço adequado, alfa limitado
    |─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
    |                 ⬇ Atenção baixa, alfa concentrado
    |
Camada 2 (Subcomponentes/Materiais): Peças e materiais que sustentam componentes principais
    |
Camada 3 (Equipamento/Matérias-primas): Equipamento e matérias-primas para fabricar subcomponentes
    |
Camada 4 (Infraestrutura): Energia, resfriamento, terra, talento, certificação
```

### 2.2 Modelo de Decomposição: Infraestrutura de IA

```
Camada 0: Serviço de treinamento/inferência de modelo de IA
Camada 1: GPU/acelerador, memória HBM, servidor, data center
Camada 2 (área de varredura de prioridade):
  ├─ Interconexão óptica: módulo óptico, fibra óptica, chip de comutação, cabo de cobre
  ├─ Óptica principal de comunicação: laser (EML/VCSEL/CW), modulador, fotodetector
  ├─ Material semicondutor: substrato InP, substrato GaAs, wafer SOI, substrato SiC
  ├─ Embalagem avançada: placa CoWoS, TSV HBM, substrato ABF
  ├─ PCB/Placa: PCB de alta frequência/alta velocidade, placa IC, fibra de vidro especial
  ├─ Teste: teste de nível de wafer (Probe Card), teste de envelhecimento, ATE
  ├─ Resfriamento/Arrefecimento: sistema de refrigeração líquida, CDU, resfriamento por imersão
  └─ Conexão de energia: canaleta, UPS, painel de distribuição, transformador
Camada 3:
  ├─ Equipamento de epitaxia: MOCVD, MBE
  ├─ Fotolitografia/Gravura: litografia de comprimento de onda especial, gravura de InP
  ├─ Matéria-prima: metal de alta pureza (índio, gálio, germânio), gás especial, alvo
  └─ Certificação/Padrão: padrão MSA, certificação Telcordia
Camada 4:
  ├─ Energia: energia nuclear, geração a gás natural, transmissão e distribuição
  ├─ Água/resfriamento de infraestrutura
  └─ Terra de data center/licenças
```

### 2.3 Decomposição de Outras Tendências

Para cada supertendência confirmada, execute decomposição similar. Use WebSearch:
- "{tendência} supply chain bottleneck 2026"
- "{tendência} shortage critical component"
- "{tendência} capacity constraint"
- "{tendência} sole source supplier"

## Etapa 3: Identificação de Gargalo — Procurando a "Garganta"

### 3.1 6 Critérios de Determinação de Gargalo

Para cada segmento nas Camadas 2-3, avalie sistematicamente:

| # | Critério | Pergunta | Pontuação |
|---|----------|----------|----------|
| 1 | **Concentração de oferta** | Fornecedores globais ≤ 3? | 🔴 ≤2 / 🟡 3-5 / 🟢 >5 |
| 2 | **Ciclo de expansão de produção** | Quanto tempo leva para nova capacidade? | 🔴 >2 anos / 🟡 1-2 anos / 🟢 <1 ano |
| 3 | **Dificuldade de substituição** | Pode ser substituído por outra tecnologia/material? | 🔴 Não substituível / 🟡 Parcialmente / 🟢 Fácil |
| 4 | **Taxa de utilização de capacidade** | Taxa atual de utilização de capacidade? | 🔴 >90% / 🟡 70-90% / 🟢 <70% |
| 5 | **Crescimento de demanda** | Taxa de crescimento de demanda a jusante? | 🔴 >50%/ano / 🟡 20-50% / 🟢 <20% |
| 6 | **Ciclo de validação de cliente** | Quanto tempo leva para novo fornecedor ser validado? | 🔴 >1 ano / 🟡 6-12 meses / 🟢 <6 meses |

**Classificação de gargalo**:
- 🔴🔴🔴 ≥4 → **Gargalo de Nível S** (ponto único de falha, prioridade máxima)
- 🔴🔴 3 → **Gargalo de Nível A** (severamente limitado)
- 🔴 1-2 → **Gargalo de Nível B** (sob pressão mas controlável)
- Nenhum 🔴 → Não é gargalo, pule

### 3.2 Saída do Mapa de Gargalos

```
Mapa de Gargalos da Cadeia de Suprimentos — {Nome da Tendência}
Data de Atualização: AAAA-MM-DD

Gargalos de Nível S (Ponto Único de Falha):
  1. [Nome do Segmento] — [Motivo em uma frase] — Fornecedores: [Lista de Empresas]
  2.

Gargalos de Nível A (Severamente Limitado):
  1.
  2.

Gargalos de Nível B (Sob Pressão):
  1.
  2.

Mudanças Recentes (vs. varredura anterior):
  - [Novo/Elevado/Reduzido/Resolvido] [Nome do Segmento] — [Motivo]
```

## Etapa 4: Seleção de Empresa — Do Gargalo ao Ativo

### 4.1 Para cada gargalo de Nível S e A, encontre todas as empresas listadas relevantes

Métodos de busca:
- WebSearch "{nome do segmento de gargalo} supplier listed company"
- WebSearch "{nome do produto de gargalo} manufacturer stock"
- WebSearch "{compartilhamento de mercado do produto de gargalo} company"

### 4.2 Critérios de Pré-filtro (Rápida Eliminação)

| Critério | Requisito | Motivo |
|----------|-----------|--------|
| Status de listagem | Listado (A/HK/US/JP/TW/EU) | Negociável |
| % de negócio de gargalo | >30% de receita do segmento de gargalo | Pureza |
| Valor de mercado | Preferencialmente < $100 bilhões USD | Já totalmente precificado |
| Liquidez | Volume médio diário > $1 milhão USD | Pode entrar/sair |

### 4.2.1 Verificação de Valuation (Obrigatório, Não Pode Ser Ignorado)

**Gargalo real ≠ Oportunidade de investimento.** Você DEVE calcular PS e PE para cada empresa e anotá-lo no relatório. Use os seguintes critérios compostos para determinar se a valuation está comprometida:

#### Luz Vermelha de Valuation (Atender qualquer um → Limite de força de sinal ★★, etiqueta "⚠️ Valuation Comprometida")

1. **Valor de Mercado > 20% do TAM**: Valor de mercado da empresa já ultrapassa 20% do tamanho de mercado que pode atingir, indicando que as expectativas de crescimento já foram internalizadas excessivamente
2. **PS > 30x E Crescimento de Receita < 100%**: Valuation alta mas crescimento insuficiente para sustentar. Empresas com crescimento >100% estão isentas da linha vermelha de PS, mas ainda devem ser marcadas como "⚠️ Valuation alta requer validação contínua de crescimento"
3. **Valor de Mercado > 10x Previsão de Receita de 5 Anos Otimista**: Mesmo se todas as suposições otimistas forem realizadas, a precificação atual permanece muito alta
4. **Preço dobrou em 60 dias após emissão de novas ações**: Forte sinal de impulsionamento emocional, reduzir força do sinal de um nível

#### Luz Amarela de Valuation (Requer Explicação Adicional, Senão Reduzir de Nível)

1. **Prejuízo + PS > 15x**: Permitir entrar em ★★★ mas DEVE explicar caminho para lucratividade e calendário
2. **PS é 5 vezes superior ao de empresas lucrativas do mesmo setor**: DEVE explicar fonte de prêmio (participação de mercado, diferença de crescimento, diferença de proteção)
3. **PE > 80x**: Calcular PEG e explicar se a velocidade de crescimento suporta

#### Luz Verde de Valuation (Itens de Bônus)

- PS < 10x E receita em crescimento → força do sinal pode subir de um nível
- PE < 30x E com proteção → marcar "valuation possui margem de segurança"

#### Verificação de Razoabilidade de Valuation (Obrigatório)

Para cada ativo responda: "Ao adquirir ao valor de mercado atual, assumindo o cenário mais otimista totalmente realizado, saindo a 25x PE em 10 anos, qual é o retorno anualizado?" Retorno anualizado < 10% → marcar "Preço atual carece de margem de segurança".

**Nota**: O objetivo da verificação de valuation é evitar recomendar "empresa de PS 100x com prejuízo", não eliminar todas as empresas de valuation alta. A chave é se a velocidade de crescimento, TAM e estrutura competitiva podem sustentar a valuation atual, requerendo análise específica em vez de regras mecânicas.

### 4.3 Dimensões de Peneiramento Profundo

Para empresas que passaram no pré-filtro, avalie cada uma:

```
## {Nome da Empresa} ({Código})

**Posicionamento de Gargalo**:
- Localização específica na cadeia de suprimentos
- Participação de mercado: Global # X, Proporção XX%
- Lista de clientes (conhecidos)

**Capacidade e Expansão**:
- Capacidade atual / Taxa de utilização
- Plano de expansão de capacidade / Cronograma
- Financiamento necessário para expansão vs caixa existente

**Snapshot Financeiro**:
- Valor de mercado / Receita / Lucro / Taxa de crescimento
- Proporção da receita de negócio de gargalo
- Tendência de margem bruta (gargalo apertado = margem deve subir)

**Checklist de Verificação de Risco**:
- [ ] Risco de tecnologia substituta: Pode ser contornado?
- [ ] Risco de diluição: Tem muita emissão/conversíveis?
- [ ] Risco geográfico: Localizado em área sensível/controlado por exportação?
- [ ] Risco de gestão: Tem histórico desfavorável?
- [ ] Risco de concentração de clientes: Dependência excessiva de cliente único?
- [ ] Valuation comprometida: A valuation atual já reflete 3 anos de crescimento?

**Avaliação de Persistência de Gargalo**:
- Quando este gargalo será eliminado?
- Depois de eliminado, o que a empresa ainda tem?
- É único ou recorrente?
```

## Etapa 5: Verificação Cruzada — Não Ouça Apenas Uma História

### 5.1 Verificação de Direção Positiva

| Item de Verificação | Pergunta | Método de Busca |
|-------------------|----------|------------------|
| Validação de cliente | Clientes principais já fecharam/estão em ramp-up? | Pesquise anúncios da empresa, menção em relatórios de clientes |
| Validação de receita | O gargalo já apareceu no crescimento de receita? | Pesquise últimas 2-3 demonstrações de resultado trimestrais |
| Validação de preço | Produto está subindo de preço? | Pesquise preços de indústria, relatórios de analistas |
| Validação de capacidade | Capacidade está realmente apertada? | Pesquise dados de prazos de entrega, reclamações de clientes |
| Validação de capital | Há despesa de capital de expansão? | Pesquise orientação de capex da empresa |

### 5.2 Verificação de Direção Oposta (Estilo Munger)

| Pergunta de Direção Oposta | Significado |
|----------------------------|-------------|
| Por que pessoas inteligentes não compram esta ação? | Encontre argumentos bearish conhecidos |
| Este gargalo pode ser contornado? Qual é a rota alternativa? | Risco de rotas técnicas |
| China/outros players conseguem replicar rapidamente capacidade? | Risco de choque de suprimento |
| Se demanda final cair 50%, o que acontece com esta empresa? | Sensibilidade de downside |
| Gestão fez emissão em alta passada? | Confiabilidade da gestão |
| Que pressupostos de crescimento a valuation atual implica? | Razoabilidade de valuation |

### 5.3 Validação Cruzada de Sinais

- Todas as empresas do mesmo gargalo estão subindo? (Validação setorial)
- Clientes a jusante mencionam tensão de suprimento em relatórios? (Validação de cliente)
- Associações da indústria/pesquisa tem dados relevantes? (Validação de terceiros)

## Etapa 6: Saída — Painel de Oportunidades de Gargalo

### 6.1 Tabela de Ranking de Oportunidades de Gargalo

| Ranking | Empresa | Código | Valor de Mercado | Receita Anual | PS | PE | Segmento de Gargalo | Classificação de Gargalo | Participação de Mercado | Crescimento de Receita | Força de Sinal | Julgamento de Valuation |
|---------|---------|--------|------------------|--------------|----|----|--------------------|----------------------|----------------------|---------------------|------------------|-----------------------|
| 1 | | | | | x | x | | S/A | | | ★1-5 | Razoável/Acima da Média/Excessiva |

**Campos obrigatórios**: Valor de mercado, receita anual, PS, PE não podem usar "pendente de verificação". Se não conseguir obter dados financeiros, força de sinal não pode exceder ★★.

Avaliação de Força de Sinal (resultado de verificação de valuation afeta diretamente classificação):
- ★★★★★ Múltiplas verificações cruzadas, cliente em ramp-up, receita refletida, luz verde de valuation (PS razoável + lucrativo ou próximo de lucro)
- ★★★★ Maioria das verificações passou, luz verde ou amarela de valuation (requer explicação)
- ★★★ Lógica constitui mas parte pendente de verificação, luz amarela de valuation aceitável (ex.: empresa de alta crescimento em estágio inicial)
- ★★ Sinal inicial, ou lógica de gargalo constitui mas luz vermelha de valuation (valor de mercado >20% TAM, PS>30x sem crescimento suficiente, valor de mercado muito acima de previsão de 5 anos)
- ★ Conceito puro, não verificado

### 6.2 Resumo de Uma Página Para Cada Oportunidade

```
🎯 {Nome da Empresa} ({Código}) — {Posicionamento de Gargalo em Uma Frase}

Por que é Gargalo:
(2-3 frases explicando por que este segmento é ponto de estrangulamento)

Por que Esta Empresa:
(2-3 frases explicando por que esta empresa em vez de outras)

Linha do Tempo de Catalisador:
- Prazo (1-3 meses): [Evento específico, ex.: Relatório, investimento em capacidade, validação de cliente]
- Médio prazo (3-12 meses): [Tendência setorial, marco de expansão]

Risco Principal:
1.
2.

Dados Principais: Valor de Mercado $XX / Receita Anual $XX / PS Xx / PE Xx / Crescimento de Receita XX% / % de Negócio de Gargalo XX%

Verificação de Margem de Segurança de Valuation: Ao adquirir ao valor de mercado atual, sair em 25x PE em 10 anos, requer lucro líquido atingir $XX, receita correspondente $XX (X vezes hoje), retorno anualizado XX%. Conclusão: Tem/Sem margem de segurança.

Status de Verificação Cruzada: ✅ Validação de Cliente / ✅ Validação de Receita / ✅ Valuation Razoável / ⚠️ Valuation Excessiva / ❌ Item Não Verificado

Conclusão: Vale aprofundar pesquisa / Adicionar à lista de observação / Não rastrear por enquanto
```

### 6.3 Recomendação de Ação

| Ativo | Ação Recomendada | Motivo |
|-------|-----------------|--------|
| A | Executar `/investment-team` pesquisa profunda | Gargalo nível S + múltiplas verificações |
| B | Adicionar à lista de observação, aguardar próximo relatório trimestral | Lógica constitui mas receita não refletida ainda |
| C | Não rastrear por enquanto | Risco de tecnologia alternativa muito alto |

## Etapa 7: Manutenção Dinâmica de Mapa de Gargalo — Atualização Incremental

### 7.1 Atualização Incremental a Cada Execução

1. Verifique se gargalos identificados ainda são válidos
   - Tem novos fornecedores entrando?
   - Capacidade já se expandiu para resolver gargalo?
   - Tecnologia alternativa teve avanço?

2. Varredura de novos gargalos emergentes
   - Pesquise últimos 7 dias de notícias sobre cadeia de suprimentos / gargalo / escassez
   - Verifique disclosure de cadeia de suprimentos em relatórios de temporada de lucros

3. Atualize classificação de gargalo (upgrade/downgrade/resolvido)

### 7.2 Arquivo de Estado

Mantenha em diretório `reports/bottleneck-map/`:
- `master-map.md` — Mapa de gargalo geral (atualização contínua)
- `watchlist.md` — Lista de observação (atualização contínua)
- `AAAA-MM-DD/` — Uma pasta por dia, contendo todos os relatórios de varredura daquele dia
- `deep-dive/` — Empresas sob análise profunda em arquivo individual

## Modo de Varredura a Cada Hora (Uso de Tarefas Agendadas)

Execute uma vez por hora, usando modo "saia de relatório apenas quando houver conteúdo":

### Fluxo de Varredura (Cada Hora)

1. **Varredura de Notícias**: Pesquise notícias de cadeia de suprimentos das últimas 1-2 horas
   - Palavras-chave: supply chain bottleneck, shortage, capacity constraint, allocation, lead time, sole source, 瓶颈, 缺货, 产能, 涨价
   - Cobertura: Fontes em inglês + chinês
2. **Sinal de Mercado**: Verifique mudanças de preço de empresas rastreadas (foco em anomalias >5%)
3. **Relatório/Comunicado**: Verifique se empresas relevantes de gargalo lançaram relatório ou comunicado importante
4. **Oportunidade de Valuation**: Verifique se empresas em watchlist entraram em zona de compra por queda geral
5. **Decidir se Produzir Relatório**:
   - Tem novo sinal de gargalo, tem oportunidade de ativo clara, tem mudança de estado significativa → **Produzir Relatório**
   - Sem descobertas novas → **Não produzir relatório**, apenas registre no log "Esta rodada sem novos sinais"

### Regra de Saída de Relatório

**Uma pasta por dia**: `reports/bottleneck-map/AAAA-MM-DD/`

**Convenção de Nomenclatura** (veja nome do arquivo rapidamente se há ativos):

| Situação | Formato de Nome de Arquivo | Exemplo |
|----------|---------------------------|----------|
| Encontrou ativo claro | `HH-MM-código-ativo1-código-ativo2.md` | `09-00-FORM-IBDN.md` |
| Tem sinal de gargalo mas sem ativo claro | `HH-MM-signal-scan.md` | `14-00-signal-scan.md` |
| Sem descobertas novas | Não gera arquivo | — |

**Código de ativo no nome do arquivo = Passou verificação de valuation, vale pesquisa profunda.** Empresas que aparecem apenas em fase de varredura de sinal mas não passaram em valuation NÃO vão para o nome do arquivo.

### Modelo de Relatório (Quando Tem Ativo)

```markdown
# Caçador de Gargalo — AAAA-MM-DD HH:MM

## Ativo Claro

### {Nome da Empresa} ({Código}) — {Posicionamento de Gargalo em Uma Frase}

**Por Que Vale Atenção Agora**: (Evento específico ou mudança de dados que acionou esta varredura)

**Posicionamento de Gargalo**: Camada X, {Nome do Segmento}, Classificação de Gargalo S/A/B
**Snapshot Financeiro**: Valor de Mercado $XX / Receita Anual $XX / PS Xx / PE Xx / Crescimento de Receita XX%
**Verificação de Valuation**: Luz Vermelha/Amarela/Verde (Explicação específica)
**Verificação de Margem de Segurança de Valuation**: Usando método de saída em 25x PE em 10 anos, retorno anualizado XX%

**Lógica de Viés Altista** (2-3 pontos):
1.
2.

**Lógica de Viés Baixista** (2-3 pontos):
1.
2.

**Recomendação**: Executar pesquisa profunda / Adicionar à observação / Aguardar preço melhor

---

## Outros Sinais (Sem Ativo Claro)

| Segmento | Sinal | Fonte | Julgamento Inicial |
|---------|-------|-------|------------------|

## Status da Lista de Observação

(Upgrade/Downgrade/Novo/Removido, sem mudanças escrever "Sem mudanças")
```

### Modelo de Relatório (Apenas Varredura de Sinal)

```markdown
# Varredura de Sinal de Caçador de Gargalo — AAAA-MM-DD HH:MM

## Novo Sinal

| Segmento | Descrição de Sinal | Fonte | Tem Ativo Negociável? | Próximo Passo |
|---------|------|------|--------|--|

## Status da Lista de Observação

Sem mudanças / Tem mudanças (listar)
```

## Consciência de Viés de Pesquisa em IA

| Viés | Manifestação | Contra-medida |
|------|-------|----------|
| Preferência por Grande Capitalização | Resultados de busca dominados por empresas de grande capitalização | Pesquise pequena capitalização fornecedora, adicione "small cap" palavra-chave |
| Preferência por Inglês | Falta empresas japonesas, coreanas, taiwanesas | Pesquise mercados Japão/Coreia/Taiwan fornecedores |
| Preferência por Narrativa | Atraído por etiqueta "conceito de IA" | Foque apenas em posição real de cadeia de suprimentos, ignore etiqueta de mercado |
| Viés de Confirmação | Procure confirmação após encontrar gargalo | Força validação de direção oposta (Etapa 5) |
| Viés de Recência | Depende de informação desatualizada | Priorize pesquisa últimos 30 dias dados |

## Princípio Principal (Prioridade Máxima)

1. **Não deixe a IA recomendar ações, deixe a IA decompor a cadeia de suprimentos** — A pergunta é mais importante que a resposta
2. **Físico em primeiro lugar** — Foque apenas em segmentos que requerem produtos/materiais/equipamento físico real
3. **Segundo e terceiro níveis** — Não persiga gargalos de primeiro nível já totalmente precificados
4. **Validação cruzada** — Cada conclusão requer ao menos 2 fontes independentes
5. **Honesto sobre incerteza** — Se não conseguir dados, escreva "dados insuficientes", não preencha com suposições
6. **Gargalos têm vida útil** — Cada gargalo eventualmente será resolvido, a chave é calcular a janela de tempo
7. **Pequena capitalização ≠ boa oportunidade** — Pequena capitalização também pode ser empresa ruim, DEVE passar verificação de qualidade financeira
8. **Gargalo real ≠ oportunidade de investimento** — Uma empresa pode estar sentada no gargalo mais apertado, mas se PS>30x ou ainda com prejuízo, preço atual não é ponto de compra. **Valuation é porta rígida, não pode ser sobrescrita por pureza de gargalo, força de sinal ou atratividade de narrativa.** Melhor perder uma ação de gargalo que subiu, do que comprar uma empresa com prejuízo a PS 100x.
9. **Obedeça princípio de objetividade em CLAUDE.md** — Não pré-julge inclinação, apresente dados primeiro depois conclusão

## Requisitos de Saída

1. **Localização de Relatório**:
   - Varredura Completa: `reports/bottleneck-map/{nome-tendência}-bottleneck-{AAAAMMDD}.md`
   - Varredura Diária: `reports/bottleneck-map/daily/{AAAA-MM-DD}-{am/pm}.md`
   - Mapa Geral de Gargalo: `reports/bottleneck-map/master-map.md`
   - Lista de Observação: `reports/bottleneck-map/watchlist.md`
2. **Idioma**: Chinês
3. **Estilo**: Direto, afiado, sem blá blá
4. **Dados**: Todos os dados anotados com fonte; valores estimados marcados "estimado"
5. **Sem posição pré-estabelecida**: Apresente dados primeiro → Conduza lógica → Saia conclusão
6. **Ambos os lados**: Cada julgamento essencial tem contra-argumento