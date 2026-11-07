# UVVine · Clube de Vinhos da UVV

Projeto Integrador de Ciência de Dados (UVV, 2026/2), Módulo 1: Workflow Parte 1.

## Pergunta de negócio
**Qual é o tamanho ideal da amostra** para analisar o gasto dos clientes da UVVine, numa população infinita e estratificada por tipo de conta (ESSENTIAL, VIP e PRIME)?

**Resposta: 141.900 notas fiscais.** Com esse tamanho, o gasto médio é estimado com margem de erro de cerca de ±0,5% a ±0,6% da média, com 95% de confiança, em todos os tipos de conta.

## Dados
Base `table42.csv`, com 1.120.000 notas fiscais e 23 colunas, fornecida pelo professor da disciplina. O arquivo não está neste repositório por causa do tamanho (cerca de 380 MB). Para rodar o notebook, faça o upload dele na pasta `/content` do Colab.

## O que foi feito
- **Preparação dos dados:** remoção de 72.477 notas com medidas de vinho negativas e correção da escala de opinião.
- **A1 · Estratificação amostral:**
  - estabilização marginal do erro padrão (4 grupos) e amostra estratificada ótima de Neyman;
  - bootstrap, análise de outliers e testes de hipóteses de normalidade, independência, mesma distribuição e médias.
- **A2 · Estatística descritiva:** variáveis quantitativas e qualitativas por tipo de conta.
- **A3 · Pesquisa de satisfação:** escala de 5 pontos, em % geral e por sexo, com bootstrap.

## Principais resultados
- O cliente PRIME gasta 5,2 vezes mais que o ESSENTIAL. Ele representa 17% das notas e cerca de 44% do faturamento da amostra.
- A renda é a variável que mais acompanha o gasto (correlação de Spearman de 0,74). Região, sexo, estado civil e dependentes não diferenciam os tipos de conta.
- 80,2% dos clientes estão satisfeitos e só 4,8% insatisfeitos, sem diferença entre homens e mulheres. Mas apenas 3% estão muito satisfeitos.

## Arquivos
- `WORKFLOW_PARTE_1_LucasCosta.ipynb`: notebook completo.
- `WORKFLOW_PARTE_1_LucasCosta.pdf`: versão em PDF, com o relatório final.

## Links
- Notebook no Colab: COLE AQUI O LINK
- Vídeo no YouTube: COLE AQUI QUANDO PUBLICAR

## Tecnologias
Python, pandas, NumPy, SciPy, statsmodels, Matplotlib, seaborn e Google Colab.

## Autor
Lucas da Silva Ferreira Costa
