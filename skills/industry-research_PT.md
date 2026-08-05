# Pesquisa de Investimento em Indústria: Varredura Completa da Cadeia de Produção + Framework dos Quatro Mestres

Realizar pesquisa sistemática de cadeia de produção de investimento na indústria de $ARGUMENTS.

## Objetivo de Pesquisa

A partir de um tema/lógica de investimento, complete:
1. Validar cada elo da cadeia lógica de investimento
2. Desenhar o mapa visual completo da cadeia de produção
3. Varrer todas as empresas listadas globalmente (A-share/Hong Kong/EUA/Internacional)
4. Para cada segmento importante, executar análise dos quatro mestres nas empresas líderes
5. Saída: recomendação de configuração de portfólio de nível industrial

---

## Primeira Etapa: Construção e Validação da Cadeia Lógica

### 1.1 Desenhar a cadeia lógica
Use setas para expressar relação causal de "tendência fundamental" para "beneficiários".

### 1.2 Validar cada elo
Para cada seta na cadeia, questione e procure evidências.

### 1.3 Procurar "eventos de validação já ocorridos"
Listar eventos comerciais reais já assinados/implementados (não previsões).

---

## Segunda Etapa: Desenho do Mapa da Cadeia de Produção

### 2.1 Desenhar a estrutura
Decompor a indústria em montante→meio→jusante→segmentos auxiliares.

### 2.2 Identificar características comerciais de cada segmento
Marcar: modelo negócio, margem bruta, formato competitivo, tipo barreira, ciclicidade.

### 2.3 Marcar "segmentos críticos"
Identificar onde oferta é tensa, substituição é difícil, margem é alta.

---

## Enviesamento de Pesquisa em IA: Armadilhas da Pesquisa de Indústria

Pesquisa de indústria é especialmente vulnerável a vieses de dados de IA.

**Vieses de Nível de Indústria**: Preferência por indústrias maduras, subestimação de emergentes, preferência por líderes, preferência por listadas, preferência por inglês.

**Medidas Anti-Viés**: Não apenas listar "empresas que IA encontra facilmente", pesquisar ativamente alvos obscuros. Para pequenas empresas, não reduzir grau apenas porque análise é breve. Marcar "suficiência de informação" A/B/C no relatório final.

---

## Terceira Etapa: Varredura Global de Empresas Listadas

Use ferramenta Task para iniciar Agent em background para busca abrangente.

### Lista de Pesquisa
- Empresas EUA, A-share, Hong Kong, outros mercados internacionais
- ETFs de indústria
- Empresas não listadas importantes

### Para cada empresa colete
- Nome, código ação e bolsa
- Valor de mercado aproximado
- Descrição uma frase
- Se é alvo puro ou diversificado
- Segmento da cadeia

### Formato de Saída
Classifique por segmento, estratifique por certeza: Tier 1 (grande-cap/puro/líder), Tier 2 (média/puro/sub-líder), Tier 3 (pequena/desenvolvimento), Tier 4 (diversificada).

---

## Quarta Etapa: Análise dos Quatro Mestres das Principais Empresas

Para Tier 1 e Tier 2 de cada segmento, execute análise abaixo.

### 4.1 Essência do Negócio (Duan Yongping)
- Definição uma frase, estrutura receita, margem, fluxo caixa
- Este é um bom negócio?

### 4.2 Fosso (Buffett)
Classificação em cinco tipos (★1-5): marca, custo troca, rede, escala, tecnologia.

### 4.3 Risco (Munger)
- Como falha? Valor pior caso? Por que não compra?

### 4.4 Gestão (Duan + Buffett)
- Quem é CEO? Histórico decisões. Propriedade. Avaliação A/B/C.

### 4.5 Avaliação
- PE/PS/EV/EBITDA, comparação, breve avaliação

### 4.6 Recomendação
★★★★★ = posição principal, ★★★★☆ = satélite, ★★★☆☆ = observação, ★★☆☆☆ = opção risco, ★☆☆☆☆ = não recomenda

---

## Quinta Etapa: Avaliação de Risco de Nível de Indústria

### 5.1 Lista de Risco Sistêmico
Elo refutado, tecnologia substituta, política black swan, demanda cicla, bolha avalia.

### 5.2 Analogia Histórica
Encontre tema similar na história, analise endgame: quem venceu? Investidores ganharam?

### 5.3 Auto-verificação de Viés
Narrativa muito perfeita? Ancorado? Efeito rebanho?

---

## Sexta Etapa: Julgamento de Tendência Civilizacional (Li Lu)

- É mudança paradigmática ou frenesi de fase?
- Analogia histórica mais próxima?
- Endgame em 10-20 anos?
- Qual segmento "vencedor tira tudo"? Qual é revolvido?

---

## Sétima Etapa: Recomendação de Portfólio

### 7.1 Portfólio Recomendado
Posit principal 50-60%, satélite 25-35%, opção 5-15%, ETF alternativa.

### 7.2 Sinais de Compra/Venda

### 7.3 Limite Superior de Posição
Baseado na certeza e risco, recomende limite superior percentual.

---

## Oitava Etapa: Memorando de Decisão Abrangente

### Tabela de Avaliação Geral
Cadeia lógica, melhor segmento, fosso, risco, tendência, avaliação.

### Comentários dos Quatro Mestres
Simule comentários sobre a oportunidade.

---

## Requisitos de Saída

1. Todas análises com suporte dados, anexar fontes
2. Tabelas Markdown para dados-chave
3. Diagrama texto para mapa de cadeia
4. Analise 2-3 empresas líderes por segmento
5. Varredura tão completa quanto possível
6. Salve em `~/[indústria]-pesquisa-cadeia-relatório.md`
7. Conclusão clara com alvos, proporções, faixa de preço
8. Fim de cada módulo tem "questão" do mestre

## Verificação de Dados (Processo de Liberação)

Após escrita do relatório, execute verificação de dados, apenas pode publicar se passar.