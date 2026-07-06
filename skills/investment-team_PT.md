# Habilidade de Equipe de Investimento - Estrutura de Análise de Quatro Mestres em Paralelo

Realizar análise de pesquisa de investimento em equipe para $ARGUMENTS. Use a ferramenta Team para criar uma verdadeira equipe de pesquisa com múltiplos Agentes em paralelo.

## Fluxo de Execução

### Passo Um: Exibir Estrutura da Equipe

Exiba a estrutura da equipe a seguir, confirme com usuário antes de iniciar:

| Função | Responsabilidade | Estrutura de Análise |
|--------|------------------|---------------------|
| **team-lead**(você mesmo) | Coordenação geral, síntese de pesquisa, relatório final | Estrutura integrada dos quatro mestres |
| **business-analyst** | Análise de modelo de negócio & defensibilidade | Perspectiva de Duan Yongping |
| **financial-analyst** | Análise de demonstrações financeiras & avaliação | Perspectiva de Warren Buffett |
| **industry-researcher** | Panorama industrial & situação competitiva | Perspectiva de Charlie Munger |
| **risk-assessor** | Avaliação de risco & qualidade da administração | Perspectiva de Li Lu |

### Passo Um e Meio: Avaliação de Viés de Pesquisa de IA

Antes de criar a equipe, exiba ao usuário a avaliação de "pesquisabilidade de IA" da empresa:

**Classificação de Riqueza de Informações** (determina estratégia de pesquisa):
| Nível | Características | Ajuste de Estratégia de Pesquisa |
|------|------------------|------------------------------|
| Nível A (Informação Abundante) | Listada há vários anos, cobertura ampla de analistas | Foco da equipe em **verificação inversa** e **perspectivas não-consensuais**, evitar saída de "conversa correta mas inútil" alinhada com mercado |
| Nível B (Informação Adequada) | Recentemente listada, cobertura limitada | Dados inferidos por cada Agent devem ser marcados com nível de confiança, síntese de team-lead deve marcar "adequação de dados" |
| Nível C (Informação Escassa) | Nicho/Recentemente listada/Mercado emergente | Equipe converte para "modo de primeiro princípio": não busca integridade de relatório, foca em poucas questões centrais sobre essência do negócio |

**Lembrete Fundamental**: mais informação ≠ certeza maior, menos informação ≠ certeza menor. Confiança que IA pode gerar ≠ certeza real de investimento. Certeza vem do modelo de negócio em si, não da quantidade de materiais. 

Comunique classificação a cada Agent, afetando seu método de pesquisa.

### Passo Dois: Criar Equipe

Use TeamCreate para criar equipe:
- team_name: `{nome_empresa}-research` (lowercase inglês, ex: `meituan-research`)
- agent_type: `team-lead`

### Passo Três: Criar 4 Tarefas

Use TaskCreate para criar as 4 tarefas seguintes (cada uma com subject, description, activeForm):

#### Tarefa 1: Análise de Modelo de Negócio
- subject: `Analisar modelo de negócio de {empresa}, defensibilidade e valor ao usuário`
- description inclui:
  1. Essência do modelo de negócio: definição do negócio principal, estrutura de receita
  2. Como o efeito de voo da plataforma/produto funciona
  3. Análise de defensibilidade: marca/custo de mudança/efeito de rede/efeito de escala/barreira técnica, validar cada
  4. Valor ao usuário/cliente: que valor único foi criado para cada parte
  5. Matriz de negócio e efeitos sinérgicos
  6. Avaliação de padrão de "bom negócio" de Duan Yongping: diferenciação, poder de precificação, vantagem competitiva sustentável
  7. Exigir busca de informações públicas recentes: demonstrações financeiras, relatórios da indústria

#### Tarefa 2: Análise Financeira e Avaliação
- subject: `Analisar dados financeiros de {empresa}, capacidade de lucro e avaliação`
- description inclui:
  1. Tendência de receita, lucro líquido, lucro operacional em 3-5 anos
  2. Indicadores de capacidade de lucro: ROE, ROA, margem bruta, margem de lucro operacional
  3. Análise de fluxo de caixa: fluxo de caixa operacional, fluxo de caixa livre, despesas de capital
  4. Saúde do balanço patrimonial: reservas de caixa, taxa de dívida, liquidez
  5. Análise de avaliação: PE/PS/PB/EV, comparação com histórico e industria
  6. Avaliação de margem de segurança: valor intrínseco vs preço atual
  7. **Validação de Rigor Financeiro (DEVE usar Bash para chamar ferramentas, proibido cálculo mental)**:
     - Verificação de valor de mercado: `python3 tools/financial_rigor.py verify-market-cap --price {preço} --shares {ações em circulação} --reported {valor de mercado informado} --currency {moeda}`
     - Verificação de avaliação: `python3 tools/financial_rigor.py verify-valuation --price {preço} --eps {EPS} --bvps {valor patrimonial por ação}`
     - Validação cruzada de dados-chave: `python3 tools/financial_rigor.py cross-validate --field {campo} --values '{JSON}' --unit {unidade}`
     - Avaliação de três cenários: `python3 tools/financial_rigor.py three-scenario --price {preço} --eps {EPS} --shares {ações em bilhões} --growth {otimista} {neutro} {pessimista} --pe {PE otimista} {PE neutro} {PE pessimista}`
     - Incorporar resultados da ferramenta diretamente no relatório como registro de validação

#### Tarefa 3: Análise Industrial e Competitiva
- subject: `Analisar panorama industrial de {indústria} e situação competitiva de {empresa}`
- description inclui:
  1. Escala e crescimento industrial: tamanho de mercado, taxa de crescimento, taxa de penetração
  2. Panorama competitivo: participação de mercado de competidores principais, comparação de estratégias competitivas
  3. Avaliação de ameaça de competidores principais: analisar cada competidor principal
  4. Panorama de cada segmento de nicho
  5. Tendências industriais: mudança tecnológica, impacto de políticas, novos entrantes
  6. Análise da cadeia de valor: distribuição de valor entre upstream, midstream e downstream
  7. Exigir busca de dados e dinâmica competitiva mais recente da indústria

#### Tarefa 4: Avaliação de Risco e Administração
- subject: `Avaliar risco de investimento de {empresa} e qualidade da administração`
- description inclui:
  1. Avaliação da administração: esfera de competência do CEO, integridade, visão estratégica, capacidade de alocação de capital, qualidade histórica de decisões
  2. Risco regulatório: impacto regulatório atual e potencial
  3. Risco competitivo: avaliação de nível de ameaça de cada competidor
  4. Risco operacional: perda de novos negócios, incerteza de expansão
  5. Risco macroeconômico: impacto de ciclo econômico e ciclo industrial
  6. Estrutura de governança: estrutura de ações, transações associadas, política de retorno ao acionista
  7. Certeza de longo prazo: como estará a empresa em 10 anos? O que pode desapropriação seu modelo de negócio?
  8. Exigir busca de dinâmica regulatória recente, discursos da administração

### Passo Quatro: Iniciar 4 Agentes em Paralelo

Use ferramenta Task para iniciar simultaneamente 4 Agentes (**DEVE chamar 4 vezes Task na mesma mensagem em paralelo**):

Cada Agent configurado como:
- `subagent_type`: `general-purpose`
- `run_in_background`: `true`
- `team_name`: nome de equipe correspondente
- `name`: nome de função correspondente (business-analyst / financial-analyst / industry-researcher / risk-assessor)

Cada Agent prompt template:

Você é "{nome_função_chinês}" da equipe de pesquisa de investimento de {empresa}, responsável por analisar {empresa} da perspectiva de investimento de {nome_mestre}.

Faça a tarefa #
{número_tarefa}: {subject_da_tarefa}

Exigências específicas:
{conteúdo_description_da_tarefa}

**Método de Pesquisa**:
- Use WebSearch para buscar informações públicas mais recentes (demonstrações financeiras, relatórios da indústria, notícias)
- **Dados financeiros DEVEM vir de duas fontes independentes**, execute segundo normas em `skills/financial-data.md` (US: macrotrends+stockanalysis; HK: aastocks+macrotrends; China: Eastmoney+巨潮资讯), erro entre duas fontes >1% deve ser marcado
- Garanta precisão de dados, marque dados-chave com fonte
- Análise profunda, não superficial

**Requisitos de Saída**:
- Relatório detalhado, use tabelas Markdown para apresentar dados-chave
- Cada dimensão de análise deve ter conclusão clara e avaliação
- Fim do relatório deve ter conclusão geral desta dimensão

**Após Conclusão**:
1. Use TaskUpdate para marcar tarefa #
{número_tarefa} como completed
2. Use SendMessage para enviar relatório de análise completo ao team-lead (type: "message", recipient: "team-lead")

### Passo Cinco: Receber Relatórios e Rastrear Progresso

- Exiba em tempo real tabela de progresso (quais Agentes completaram, quais ainda pesquisam)
- Cada relatório recebido, atualize progresso e exiba pontos-chave do relatório (3-5 itens)
- Aguarde até que todos os 4 relatórios estejam prontos

### Passo Seis: Fechar Membros da Equipe

Todos os relatórios recebidos, envie shutdown_request aos 4 Agentes (use SendMessage, type: "shutdown_request").

### Passo Sete: Síntese de Relatório Final

Sintetize os 4 relatórios de análise, exiba relatório final com estrutura seguinte:

---

#### 1. Conclusão em Uma Frase
> Use 1 parágrafo (50-100 palavras) para resumir se vale a pena investir e lógica principal

#### 2. Tabela de Avaliação de Quatro Dimensões
| Dimensão | Estrutura | Avaliação(1-5 estrelas) | Julgamento Principal |
|----------|-----------|---------------------|---------------------|

Avaliação Integrada: X / 5

#### 3. Visão Rápida de Dados Principais
Tabela de indicadores financeiros e operacionais principais (comparação últimas 2 anos)

#### 4. Resumo de Análise de Cada Dimensão
Cada dimensão extraia 3-5 descobertas mais importantes

#### 5. Proposição de Investimento (Bull vs Bear)
- 🟢 Lógica de otimismo (5-7 itens)
- 🔴 Lógica de pessimismo (5-7 itens)

#### 6. Checklist Pré-Compra de Buffett
| # | Item de Verificação | Passou? | Explicação |
|---|-------------------|---------|------------|
10 itens de verificação principais, avaliar cada um

#### 7. Recomendação de Investimento Final
- Tabela de julgamento qualitativo (qualidade do negócio/administração/avaliação/timing)
- Tabela de recomendação operacional em camadas (agressivo/prudente/conservador → recomendação + intervalo de preço)
- Catalisadores-chave (sinal de acréscimo/redução cada 3-5 itens)

#### 8. Parágrafo de Resumo
100-200 palavras de resumo final

---

### Passo Oito: Salvar Relatório

Escreva relatório final completo em `~/{nome_empresa}投资研究报告_{data}.md` (formato de data YYYYMMDD).

### Passo Nove: Auditoria de Amostragem de Dados (Fluxo de Aprovação)

```bash
# Passo 1 — Extrair lista de auditoria (amostragem aleatória de 15%)
python3 tools/report_audit.py extract \
  --report <caminho_arquivo_relatório>

# Passo 2 — Para cada item da lista, obter dados de fonte confiável (veja skills/financial-data.md)

# Passo 3 — Saída de decisão de aprovação/rejeição
python3 tools/report_audit.py verdict \
  --results '<JSON_preenchido>' \
  --report <nome_arquivo_relatório>
```

**【APROVADO】** Todos passaram → Relatório pode ser publicado; **【REJEITADO】** Alguns falharam → Corrigir e reauditar.

### Passo Dez: Limpar Equipe

Use TeamDelete para limpar recursos de equipe.

## Notas Importantes

1. **4 Agentes DEVEM ser iniciados em paralelo** — chamar 4 vezes Task na mesma mensagem
2. **Agentes reportam via SendMessage** — não colaboração de arquivo, mas comunicação de mensagem
3. **Precisão de dados** — exigir que Agentes usem WebSearch para buscar dados mais recentes, validação cruzada de dados-chave
4. **Conclusão deve ser clara** — não evitar dar recomendação de compra/observação/evitar e intervalo de preço específico
5. **Toda análise deve ter suporte de dados** — anexar fontes de dados
6. **Paciência necessária** — pesquisa de 4 Agentes leva alguns minutos, atualizar progresso em tempo real ao usuário
7. **Consciência anti-viés** — team-lead ao sintetizar DEVE avaliar: análise de cada Agent é limitada por adequação de dados? Todos convergem demais com consenso de mercado? Relatório final precisa incluir "avaliação de adequação de informação" e "declaração de limitação de pesquisa de IA"
8. **Princípio de honestidade quando informação é escassa** — prefira deixar em branco no relatório marcado "dados insuficientes" em vez de usar suposição para preencher estrutura e fingir certeza