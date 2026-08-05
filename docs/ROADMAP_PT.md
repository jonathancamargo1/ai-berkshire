# Roteiro do ai-berkshire

## P0: Curto prazo (1-2 meses)

### Integração de fontes de dados do mercado A-Share
- Integrar fontes de dados gratuitas como akshare e East Money
- Cobertura de dados financeiros, cotações e lista de negociações do mercado A-Share
- Skills existentes não precisam de modificação, apenas expansão na camada de dados

## P1: Médio prazo (3-6 meses)

### Saída de relatórios em HTML
- Adicionar formato HTML de relatórios além do Markdown
- Suporte a modo escuro, barra de navegação e visualização de gráficos
- Melhorar a transmissibilidade e experiência de leitura dos relatórios

### Múltiplos modos de profundidade
- `lite`: Avaliação rápida em 5 minutos, fornecendo intervalo de avaliação e conclusões principais
- `standard`: Modo padrão atual, pesquisa multi-agente completa
- `deep`: Adicionar mais validação cruzada e análise histórica comparativa, profundidade de nível institucional

### Comparação horizontal de múltiplas ações
- Suporte a comparação horizontal de 2-4 ações na mesma dimensão
- Benchmarking de avaliação de empresas do mesmo setor
- Saída de matriz de comparação e recomendação de seleção

## P2: Longo prazo (6+ meses)

### Cobertura de testes
- Adicionar testes unitários para ferramentas principais (financial_rigor.py, etc.)
- Adicionar testes de regressão para saída de Skills
- Garantir que iterações não quebrem funcionalidades existentes

### Análise de nível de portfólio
- Avaliação da saúde da carteira de investimentos
- Análise de concentração de indústria/região geográfica
- Detecção de risco de correlação