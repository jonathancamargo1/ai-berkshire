---
name: quality-screen
description: "AI Berkshire skill: Filtro de qualidade: 7 indicadores para eliminar rapidamente empresas não-primeira classe. Fonte: skills/quality-screen.md."
---

## Nota do adaptador Codex

Esta skill é gerada a partir de `skills/quality-screen.md` para que usuários de Claude Code e Codex compartilhem um único fluxo de trabalho canônico.

- Trate `$ARGUMENTS` como o pedido do usuário na thread Codex atual.
- Quando a fonte mencionar superfícies apenas de Claude, como Task, Agent, WebSearch, Bash, Read ou Write, use a capacidade Codex mais próxima disponível nesta sessão: subagentes quando disponíveis, busca web quando necessário, comandos shell para ferramentas locais e edições normais de arquivos para arquivos do workspace.
- Use ferramentas de projeto compartilhadas de `tools/` neste repositório. Prefira executar comandos a partir da raiz do repositório com caminhos como `python3 tools/financial_rigor.py ...`; se a thread atual começar fora do repo, localize o caminho de checkout real em vez de assumir um caminho fixo no diretório home.
- Antes de iniciar a pesquisa, execute o comando `date` para confirmar a data de hoje; trate como a base de dados "mais recentes" e declare a data de corte de dados no cabeçalho do relatório. Nunca assuma a data atual a partir de dados de treinamento.
- Preserve as regras de qualidade de pesquisa de `AGENTS.md`: verificação cruzada de dados financeiros, uso de ferramentas aritméticas exatas para avaliação/matemática e marcação clara de incerteza e lacunas de fonte.

# Filtro de Qualidade: 7 Indicadores para Eliminar Rapidamente Empresas Não-Primeira Classe

Execute filtro de indicadores de qualidade para $ARGUMENTS, eliminando rapidamente targets que não atendem padrão de empresa primeira classe.

**Formato de entrada suportado**:

| Forma entrada | Exemplo | Descrição |
|---------|------|----------|
| Ação individual | `Tencent, Meituan, NVIDIA` | Filtro cada uma |
| Indústria | `Indústria cerveja China` `Cloud computing global` `Marca desportiva H-shares` | Pesquisa primeiro principais empresas listadas daquela indústria (10-20), depois filtro cada uma |
| Mercado/índice | `Constituintes Hang Seng` `CSI 300` `NASDAQ 100` | Puxe lista constituintes, filtro cada uma |
| Tema | `China 50 de alto dividendo` `Cadeia IA compute global` | Pesquisa primeiro empresas relacionadas tema, depois filtro cada uma |

Em modo indústria/mercado/tema, saída adicional contém: estatística de taxa aprovação, classificação dentro indústria, resumo comparação de setor.

## Princípio de Design

- **Alvo**: Não erro matar nenhuma empresa primeira classe boa, mas consegue eliminar certo não primeira classe
- **Lógica**: 7 indicadores rígidos + 2 regras de isenção, melhor deixar passar do que matar por engano
- **Aplicação**: Todas empresas listadas (Banco/seguro não se aplica condição 3 de cobertura de juros)

---

## 7 Indicadores de Filtro de Qualidade

| # | Indicador | Condição eliminação | O que mede |
|---|------|---------|----------|
| 1 | ROE média 10 anos | < 8% | Eficiência capital —— dinheiro acionista consegue vencer custo oportunidade? |
| 2 | Fluxo caixa livre acumulado 5 anos | Negativo | Ouro real —— lucro é "riqueza papel" ou "riqueza real"? |
| 3 | Múltiplo cobertura de juros (EBIT/juros) | < 2x | Segurança reembolso —— capacidade pagar juros |
| 4 | Margem bruta longo prazo | < 15% | Poder de preços —— produto/serviço tem diferenciação? |
| 5 | Fluxo caixa operacional / lucro líquido (média 5 anos) | < 0.7 | Qualidade lucro —— lucro ganho consegue cobrar caixa? |
| 6 | Margem lucro líquido longo prazo | < 5% | Capacidade resistir risco —— lucro zero quando receita oscila? |
| 7 | Diluição total shares 5 anos | > 20% (não de M&A) | Interesse acionista —— administração está diluindo seu direito? |

## 3 Regras de Isenção

### Isenção A: Isenção período investimento estratégico (aplica ao #1)

Se simultaneamente satisfaz 3 condições, consegue isentar #1 ROE insuficiente:
1. Listada menos de 10 anos
2. Margem bruta > 30% (prova modelo comercial tem poder de precificação)
3. Últimos 2 anos fluxo caixa operacional positivo (prova capacidade de geração de caixa já estabelecida)

**Lógica**: Margem bruta alta+fluxo caixa positivo prova modelo comercial certo, ROE baixo só porque ainda em período de investimento. Caso típico: Meituan.

### Isenção B: Isenção de taxa lucro baixo ativo (aplica ao #6)

Se simultaneamente satisfaz 2 condições, consegue isentar #6 margem lucro líquido insuficiente:
1. Margem bruta > 30% (tem capacidade ganhar mas escolhe não ganhar)
2. Últimos 2 anos margem lucro líquido já voltou acima 5%, ou tendência clara de aumento

**Lógica**: Margem bruta alta prova ter poder de precificação, margem lucro baixo é escolha estratégica (re-investimento) não capacidade insuficiente. Caso típico: Amazon.

### Isenção C: Isenção modelo margem fina alto turnover (aplica ao #4 e #6)

Se simultaneamente satisfaz 3 condições, consegue isentar #4 margem bruta e #6 margem lucro líquido insuficiente:
1. ROE > 20% (prova embora margem lucro baixa, mas taxa retorno capital extremo alta)
2. Fluxo caixa operacional/lucro líquido > 1.0 (qualidade lucro sem problema)
3. Modelo comercial é tipo "membro/comissão plataforma/margem fina alto turnover" (lucro não se mostra em margem bruta)

**Lógica**: Algumas empresas primeira classe lucro não está em margem bruta, está em taxa membro, comissão plataforma ou eficiência turnover. Margem bruta e margem lucro naturalmente baixa, mas ROE alto prova eficiência capital primeira classe. Caso típico: Costco (margem bruta 12%, margem lucro 2.5%, mas ROE 25%+, taxa renovação membro 90%+).

---

## Fluxo de Execução

### Passo Um: Analisar entrada, determinar escopo filtro

**Julgamento de modo**:
- Se entrada é empresa específica/código → **modo ação individual**, direto ao passo dois
- Se entrada é indústria/mercado/tema → **modo batch**, execute primeiro operação:
  1. Use WebSearch para pesquisar principais empresas listadas daquela indústria/mercado/tema
  2. Modo indústria: cobrir top 15-20 empresas listadas daquela indústria
  3. Modo índice: puxe lista constituintes completa
  4. Modo tema: pesquise empresas relacionadas, cobrir 15-30 empresas
  5. Liste lista de empresa completa para confirmação (se empresa > 30, processe em batch paralelo)

Para cada empresa confirme nome completo, código, bolsa.

### Passo Dois: Coleta de dados em paralelo

Para cada empresa inicie Agent independente em background, use WebSearch para pesquisar seguintes dados:

1. **ROE**: ROE de cada ano dos últimos 10 anos (ou desde listagem), calcule média
2. **Fluxo caixa livre**: Fluxo caixa operacional e despesa capital dos últimos 5 anos, calcule FCF acumulado 5 anos
3. **Cobertura de juros**: EBIT e despesa de juros do ano mais recente, calcule múltiplo
4. **Margem bruta**: Tendência margem bruta dos últimos 5 anos
5. **Fluxo caixa operacional/lucro líquido**: Proporção dos últimos 5 anos, calcule média
6. **Margem lucro líquido**: Tendência margem lucro líquido dos últimos 10 anos, calcule média
7. **Mudança total shares**: Total shares 5 anos atrás vs atual, calcule proporção diluição

Prioridade fonte de dados: Relatório anual empresa > Pesquisa corretora > Plataforma dados financeiros

### Passo Três: Verificação linha por linha

Para cada empresa, verifique linha por linha 7 indicadores:
- ✅ Passou
- ❌ Não passou
- ⚠️ Limite (anexe valor como descrição)

Se violou certa linha, verifique se satisfaz condição isenção correspondente.

### Passo Quatro: Saída resultado

#### Formato saída

```markdown
# Resultado de Filtro de Qualidade

**Data filtro**: {data hoje}
**Quantidade empresa**: {N} empresas

## Tabela Resumo

| Empresa | ①ROE | ②FCF | ③Cobertura juros | ④Margem bruta | ⑤OCF/NI | ⑥Margem lucro | ⑦Diluição | Resultado |
|------|------|------|----------|---------|---------|---------|-------|----------|
| xxx | ✅ 24% | ✅ | ✅ | ✅ 56% | ✅ | ✅ 30% | ✅ | **Passou** |
| yyy | ❌ 3% | ❌ | ❌ | ✅ 20% | ✅ | ❌ 2% | ✅ | **Eliminada** |
| zzz | ⚠️→✅ | ✅ | ✅ | ✅ 35% | ✅ | ⚠️→✅ | ✅ | **Isenção Passou** |

## Empresas que passaram (N empresas)
[Lista]

## Empresas eliminadas (N empresas)
| Empresa | Indicador violado | Dados específicos | Razão eliminação |
|------|---------|---------|----------|

## Empresas isenção passou (N empresas)
| Empresa | Cláusula isenção | Dados específicos | Razão isenção |
|------|---------|---------|----------|

## Controvérsia de limite (se houver)
[Explicação adicional para empresas próximo limiar]

## Resumo de setor (modo indústria/mercado específico)

**Taxa aprovação**: {número passou}/{total} = {percentagem}
**Julgamento qualidade indústria**: [conforme taxa aprovação dê avaliação de qualidade geral indústria]

| Estratificação qualidade | Empresa | Traço em comum |
|---------|------|----------|
| Primeira classe (passou tudo+ROE alto) | xxx, yyy | ... |
| Aprovado (passou tudo mas indicador médio) | aaa, bbb | ... |
| Eliminado | ccc, ddd | ... |

**Conclusão seleção de ação de indústria**: [resumo em uma frase se esta indústria vale aprofundar, qual 2-3 empresas mais vale atenção]
```

---

## Pontos de Atenção

1. **Banco/seguro**: Não se aplica #3 (cobertura de juros), modelo comercial essência é operação de spread de juros
2. **REIT**: ROE pode oscilar muito de reavaliação de propriedade, use "ROE de lucro operacional núcleo" substituir
3. **Dados insuficientes**: Se certo dado não consegue obter, anotar "dados insuficientes" em vez de julgar direto passou/não passou
4. **Indústria cíclica**: Use média de ciclo completo (pelo menos cobrir pico alto e pico baixo), não use ano individual
5. **Listagem tempo curto**: Menos 5 anos empresa use todos dados disponível, mas em resultado anotar "janela dados insuficiente"

## Declaração de Limitação

Este conjunto indicadores consegue eliminar "certo não bom" empresa, mas passou filtro não igual "certo bom". Empresa que passou ainda precisa pesquisa mais aprofundada:
- Modelo comercial consegue sustentável?
- Administração consegue confiar?
- Avaliação atual razoável?
- Paisagem competição piora?

Filtro de qualidade é passo um, não é passo final.