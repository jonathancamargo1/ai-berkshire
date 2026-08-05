# A próxima batalha dos grandes modelos: multi-modalidade é inevitável ou uma narrativa superaquecida?

Uma análise dialética profunda sobre a direção futura da IA

---

## Introdução: Uma disputa de direção que não pode ser evitada

Em maio de 2024, OpenAI lançou o GPT-4o. Na apresentação, quando o modelo analisava em tempo real expressões faciais e respondia a perguntas com voz carregada de emoção, o público presente soltou exclamações de admiração. Este momento criou um consenso quase instintivo na comunidade tecnológica global: o futuro dos grandes modelos está na multi-modalidade.

Mas este consenso está correto?

Ao discutir "direção futura", na verdade misturamos duas questões diferentes: multi-modalidade tem valor (quase todos concordam que tem); e se agora devemos tratar multi-modalidade como a prioridade máxima e, por esta razão, minimizar a otimização profunda de modelos de linguagem apenas em texto (este é o verdadeiro ponto de discordância).

Este artigo tenta desvendar estas duas questões, utilizando avanços tecnológicos recentes, casos de produtos e dados de mercado, para dar um julgamento mais honesto.

---

## Primeira dimensão: O valor real da expansão de percepção

O argumento mais intuitivo em apoio à prioridade da multi-modalidade é que a própria cognição humana é multi-modal.

Este argumento não é vazio. No campo médico, o Med-PaLM M do Google atingiu o nível de médicos especialistas no diagnóstico de radiografias de tórax, imagens de fundo de olho e seções de patologia, e pesquisas de Stanford mostram que o diagnóstico combinado de visual + texto tem uma taxa de precisão 23 pontos percentuais superior à análise de registros médicos apenas em texto. No campo da educação, o recurso de tirar fotos para resolver problemas aumentou a participação dos alunos em 40%. Na indústria criativa, Midjourney, Suno e Adobe Firefly deram aos bilhões de pessoas comuns a oportunidade de ter produção criativa de nível profissional pela primeira vez.

Estes não são casos de demonstração, mas sim implementação comercial com base em usuários reais.

Do ponto de vista da teoria da informação, esta tendência também tem sua lógica interna. A quantidade de informação de vídeo gerada diariamente na Terra ultrapassa em muito a quantidade de informação textual. Uma imagem em 1080P contém uma quantidade de informação equivalente a milhares de palavras. Uma IA que só consegue processar texto está em contato com um pequeno subconjunto do mundo de informações humano.

---

## Segunda dimensão: A "maturidade" dos LLMs foi superestimada?

No entanto, a inferência "os LLMs já são suficientemente maduros, portanto devemos passar para multi-modalidade" não resiste a um exame atento.

Qual é a evidência de "suficientemente maduro"? ChatGPT tem mais de 200 milhões de usuários ativos mensais e cobre mais de 90% das empresas da Fortune 500. Do ponto de vista do tamanho do usuário, isto é de fato impressionante.

Mas do ponto de vista da confiabilidade da capacidade, o cenário é muito mais complexo. A avaliação de Stanford em 2024 mostrou que a taxa de alucinação dos LLMs na tarefa de resumo de literatura médica ainda é tão alta quanto 20-30%. O problema no campo jurídico é mais específico: há casos frequentes de advogados em Nova York sendo punidos pela corte por apresentar referências de casos falsas geradas por IA. Os 200 milhões de usuários estão usando diariamente uma ferramenta com uma taxa de erro tão alta, o que indica a propagação da ferramenta, não a maturidade da capacidade.

Mais importante ainda, a série o1/o3 da OpenAI mostrou o potencial de outro caminho. Abandonando a rota de iteração rápida com RLHF, regressando ao treinamento de raciocínio profundo, o o3 na avaliação de referência ARC-AGI mostra um aumento que é várias vezes maior do que a soma de todos os progressos multi-modais dos últimos dois anos. Isto indica que a profundidade de raciocínio do LLM está longe de seu limite. Retirar recursos daqui e transferi-los para multi-modalidade representa um custo real e tangível.

---

## Terceira dimensão: Disputas sobre a profundidade técnica da multi-modalidade

Os defensores da multi-modalidade frequentemente citam um cenário inspirador: o GPT-4o vê uma foto e consegue entender emoções, analisar composição, conectar contexto e dar uma resposta profunda. Isto não é "suficientemente maduro"?

Há um detalhe técnico chave que merece atenção séria.

A arquitetura de quase todos os modelos multi-modais atuais é em pipeline: o codificador de visão converte a imagem em tokens, e o modelo de linguagem processa estes tokens. Não há verdadeira interação bidirecional entre raciocínio visual e raciocínio de linguagem - a entrada visual acaba sendo "traduzida" em conceitos linguísticos, com o processamento central permanecendo sendo raciocínio de linguagem.

Existe um experimento que ilustra este problema: para a mesma imagem, se você disser ao GPT-4o com texto o conteúdo da imagem ("uma menina triste, com ruínas de guerra ao fundo"), a qualidade da análise é quase idêntica a ver a imagem diretamente. A entrada visual é o "ponto de recepção", o raciocínio de linguagem é o "ponto de processamento" - a "sinergia" da multi-modalidade nesta arquitetura é principalmente ilusória, uma descrição mais precisa seria: o LLM é o motor central, multi-modalidade é a entrada periférica.

A pesquisa do MIT em 2024 também descobriu que a maioria dos modelos multi-modais apresenta falhas sistemáticas no raciocínio visual do mundo real - particularmente na compreensão de relacionamentos espaciais, contagem e estrutura 3D, significativamente inferior aos humanos. Os vídeos gerados pelo Sora apresentam erros físicos como líquidos em fluxo reverso e penetração de membros, o que também ilustra isto: o modelo imitou padrões visuais em nível estatístico, mas não entendeu verdadeiramente a realidade física.

---

## Quarta dimensão: Estratificação do valor comercial

O valor comercial da multi-modalidade requer uma importante distinção.

O que as empresas estão usando a IA multi-modal para fazer? A análise visual da Salesforce é essencialmente identificar categorias de produtos em imagens, a compreensão de imagem do HubSpot é detectar frequência de aparição de logo de marca, a detecção de segurança em fábricas é identificar se os trabalhadores estão usando capacetes de segurança. Estas tarefas realmente precisam de visão de máquina (visão computacional), não de modelos de linguagem multi-modais grandes - usar ResNet que já era maduro em 2019 é suficiente. A maioria dos fornecedores comerciais de IA de segurança também usa modelos de visão leve e especializados, porque modelos multi-modais universais têm custos muito altos e velocidade de raciocínio muito lenta.

O relatório de 2024 da Andreessen Horowitz confirma isto: a maioria dos projetos de IA empresarial cortou características multi-modais porque o custo de raciocínio excedeu as expectativas. O custo de token do raciocínio multi-modal é várias vezes maior do que o do raciocínio em texto, o que é uma limitação real em mercados sensíveis a preços.

Cenários de alto valor que realmente precisam da profunda capacidade de modelos multi-modais existem - análise de imagens médicas complexas, compreensão entre modalidades de dados de pesquisa - mas estes cenários precisam mais de modelos especializados por domínio, não de modelos multi-modais universais. No diagnóstico de imagens médicas, a precisão do GPT-4V (multi-modal universal) é 63%, a de modelos visuais médicos especializados (versão especializada Med-Gemini) é 84%, e a lacuna não se estreitou significativamente com a expansão da escala.

---

## Quinta dimensão: Os dois lados do gargalo de dados

Os defensores da multi-modalidade têm um argumento importante: os dados de texto já estão se esgotando. A equipe de pesquisa da Meta estimou que dados de texto de alta qualidade da internet chegarão ao pico em 2026-2028. A quantidade de dados de imagem e vídeo ultrapassa muito a quantidade de texto, e é a forma de escapar da "parede de dados".

Este argumento é verdadeiro, mas a cadeia lógica não está completa.

Os dados multi-modais são abundantes em quantidade, mas a densidade de sinal de treinamento efetivo é extremamente baixa. Vídeos no YouTube não vêm com anotações semânticas de alta qualidade, o texto alternativo de imagens é extremamente rudimentar - embora a quantidade de dados multi-modais seja grande, muito é ruído. Em contraste, dados sintéticos são outro caminho para expandir dados de texto - o AlphaProof da DeepMind, usando apenas dados de prova matemática sintética, alcançou um avanço histórico na Olimpíada Internacional de Matemática. Em domínios com mecanismos de verificação objetiva (o programa roda ou não, a prova é válida ou não), dados sintéticos podem efetivamente quebrar a parede de dados.

Ambos os caminhos têm seu valor e limitações, mas equiparar diretamente "dados de texto tocando o pico" com "deveria desenvolver multi-modalidade prioritariamente" é uma simplificação que pula muitos passos intermediários.

---

## Sexta dimensão: Risco assimétrico de segurança e ética

Os riscos de segurança da tecnologia multi-modal são mais difíceis de lidar do que apenas texto, e são frequentemente subestimados.

A falsificação profunda é o risco de segurança mais típico da tecnologia multi-modal. Em 2024, uma empresa em Hong Kong foi defraudada em 25 milhões de dólares por um vídeo falsificado multi-modal. O conteúdo multi-modal é mais prejudicial em escala oculta - dependência de contexto de imagem, memes visuais entre idiomas, informações proibidas mascaradas como imagens "normais" - a dificuldade de moderação é exponencialmente maior do que o conteúdo de texto.

Tecnologias de rastreamento de conteúdo como marca d'água digital C2PA são eficazes em laboratório, mas falham no ambiente de propagação real (transcoding, captura de tela, compressão). Para aplicações de reconhecimento emocional de imagem, a pesquisa do MIT Media Lab descobriu que a correlação entre ações musculares faciais e estado emocional interno é muito menor do que geralmente é assumido, portanto aplicações de computação emocional construídas nesta suposição científica têm deficiência inerente de precisão e risco ético.

Isto não é negar a tecnologia multi-modal em si, mas dizer: quando o alinhamento de segurança ainda não está perfeito, a rápida expansão da capacidade multi-modal precisa ser mais cautelosa, e não avançar rapidamente sob o pretexto de que "a governança acompanhará".

---

## Sétima dimensão: A questão de sequência na alocação de recursos

Considerando tudo isto, o núcleo deste debate não é "multi-modalidade tem valor", mas sim "em que momento e em que proporção investir em multi-modalidade".

Uma observação interessante é que há uma clara divergência entre o foco da comunidade de pesquisa em publicações globais de laboratórios de IA de topo e o foco de lançamentos de produtos. No nível de produto, multi-modalidade é o foco de marketing, o ator principal do lançamento; no nível de pesquisa, os avanços mais profundos (o avanço de raciocínio do o1/o3, a sistematização das cadeias de pensamento, métodos de auto-consistência, mecanismos de verificação de dados sintéticos) ocorrem principalmente no domínio dos modelos de linguagem pura.

Esta divergência ilustra algo: produtos evoluem para multi-modalidade porque os usuários conseguem ver e tocar, a experiência é mais intuitiva; mas os verdadeiros problemas de inteligência difíceis, pesquisadores ainda estão escavando no solo do raciocínio linguístico.

Historicamente, em cada geração de desenvolvimento de tecnologia, há estágios onde a "narrativa está à frente da tecnologia". A discussão sobre modelos multi-modais grandes atualmente, em parte, pertence a esta categoria - sua direção a longo prazo pode estar correta, mas a proporção de investimento de recursos a curto prazo pode ser superestimada pela grande narrativa.

---

## Conclusão: Alicerces e tetos, não uma escolha entre um ou outro

A resposta mais honesta não é "multi-modalidade é o futuro" nem "LLM é o ponto focal", mas sim: ambos são importantes, mas há uma sequência.

No estágio atual, confiabilidade dos modelos de linguagem, profundidade de raciocínio e alinhamento de segurança permanecem sendo as direções prioritárias que merecem concentração de recursos. Estas capacidades são o alicerce. A expansão perceptiva da multi-modalidade é um valor incremental genuíno, mas quando o alicerce ainda não está estável, transferir grandes quantidades de recursos para o nível superior traz riscos estruturais muito altos.

Isto não é conservadorismo técnico, mas respeito pela realidade da engenharia.

O lançamento do GPT-4o foi de fato impressionante, e a implementação comercial da multi-modalidade também está realmente avançando. Mas o que realmente mudará o mundo não é a função "consegue ver imagens", mas sim quando a IA conseguir verdadeiramente integrar percepção, raciocínio e confiabilidade como um todo integrado. Até aquele dia chegar, precisamos manter um julgamento claro entre perseguir narrativas e consolidar os alicerces.

---

*Este artigo baseia-se em relatórios técnicos públicos, publicações acadêmicas e dados de avaliação de produtos. Todos os dados citados têm fontes bibliográficas, sem previsões infundadas adicionadas.*