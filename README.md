# UVVine · Clube de Vinhos da UVV

Projeto Integrador de Ciência de Dados (UVV, 2026/2), em duas partes:

- **Parte 1 (Módulo 1):** estatística, com amostragem, testes de hipóteses e estatística descritiva.
- **Parte 2 (Módulo 2):** aprendizado de máquina, com regressão, clusterização e classificação.

## Dados
Base `table42.csv`, com 1.120.000 notas fiscais e 23 colunas, fornecida pelo professor da disciplina. O arquivo não está neste repositório por causa do tamanho (cerca de 380 MB). Para rodar os notebooks, faça o upload dele na pasta `/content` do Colab.

Na preparação, removi 72.477 notas com medidas de vinho negativas, e a base limpa ficou com 1.047.523 notas.

## Parte 1 · Tamanho ideal da amostra

**Pergunta:** qual é o tamanho ideal da amostra para analisar o gasto dos clientes, numa população infinita e estratificada por tipo de conta (ESSENTIAL, VIP e PRIME)?

**Resposta: 141.900 notas fiscais.** Com esse tamanho, o gasto médio é estimado com margem de erro de cerca de ±0,5% a ±0,6% da média, com 95% de confiança, em todos os tipos de conta.

**O que foi feito:**
- **A1 · Estratificação amostral:**
  - estabilização marginal do erro padrão (4 grupos) e amostra estratificada ótima de Neyman;
  - bootstrap, análise de outliers e testes de hipóteses de normalidade, independência, mesma distribuição e médias.
- **A2 · Estatística descritiva:** variáveis quantitativas e qualitativas por tipo de conta.
- **A3 · Pesquisa de satisfação:** escala de 5 pontos, em % geral e por sexo, com bootstrap.

**Principais resultados:**
- O cliente PRIME gasta 5,2 vezes mais que o ESSENTIAL. Ele representa 17% das notas e cerca de 44% do faturamento da amostra.
- A renda é a variável que mais acompanha o gasto (correlação de Spearman de 0,74). Região, sexo, estado civil e dependentes não diferenciam os tipos de conta.
- 80,2% dos clientes estão satisfeitos e só 4,8% insatisfeitos, sem diferença entre homens e mulheres. Mas apenas 3% estão muito satisfeitos.

## Parte 2 · Aprendizado de máquina

**Conjuntos:** train, validation e test, cada um com o tamanho ideal da Parte 1 (141.900 notas), disjuntos e sorteados da base limpa com semente fixa. As 621.823 notas restantes formam a população, usada como teste extra. O test ficou guardado até a avaliação final de cada modelo.

| Pergunta | Modelo escolhido | Score no test | Score na população |
|---|---|---|---|
| Quanto o cliente gasta? (regressão) | Linear Regression | R² = 0,7341 | R² = 0,7368 |
| Que grupos de clientes existem? (clusterização) | K-Means, 3 clusters, só a renda | silhueta = 0,872 | silhueta = 0,868 |
| Que tipo de conta o cliente deve ter? (classificação) | AdaBoost, entre 10 classificadores | acurácia = 92,62% | acurácia = 92,63% |

Cada modelo foi avaliado com validação cruzada (10 folds), intervalos de confiança por bootstrap (9.999 reamostras) e 200 amostras aleatórias da população.

**Principais resultados:**
- **A renda explica tudo.** Os três modelos chegaram à mesma conclusão por caminhos independentes:
  - na regressão, cada R\$ 1.000 a mais de renda soma R\$ 109,45 ao gasto por nota;
  - a clusterização reencontrou os três tipos de conta usando só a renda (92,6% de concordância);
  - no classificador, a renda responde por 86% da importância.
  
  Região, sexo, estado civil, dependentes, opinião e as características do vinho não explicam nem o gasto nem o tipo de conta.
- **Os dois limites vêm da base, e não dos modelos:**
  - o gasto é uma fração da renda sorteada entre 4% e 18%, o que limita o R² a cerca de 0,74;
  - cerca de 7,4% das notas são de clientes com renda incompatível com o tipo de conta, o que limita a acurácia a cerca de 92,6%.
- **O PRIME gasta mais porque ganha mais.** Os três tipos de conta gastam a mesma fatia da renda (cerca de 11%) por compra. Clientes no tipo de conta "errado" gastam conforme a renda, e isso abre espaço para ofertas de upgrade e para uma revisão do enquadramento.

## Arquivos
- `Projeto_Integrador_WORKFLOW_PARTE_1.ipynb` e `.pdf`: Parte 1, com o relatório final.
- `Projeto_Integrador_WORKFLOW_PARTE_2.ipynb` e `.pdf`: Parte 2, com os relatórios parciais dos três modelos e o relatório final.

## Links
- Parte 1 no Colab: [abrir](https://colab.research.google.com/github/LuckCsta/ProjetoIntegrador/blob/main/Projeto_Integrador_WORKFLOW_PARTE_1.ipynb)
- Parte 2 no Colab: [abrir](https://colab.research.google.com/github/LuckCsta/ProjetoIntegrador/blob/main/WORKFLOW_PARTE_2.ipynb#scrollTo=x4Zk9rhe1bET)

## Tecnologias
Python, pandas, NumPy, SciPy, statsmodels, scikit-learn, Matplotlib, seaborn e Google Colab.

## Autor
Lucas da Silva Ferreira Costa
