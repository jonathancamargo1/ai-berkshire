# AI Berkshire — Arquivo de Memória AI

> Este arquivo registra o conhecimento do projeto, preferências do usuário e histórico de decisões acumulados através da colaboração do Claude com o usuário para referência em conversas subsequentes.

## Perfil do Usuário

- Estilo de investimento: Investimento em valor, posições concentradas com grandes alocações, focado em internet, consumo e IA na China
- Preferência de pesquisa: Direto e incisivo, sem rodeios, conclusões claras sem tentar agradar ambos os lados, dados devem ser precisos
- Casos de uso: Assistência em decisões de investimento pessoal, além de promoção do projeto como produto de código aberto

## Histórico de Evolução do Projeto

### 7-9 de abril de 2026 (Primeira rodada de pesquisa + refinamento de estrutura)

**Pesquisas concluídas:**
1. `/investment-team Pinduoduo` — Primeira pesquisa completa com 4 Agents em paralelo, classificação 3,4/5
2. `/investment-checklist` 7 empresas — Moutai, Tencent, NVIDIA, Meituan, Pinduoduo, Pop Mart, Kuaishou
3. Rastreamento de posições dos grandes mestres — Últimas 13F de Buffett/Li Lu/Duan Yongping + análise de preço de custo PDD
4. Reavaliação profunda de 5 empresas como Meituan (desafiada pelo usuário na avaliação inicial)

**Correções resultantes de feedback do usuário:**
- Meituan de ❌ para ✅ aprovado condicionalmente — usuário apontou: esperar recuperação de lucros é tarde demais, 200 bilhões impenetráveis = verdadeiro fosso
- NVIDIA de ❓ para ✅ aprovado condicionalmente — Capex de IA ainda acelerador, Paradoxo de Jevons
- Kuaishou de ❓ para ✅ aprovado condicionalmente — IA Keling subestimada, Sora já descontinuado

**Lições-chave:**
- Não aplicar checklist mecanicamente, ter julgamento independente
- "Esperar recuperação de lucros para comprar" é falácia lógica — preço de ação reflete antecipadamente
- Concorrentes gastaram mais dinheiro mas não tiveram ganho = melhor evidência do fosso

## Propostas de Valor Principal do Projeto

1. **Forçar conclusões sem rodeios** — Aprovado/Não aprovado/Cinzento, com faixa de preço específica
2. **Confrontação de perspectivas dos quatro mestres** — Não é divisão de trabalho, mas desafio mútuo
3. **Mecanismo anti-viés estruturado** — Suficiência A/B/C, reversão de Munger, contrária ao consenso
4. **Precisão de dados financeiros** — Cálculo Decimal preciso, cálculo manual de valor de mercado
5. **Processo de pesquisa reproduzível** — Mesma entrada → saída estruturalmente consistente
6. **Profundidade paralela de múltiplos Agents** — 4 Agents cada um pesquisa + análise independente
7. **Validação de trading real** — Lucro cumulativo de 1,46 milhão em 2 anos

## Preferências do Usuário e Hábitos de Trabalho

- **Idioma do relatório**: Chinês
- **Push para GitHub**: Após conclusão da pesquisa, geralmente solicitado e perguntado proativamente
- **Operações Git**: Há frequentemente novos commits remotos, deve fazer `git pull --rebase` antes de fazer push
- **Atitude em relação a erros**: Apontar diretamente, sem necessidade de ser delicado
- **Profundidade de pesquisa**: Prefira gastar tempo fazendo direito em vez de rápido e superficial