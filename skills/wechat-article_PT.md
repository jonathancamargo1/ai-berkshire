# Skill de Artigo WeChat - Transformando Relatórios Técnicos em Artigos de Público

Transforme relatórios de pesquisa de investimento áridos em artigos WeChat interessantes e envolventes para leitura geral.

## Características

- Remover detalhes técnicos, manter pontos-chave
- Adicionar narrativa e visualização de dados
- Direcionado para leitores comuns, sem necessidade de conhecimento financeiro

## Filosofia de Design

Um bom artigo de WeChat precisa atender três dimensões simultaneamente:
1. **Profundidade** — à altura de quem gasta tempo lendo (responsabilidade do autor)
2. **Legibilidade** — estrutura clara, ritmo bom, não desestimula (responsabilidade do editor)
3. **Realmente compreensível** — leitores-alvo não desistirão no meio (responsabilidade do leitor)

Escrever sozinho é fácil "se agradar a si mesmo" — o escritor acha claro, o leitor não entende. A essência da colaboração de três agentes é **forçar a introdução de perspectiva externa**.

---

## Estágio Um: Pesquisa e Coleta de Materiais

### Passo Um: Esclarecer o Posicionamento do Artigo

Antes de começar a escrever, confirme as seguintes informações (se o usuário não especificar, pergunte ativamente):

| Dimensão | Confirmação Necessária | Valor Padrão |
|----------|----------------------|---------------|
| **Público-alvo** | Nível de conhecimento técnico | Um pouco técnico, mas não especialista neste campo |
| **Profundidade do artigo** | Divulgação/Profundidade média/Muito técnico | Profundidade média (com fórmulas, mas explicadas claramente) |
| **Comprimento do artigo** | Intervalo de palavras | 3000-4000 caracteres |
| **Precisa de materiais originais baixados?** | PDF/Imagens necessárias | Sim |
| **Estilo de escrita** | Formal/Conversacional/Direto | Conversacional (como escrever para amigos inteligentes) |

### Passo Dois: Pesquisa Profunda

Use a ferramenta Agent para iniciar em **paralelo** 2-3 Agentes de Pesquisa para coletar materiais suficientes:

**Agente de Pesquisa A: Pesquisa de Conteúdo Principal**
- Se for interpretação de artigo: baixar PDF, extrair contribuições principais, figuras-chave, resultados experimentais
- Se for tema técnico: buscar desenvolvimentos mais recentes, artigos principais, detalhes técnicos
- Se for tema comercial/investimento: buscar dados mais recentes, relatórios da indústria, panorama competitivo

**Agente de Pesquisa B: Contexto Industrial e Aplicação**
- Buscar implementação desta tecnologia/tema na indústria
- Quais empresas estão usando? Como está o desempenho?
- Tendências mais recentes de desenvolvimento e marcos importantes

**Agente de Pesquisa C (Opcional): Pesquisa Comparativa**
- Comparação de métodos/produtos similares
- Trajetória de desenvolvimento histórico
- Direção de evolução futura

### Passo Três: Organizar Estrutura de Materiais

Após conclusão de todos os Agentes de Pesquisa, organize:
1. **Ponto-chave central** (resumir em uma frase a mensagem principal do artigo)
2. **Dados principais** (3-5 pontos de dados com maior impacto)
3. **Lista de imagens** (que imagens são necessárias, qual é a fonte)
4. **Esboço do artigo** (títulos de 6-8 seções e conteúdo principal)

---

## Estágio Dois: Agente Autor Escreve Rascunho Inicial

Use a ferramenta Agent para iniciar o **Agente Autor** com instruções de escrita detalhadas.

### Modelo de Prompt do Agente Autor

Você é um escritor técnico profundo responsável por escrever um artigo WeChat.

## Público-alvo
{Baseado na confirmação de posicionamento do Passo Um}

## Requisitos de Estilo de Escrita
- Expressão pura em chinês, evite mistura de chinês-inglês (primeiro aparecimento de termos técnicos com inglês, depois use chinês)
- Como divulgação técnica para amigos inteligentes, não tradução de artigos acadêmicos
- Use analogias para ajudar na compreensão, mas analogias devem ser apropriadas, não clichês
- Fórmulas/dados-chave são necessários, mas cada um requer explicação em linguagem simples
- Não use emoji
- Parágrafos não excedem 4 linhas (ambiente de leitura WeChat)

## Conteúdo Principal
{Materiais organizados, dados, argumentos}

## Requisitos de Estrutura do Artigo
1. **Abertura (primeiros 3 parágrafos)**: Deve haver gancho forte — comece com impacto de dados ou conclusão contra-intuitiva, não comece com analogia moderada
2. **Contexto**: Por que isto é importante? Que problema resolve?
3. **Conteúdo principal (2-3 seções)**: Profundidade técnica aparece aqui, mas cada ponto técnico precisa de "tradução em linguagem comum"
4. **Prova/Casos**: Use dados e casos, não fale em abstrato
5. **Impacto/Perspectiva industrial**: O que isto significa para a indústria
6. **Conclusão**: Um julgamento com potencial viral, adequado para ser capturado em screenshot

## Requisitos de Imagem
- Artigos de interpretação de papers: DEVE extrair imagens originais do PDF, insira diretamente no artigo usando `![descrição](caminho relativo)`, não use placeholders `[Fig X: descrição]`
- Método de extração: use pdftoppm para renderizar páginas PDF como PNG de alta resolução (pelo menos 900 DPI), depois use PIL para cortar áreas de tabelas alvo
- Cada imagem não menor que 500KB, garantir alta qualidade
- Imagens armazenadas uniformemente em `assets/{nome_tema_abreviado}/` diretório
- Artigos não-paper: se precisar de imagens, busque e baixe imagens apropriadas, insira diretamente

## Requisitos de Fórmula
- Todos os símbolos matemáticos usam formato LaTeX: inline com `$...$`, fórmulas independentes com `$$...$$`
- Proíbido escrever fórmulas em texto puro (como `> D_KL(P || Q) = ...`), DEVE usar formato renderizável LaTeX
- Cada fórmula seguida de "tradução em linguagem comum"

Escreva o rascunho inicial completo, cerca de {número de palavras alvo} caracteres.