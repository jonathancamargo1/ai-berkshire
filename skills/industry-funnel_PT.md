# Filtragem de Funil da Indústria: Processo de Seleção de Investimento de Valor de 30-60 Empresas para 3

Execute filtragem de funil de seleção de investimento de valor para $ARGUMENTS indústria/direção, desde varredura de mercado até seleção de 3 alvos principais.

## Cenários Aplicáveis

Quando você menciona uma indústria ou direção de investimento (como "Poder de Computação AI", "Medicamentos Inovadores", "Robótica"), desejando:
1. Não deixar passar nenhum alvo importante (incluindo ações A, Hong Kong, EUA, candidatos não-listados)
2. Usar critérios unificados para filtrar "ações de histórias" e empresas com qualidade insuficiente
3. Concentrar energia nos realmente 3 melhores que valem pesquisa profunda
4. Cada camada tem critério claro, rastreável e revisável

Diferença com `industry-research`:
- `industry-research` enfatiza estrutura de cadeia industrial e visão geral
- `industry-funnel` enfatiza filtragem de seleção de ações, refinando de mercado inteiro para 3

Os dois podem ser complementares: primeiro usar `industry-research` para entender estrutura da indústria, depois usar `industry-funnel` para selecionar alvos.

---

## Visão Geral da Estrutura de Funil

```
Camada 1: Varredura de Mercado Inteiro     30-60 empresas   (atividade+variação+valor top 30)
        ↓ 5 Indicadores Hard de Investimento de Valor
Camada 2: Filtragem Grosseira             ≤ 10 empresas   (5 aprovados + fosso protetor ★★★+)
        ↓ Análise Detalhada
Camada 3: Análise Detalhada                 ≤ 10 empresas  (cada 300-500 caracteres análise estruturada)
        ↓ Seleção Final
Camada 4: Análise Profunda de Quatro Mestres     3 empresas     (cada 800-1200 caracteres, perspectiva dos 4)
        ↓
Saída: Recomendação de Investimento + Sinal Operacional + Sugestão de Posição
```

Os alvos "filtrados de cada camada" devem deixar registro de razão de eliminação, não pode ser caixa preta.

---

## Primeira Etapa: Varredura de Mercado Inteiro

### 1.1 Definição de Ação Ativa (Três Categorias Combinadas)

**Categoria A - Atividade de Negociação**:
- Principais 30 em volume médio diário nos últimos 30 dias (A/HK/EUA cada)

**Categoria B - Tabela de Variação**:
- Principais 20 em variação nos últimos 30 dias
- Principais 20 em variação nos últimos 90 dias
- Combinação dos dois

**Categoria C - Âncora de Valor de Mercado**:
- Principais 30 em valor de mercado na indústria (independentemente de sobe/desce)

Combinação final = A ∪ B ∪ C, esperado 30-60 empresas.

### 1.2 Mercados que Deve Pesquisar

| Mercado | Sugestão de Fonte |
|------|----------|
| A-Shares (Shanghai/Shenzhen) | Painel de Indústria de Tonghuashun/Eastmoney, Thinkorswim |
| Hong Kong | Futu/Tonghuashun Hong Kong, HKEX Classificação de Indústria |
| EUA | NASDAQ/NYSE Composições de ETF de Indústria, Yahoo Finance |
| Mercados Internacionais | Empresas de Japan/Coréia/Taiwan/Europa não podem ser perdidas (especialmente semicondutores, eletrônicos) |
| Empresas Não-Listadas | Seção separada "Candidatos Futuros IPO", anotar estimativa e tempo de IPO |

### 1.3 Formato de Saída

| Nome | Código | Mercado | Valor Mercado | Negócio Principais em Uma Frase | % da Indústria | Categoria (A/B/C) |
|-------|------|-----|------|----------|-----------|--------|

**Auto-verificação Importante**:
- % da indústria < 30%, ser cuidadoso com "ações relacionadas", marcar "alvo não puro"
- Mercado China/Ásia, não perder por falta de dados em inglês
- Pequeno valor mercado, não perder por tendência AI favorecer líder

---

## Segunda Etapa: 5 Indicadores Hard de Investimento de Valor para Filtragem Grosseira → ≤ 10 Empresas

Para 30-60 empresas da primeira etapa, aplicar 5 indicadores a cada uma.

### 2.1 5 Indicadores Hard

| # | Indicador | Critério de Aprovação | Condição de Relaxamento | Fonte de Dados |
|---|------|---------|---------|----------|
| 1 | Avaliação PE | Razoável (comparar com faixa histórica, indústria) | Alta crescimento relaxado para PEG < 1,5 | Relatório Financeiro+Wind/Tonghuashun |
| 2 | ROE | > 15% ou tendência de 3 anos melhorando | Indústria intensiva em capital pode relaxar | Relatório Financeiro |
| 3 | Fluxo Operacional | Positivo e >70% do lucro líquido | — | Relatório Financeiro |
| 4 | Taxa de Alavancagem | < 60% | Utilidades/Energia podem relaxar para 70% | Relatório Financeiro |
| 5 | Avaliação Rápida de Fosso Protetor | ★★★+ | — | Julgamento Qualitativo |

**5 Tipos de Fosso Protetor**:
- Marca/Poder de Preço
- Custo de Troca/Pegajosidade de Usuário
- Efeito de Rede
- Efeito de Escala
- Barreira Técnica/Licença/Recurso

### 2.2 Formato de Saída

| Empresa | PE | ROE | Fluxo Op/Lucro Líq | Taxa Alavancagem | Fosso Protetor | Combinado | Manter/Eliminar | Razão Eliminação |
|------|----|----|-----------|--------|-------|------|------|--------|

**Regra de Retenção**:
- 5 aprovados → Manter direto
- 4 aprovados + 1 próximo → Manter com marcação amarela
- Menos de 4 → Eliminar, anotar razão

**Meta**: Manter ≤ 10 empresas. Se manter muito (> 12), aumentar fosso para ★★★★ e peneirar novamente.

---

## Terceira Etapa: Análise Detalhada (≤ 10 empresas, cada 300-500 caracteres)

Para empresas mantidas na filtragem grosseira, fazer análise estruturada.

### 3.1 Modelo de Análise por Empresa

```
## {Nome Empresa}（{Código}）

**Modelo de Negócio em Uma Frase**:
（O que vende, para quem, como arrecada）

**Qualidade Financeira**:
- Crescimento de Receita / Crescimento de Lucro / Margem Bruta / ROE / Fluxo de Caixa
- Mudanças-chave（Ponto de inflexão financeira mais importante últimos 1-2 anos）

**Profundidade do Fosso Protetor**:
- Tipo principal de fosso protetor + Evidência específica
- Se ainda existir fosso protetor em 5 anos: Julgamento breve

**Principais Riscos（Top 3）**:
1.
2.
3.

**Avaliação Rápida**:
- PE/PS/EV/EBITDA atual + Posição na faixa histórica
- Comparação com indústria
- Conclusão em uma frase: Caro / Razoável / Barato

**Entrar nos 3 Finais?**：Sim / Não（Razão）
```

### 3.2 Critério de Seleção dos 3 Finais

Não é pela classificação, mas por "Complementaridade da Carteira":
- Pelo menos 1 "Alta Certeza Baixa Flexibilidade"（Tipo Buffett）
- Pelo menos 1 "Média Certeza Média Flexibilidade"（Tipo Crescimento）
- Opcionalmente 1 "Alta Flexibilidade Alto Risco"（Tipo Opção）

Se não encontrar 3 adequados em alguma sub-trilha, melhor escrever "2 Finais + 1 Observação" do que forçar 3.

---

## Quarta Etapa: Análise Profunda dos Quatro Mestres（3 Empresas, cada 800-1200 caracteres）

Executar análise profunda de perspectiva dos quatro mestres nos 3 finais.

### 4.1 Perspectiva Duan Yongping: Essência do Negócio

- Definir em uma frase o negócio que esta empresa faz
- É um bom negócio? Por quê?
- Qual é a "essência" deste negócio? A gestão se desviou?
- Onde está a "continuidade" do modelo de negócio?

### 4.2 Perspectiva Buffett: Profundidade do Fosso Protetor

- Classificar cinco tipos de fosso（★1-5）, listar evidência específica
- Este fosso ainda vai existir em 10 anos?
- Onde está a "margem de segurança" de compra agora?

| Fosso Protetor | Intensidade | Evidência Específica |
|-------|------|--------|
| Marca/Poder de Preço | | |
| Custo de Troca | | |
| Efeito de Rede | | |
| Efeito de Escala | | |
| Barreira Técnica/Licença | | |

### 4.3 Perspectiva Munger: Risco e Modo de Falha

- Como esta empresa provavelmente vai falhar?（Listar 3 caminhos de falha）
- Quanto vale no pior cenário?（Avaliação minimalista）
- Por que pessoas inteligentes não compram?（Argumentação reversa）
- Tem risco moral/conformidade/gestão?

### 4.4 Perspectiva Li Lu: Posicionamento de Mudança de Civilização

- A trilha desta empresa é "Mudança de Paradigma de Nível Civilizacional" ou "Boom de Curto Prazo"?
- Qual revolução tecnológica histórica é mais próxima?
- Qual é o endgame desta empresa em 10-20 anos?
- É estrutura "Winner-Take-All"?

### 4.5 Grau de Recomendação Combinado

```
Grau de Recomendação: ★★★★☆
Tipo de Posição: Núcleo / Satélite / Opção / Observação
Intervalo de Compra Sugerido: Preço Atual / Recuação N% / Esperar Pacientemente
Porcentagem de Posição Sugerida: X% da Posição deste Tema
Indicador Crítico de Monitoramento: （Se a lógica desta empresa se inverter, qual é o sinal）
```

---

## Quinta Etapa: Saída Combinada

Fim do relatório integra:

### 5.1 Tabela de Combinação dos 3 Finais

| Empresa | Tipo | Grau de Recomendação | Posição Sugerida | Lógica Principal | Risco Principal |
|------|------|-------|---------|---------|----------|
| A | Núcleo | ★★★★★ | 50-60% | | |
| B | Satélite | ★★★★☆ | 25-35% | | |
| C | Opção | ★★★☆☆ | 5-15% | | |

### 5.2 ETF de Nível da Indústria como Substituto

Se não quer selecionar ações, listar 1-3 ETF relacionados（A/HK/EUA）。

### 5.3 Julgamento de Posição Geral da Indústria

- Histórico PE/PB percentil da indústria
- Fluxo de Fundos（Conexão do Norte, Resgate de ETF, Densidade de Cobertura de Vendedor）
- Indústria está em que estágio （Inicial/Expansão/Maduro/Declínio）

### 5.4 Auto-Avaliação de Grau de Informação （Preenchimento Obrigatório）

| Dimensão | Nível | Explicação |
|-----|------|-----|
| Integridade de Dados Financeiros da Empresa | A/B/C | |
| Atualidade de Dados de Avaliação | A/B/C | |
| Julgamento de Estrutura da Indústria | A/B/C | |
| Informação de Gestão | A/B/C | |

A = Dados Suficientes Confiáveis; B = Parcialmente Faltando mas Sem Afetar Conclusão Principal; C = Muito Faltando, Conclusão Precisa de Cautela.

### 5.5 Pontos de Dados Pendentes de Atualização

Listar claramente: Quais dados são estimativas, quais precisam verificação posterior, qual relatório trimestral precisa acompanhamento.

### 5.6 Lista de Fontes de Informação

Link de origem de cada dado/conclusão, listado por categoria (Relatório, Relatório Analista, Notícias, Relatório Indústria).

---

## Preconceito de Pesquisa AI（Importante）

Processo de filtragem de funil onde AI facilmente tropeça:

| Preconceito | Manifestação | Resposta |
|------|-----|------|
| Preferência por Líder | Grandes dados empresa, análise longa, parece "melhor" | Classificar por critério hard e fosso, não por comprimento relatório |
| Preferência por Inglês | Dados EUA ricos, A/HK fácil subestimar | Pesquisar Chinês/Inglês, não perder A/H empresa |
| Preferência por Histórias | Variação alta + Calor mídia = Melhor "ação conceito AI" | Distinguir "% de receita AI" vs "% de história AI", ver negócio real |
| Preferência por Agora | Empresa com finança boa agora fácil selecionar, perder dark horse período transição | Filtragem nível 2 permite "tendência melhora" como relaxamento |
| Preferência por Listado | Apenas empresa listada perder melhor jogador trilha | Deve listar "Candidato IPO Futuro", anotar estimativa e tempo |

---

## Requisitos de Saída

1. **Localização Relatório**: `reports/{Nome Indústria}-funnel-{YYYYMMDD}.md`（Relatório indústria colocar raiz reports/）
2. **Língua**: Chinês
3. **Estilo**: Direto, agudo, sem conversa boba
4. **Dados**: Todo dado anotar fonte; valor estimado marcar "estimado"
5. **Não Pré-Definir Postura**: Primeiro dados → Depois lógica → Depois conclusão. Conclusão deve vir naturalmente dos dados
6. **Dois Lados**: Cada julgamento principal anexar contra-argumento（"Mas por outro lado..."）, deixar leitor pesar
7. **Deixar Registro de Eliminação de Cada Camada**: Empresa eliminada também deixar nome+razão

---

## Verificação de Dados（Fluxo de Saída）

Após escrever relatório, executar verificação de dados, passar apenas após aprovação:

```bash
# Etapa 1 — Extrair Lista de Verificação（15% Amostragem Aleatória）
python3 tools/report_audit.py extract \
  --report <Caminho arquivo relatório>

# Etapa 2 — Para cada item na lista, obter dados de fonte confiável（Ver skills/financial-data.md）

# Etapa 3 — Saída Verdict Aprovado/Rejeitado
python3 tools/report_audit.py verdict \
  --results '<JSON Preenchido>' \
  --report <Nome arquivo relatório>
```

**【Aprovado】** Todos passaram → Relatório pode ser publicado；**【Rejeitado】** Algum falhou → Corrigir depois reanalisar.

---

## Próximas Ações

Após 3 finais de funil, para cada um pode executar separadamente:
- `/investment-team` —— Pesquisa Profunda Paralela Completa de Quatro Mestres（Sub-diretório + 5 Documentos）
- `/investment-checklist` —— Sistema Buffett Checklist Pré-Compra Completamente
- `/management-deep-dive` —— Pesquisa Profunda de Gestão

`industry-funnel` é entrada, skill depois é escavar profundo.