---
name: deep-company-series
description: "AI Berkshire skill: Série de Análise Profunda: Descompondo uma empresa em 8 artigos longos. Source: skills/deep-company-series.md."
---

## Nota do adaptador Codex

Esta skill é gerada a partir de `skills/deep-company-series.md` para que usuários de Claude Code e Codex compartilhem um fluxo de trabalho canonical.

- Trate `$ARGUMENTS` como o pedido do usuário no thread Codex atual.
- Quando a fonte mencionada superfícies exclusivas do Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca web quando necessário, comandos de shell para ferramentas locais e edições normais de arquivo para arquivos de workspace.
- Use ferramentas de projeto compartilhadas de `tools/` neste repositório. Prefira executar comandos a partir da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`; se o thread atual começar fora do repositório, localize primeiro o caminho do checkout real em vez de assumir um caminho fixo de diretório home.
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje; trate como a linha de base para dados "mais recentes" e declare a data de corte dos dados no cabeçalho do relatório. Nunca assuma a data atual a partir dos dados de treinamento.
- Preserve as regras de qualidade de pesquisa de `AGENTS.md`: verificação cruzada de dados financeiros, use ferramentas de aritmética exata para avaliação/matemática e rotule claramente a incerteza e as lacunas de origem.

# Série de Análise Profunda: Descompondo uma empresa em 8 artigos longos

Para $ARGUMENTS, escreva uma série de 8 artigos longos em profundidade para publicação em canais públicos como WeChat Official Accounts/Douyin. **O núcleo da propriedade intelectual não é "saber escrever", mas "saber revisar" — 99% dos artigos financeiros violam os padrões de verificação de fatos desta skill**.

Amostra de referência: `reports/腾讯/《看懂腾讯》/`

---

## Um. Cenários de disparo

O usuário deseja fazer "pesquisa em nível de livro didático" para uma empresa e publicá-la publicamente em **formato de série de artigos longos**. Diferente de um relatório único:
- 8 artigos de aproximadamente 120 mil caracteres, com loop completo de reset cognitivo para estrutura de decisão
- Cada artigo pode ser independente (adequado para compartilhamento único), mas atravessado por um conjunto de avaliação/gestão/julgamento de preço
- Escrito para "leitores dispostos a dedicar 90 minutos para entender uma empresa", não para clientes de corretoras

**Cenários onde esta skill não é apropriada**: relatório único, revisão de trimestre, pesquisa de indústria — use em vez disso `/investment-research`, `/earnings-review`, `/industry-research`.

---

## Dois. Modelo de série (8 artigos)

| # | Modelo de título | Pergunta central | Contagem de palavras |
|---|---------|---------|------|
| 01 | Você pensa que entende X, mas na verdade não | Reset cognitivo: quebre 3 ilusões comuns | 4,000-5,000 |
| 02 | Fosso da empresa X—`<essência da negociação em uma frase>` | Quão profundo é o fosso, ele ainda existe em 5/10 anos | 6,000-8,000 |
| 03 | O maior motor de lucro de X—`<negócio mais lucrativo>` | Qual é o negócio principal, por que pode ser sustentado | 6,000-8,000 |
| 04 | Outra empresa escondida nos livros de X—`<ativo oculto>` | Portfólio de investimentos / subsidiárias / valor oculto | 8,000-10,000 |
| 05 | Na era da IA (ou narrativa atual), X é vencedor ou perdedor | Variável de época: decomponha o impacto da IA por negócio | 8,000-10,000 |
| 06 | Descompondo os demonstrativos financeiros de X no jeito Buffett | Profundidade financeira: margem bruta/FCF/ROE/SBC | 8,000-10,000 |
| 07 | `<Citações de ouro da gestão>`—a gestão de X vale confiança | Disciplina de alocação de capital + verificação de integridade + sucessão | 8,000-10,000 |
| 08 | Quanto custa para comprar, qual sinal deve vender (epílogo da série) | Três cenários DCF + lista de linhas vermelhas + estrutura de posição | 10,000-12,000 |

Adicione um `00-série-explicação.md` como índice de conteúdo, não para publicação.

---

## Três. Normas de estilo de escrita

### Tom de voz

- **Direto, afiado, sem desperdício** — a primeira frase deve fornecer números ou conclusões contraconsensuais
- **Estrutura de investimento em valor** — perspectivas de Buffett/Munger/Duan Yongping/Li Lu interpoladas (mas não amontoar citações)
- **Sem posturas preconcebidas** — exponha dados primeiro, depois deduza lógica, depois chegue a conclusões
- **Apresente ambos os lados** — cada julgamento central deve vir com uma contraposição "mas por outro lado..."
- **Sensação de WeChat** — os primeiros 18-20 caracteres devem se manter independentemente (pré-visualização móvel)

### Palavras proibidas

| Proibido | Razão | Alternativa |
|------|------|------|
| Obviamente / Inevitavelmente / Certamente | Absolutismo subjetivo | Os dados mostram / A evidência indica |
| Eu acho / Eu sinto | Tom subjetivo | Remova ou mude para "de acordo com este framework" |
| Nível de livro didático / Toque divino | Buscadores de tráfego | Descreva fatos concretos |
| Severamente desalinhado / Severamente subavaliado | Palavras fortemente subjetivas | Cite porcentagens de desconto específicas |
| Perfeito / Indefectível | Julgamento unilateral | Adicione observações do lado oposto |

### Estilo de título

- Use **números de contraste** ou **conclusões contra-consensuais** como anzol ("7 tentativas falhadas em 15 anos", "Salário anual de 42,92 milhões representa apenas 0,0165% do lucro")
- Subtítulo neutro e resumido ("—`<julgamento essencial>`")
- **Evite comparações de busca de tráfego**: "mini-Buffett", "versão chinesa de X", "YYDS" completamente evitado
- Use terminologia familiar aos leitores profissionais ("Berkshire" em vez de "Buffett", nome da empresa em vez de nome pessoal)

---

## Quatro. Checklist rigoroso de verificação de fatos (núcleo de propriedade intelectual)

### Armadilhas de "pseudo-precisão" a ter cuidado antes de escrever

1. **Valor esperado ponderado por probabilidade**: `30% × A + 50% × B + 20% × C = esperado +X%` — este tipo de cálculo é quase sempre lixo — a alocação de probabilidade é pura subjetividade, dando falsa sensação de precisão. **Apenas listar cenários + condições de disparo + direção, não calcular expectativas ponderadas**.
2. **Medições de terceiros de MAU/quota**: As discrepâncias do QuestMobile/Qimai/CBNData são enormes (podem diferir 2-3× no mesmo ponto no tempo). **Use apenas os dois mais confiáveis para comparação, faça descrição qualitativa do resto**.
3. **Extrapolação linear de crescimento histórico**: `2025 com +33% × 5 anos compostos → 2030 X` é predição de analfabeto financeiro. **Hipóteses de cenário + intervalos altos/baixos + não é promessa**.
4. **Percentuais de participação não divulgados**: Empresas não listadas como ByteDance, Halti **nunca divulgaram participações**. **Forneça intervalo, marque "desconhecido"**.
5. **Atribuição forte**: O fracasso do concorrente = porque X. Liste múltiplas causas, **este artigo não faz atribuição única**.

### 7 verificações obrigatórias durante revisão

```
□ 1. Consistência numérica entre artigos: capitalização de mercado total, lucro líquido Non-IFRS, percentuais-chave de participação alinhados em toda a série
□ 2. Anotação de metodologia: Non-IFRS / GAAP / Non-IFRS-SBC / FCF qual usar, claro em todo o texto
□ 3. Varredura de dupla contagem: subsidiárias já consolidadas não em "portfólio de investimentos", SOTP não duplo contabilizado
□ 4. Equidade em comparações horizontais: não pode ser "negócio principal PE (excluindo caixa + portfólio)" vs "concorrente PE (não excluído)"
□ 5. Todas as expectativas ponderadas por probabilidade deletadas: veja acima
□ 6. Todas as afirmações absolutizadas enfraquecidas: grep "obviamente|inevitavelmente|severamente|nível-livro-didático|perfeito"
□ 7. Anotação de origem de dados de terceiros: cada peça de dados não-financeiro deve vir com "(Fonte: X)" depois
```

### Preferência de modelo

Antes de escrever, **liste erros históricos já conhecidos**:
- Múltiplos de retorno histórico: deve usar acumulado da entrada (ex. Riot 33× não 58×)
- Percentuais de participação: deve verificar mais recentes Futu/demonstrações financeiras (ex. Tencent hold Meituan 1.5% não 6.4%)
- Tratamento contábil de "distribuição de dividendos": considerar ganho de alienação sob IFRIC 17 na data de declaração (ex. JD em 2021, Meituan em 2022 mas quantidade pequena)
- Total de ações refletirá: SBC concentrado no início do ano deixará ações curto prazo subir

---

## Cinco. Processo de execução

### Fase 1: Pesquisa (completar antes de escrever artigos 01-02)

1. Ler relatórios anuais dos últimos 5 anos, último trimestre
2. Ler pelo menos 3 relatórios de vendedor independentes (encontrar consenso + anti-consenso)
3. Usar `/investment-team` ou `/investment-research` para gerar primeiro rascunho de pesquisa interna
4. Confirmar com usuário os 8 pontos-chave dos artigos (evitar descobrir direção errada após escrever)

### Fase 2: Escrita (escrever em ordem 01→08, não pule)

- Após escrever cada artigo, salve em `reports/{公司名}/《看懂{公司名}》/0X-XX.md`
- Não push GitHub imediatamente — espere revisão do usuário
- Após feedback de revisão do usuário, modifique
- Após revisão completa push git

### Fase 3: Varredura de consistência entre artigos (após escrever todos os 8)

Dispache agente Explore para verificação paralela dos 8 artigos:
1. Se os mesmos números (capitalização, lucro líquido, percentuais de participação) são consistentes entre artigos
2. Se os mesmos termos (FBS, SBC, Non-IFRS) são explicados na primeira aparição
3. Relacionamentos de referência: artigo 02 diz "veja detalhes no artigo 06" se realmente corresponde
4. Recapitulação de pontos-chave vs corpo principal se os números são consistentes

### Fase 4: Verificação final pré-publicação

```bash
# Deve fazer grep local uma vez antes de push (sob regras de privacidade ai-berkshire)
grep -r "<nome-usuario-local>\|/Users/\|<informação-identidade-pessoal>" reports/ | head
```

Com certeza então `git pull --rebase && git commit && git push`.

---

## Seis. Processo de tratamento de feedback de revisão

Quando o usuário der feedback de revisão, processe na seguinte ordem:

### 1. Primeiro verifique fatos (não mude diretamente)

Se o usuário disser "dados X estão errados", primeiro use Bash/Read para encontrar dados originais e verificação cruzada:
- Veja outros relatórios de earnings/financeiros dessa empresa no ai-berkshire
- Veja Futu/divulgações oficiais
- Forneça comparação de três vias "dados que usuário disse vs dados que encontrei vs dados que usei antes"

### 2. Julgue o nível de revisão

| Nível | Tipo | Tratamento |
|------|------|----------|
| 🔥 Erro duro | Números errados, atribuição errada, metodologia errada | Deve mudar, sem hesitação |
| ⚠️ Subjetivação | Palavras fortemente subjetivas, absolutismo, comparações de busca de tráfego | Enfraqueça ou remova |
| 🔬 Granularidade | Anotação de origem, refinamento de metodologia | Prioridade baixa, equilibre com legibilidade |
| ❓ Não confiável | Disparidade de medições de terceiros | **Deletar é mais seguro do que mudar** (instruções claras do usuário) |

### 3. Verificação vinculada após revisão

Ao mudar um lugar, pense "quais outros lugares vão referenciar esse número/conceito". Por exemplo:
- Mudou capitalização total → mude PE / PE de negócio principal / desconto / FCF Yield em toda série
- Mudou percentual de participação → mude ranking TOP 10 + tabela de participação histórica + lista de redução
- Mudou metodologia do termo → mude primeira definição + referências posteriormente + recapitulação de pontos-chave

### 4. Reporte imediatamente após push

```
Push bem-sucedido (hash de commit).
[N] resumo de revisões totais [com tabela]:
- O que mudou
- O que mudou vinculado
- O que ainda não mudou

Esperando próximas instruções.
```

---

## Sete. O que esta skill não faz

- **Não toma decisão de investimento para leitores** — todas as seções finais têm "não constitui conselho de investimento"
- **Não prediz preço de ação** — apenas fornece "cenários + condições de disparo"
- **Não calcula "retorno anualizado esperado" valor ponderado** — alocação de probabilidade subjetiva enganará leitores
- **Não escreve "o grande X também mantém"** — usar participação de outros para endossar seu julgamento é anti-investimento em valor
- **Não força 8 artigos completos** — se um artigo não tem conteúdo independente suficiente (ex. gestão da empresa não é especial), mescle com outros ou reduza número de artigos

---

## Oito. Conformidade e privacidade

- Todos os relatórios públicos **apenas usam informações públicas** (demonstrações financeiras, divulgações oficiais, relatórios de vendedor, instituições de terceiros conhecidas)
- Não use nenhuma **informação pessoal do usuário** (apelido da empresa, IM interno, informações de participação não divulgadas)
- Antes de push, use grep para varrer nome de usuário local / `/Users/` / nome real e outros campos de privacidade
- Assinatura pública segue estratégia de identidades em camadas do usuário, não misture

---

## Uma sentença para resumir

**A capacidade central de escrever "Entender X Série" ≠ escrever bem, mas revisar com rigor** —
89% dos artigos longos financeiros morrem de números pseudo-precisos, expectativas ponderadas por probabilidade subjetivas, afirmações absolutizadas. A existência desta skill é para marcar todos esses pits, evitar antes de escrever, limpar completamente depois.