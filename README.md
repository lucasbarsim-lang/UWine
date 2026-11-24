# Projeto UWine - TCC

Este repositório reúne as partes do Trabalho de Conclusão de Curso (TCC) em Ciência de Dados, utilizando o caso fictício da UWine, o clube de vinhos da UVV, para aplicar estatística, análise de dados e machine learning em Python.

## 🔗 Objetivo do trabalho

O projeto está organizado para abranger:

- **Parte 1:** definição e validação do tamanho amostral, estratificação da população, testes de hipóteses e bootstrap.
- **Parte 2:** construção e avaliação de modelos de machine learning sobre uma amostra estratificada de 50.300 notas fiscais, com três atividades: **regressão** (prever o valor da nota), **clusterização** (descobrir grupos de clientes) e **classificação** (identificar o tipo de conta).

## 🔗 Estrutura do repositório

| Arquivo | Conteúdo |
|---|---|
| `Lucas_Barbosa_WORKFLOW_PARTE_1 (2).ipynb` | Parte 01 do projeto |
| `Lucas_Barbosa_WORKFLOW_PARTE_2.ipynb` | Parte 02 do projeto |

## 🔗 Parte 2: como o trabalho foi feito

**Base de dados.** Tabela de notas fiscais simulada do clube, com 1.120.000 registros e 23 colunas (perfil do cliente, tipo de conta, características dos vinhos e valor total da nota), em Python no Google Colab.

**Amostra.** Amostra estratificada por tipo de conta (ESSENTIAL, VIP e PRIME) com alocação de Neyman, totalizando **50.300 notas**: 20.073 ESSENTIAL, 11.327 VIP e 18.900 PRIME. A amostra foi dividida em **70% treino** (35.210), **15% validação** (7.545) e **15% teste** (7.545), de forma estratificada.

**Preparação dos dados.** Normalização (z-score), mapeamento das variáveis categóricas e discretização da opinião do cliente em nota de satisfação de 1 a 5, com todos os parâmetros definidos apenas no treino, para evitar vazamento de dados.

**Avaliação.** Cada modelo foi escolhido na validação, medido no teste e verificado em uma amostra aleatória de 50.300 notas da base completa, que mantém as proporções reais dos tipos de conta. Também foram usados validação cruzada e bootstrap para os intervalos de confiança.

## 🔗 Parte 2: principais resultados

| Atividade | Modelo final | Resultado no teste | Resultado na base real |
|---|---|---|---|
| A1: Regressão (valor da nota) | Lasso (modelo linear) | R² de 71,0% | R² de 74,1%, erro típico (RMSE) de 417 reais |
| A2: Clusterização | K-Means com 4 grupos | Silhueta de 0,305 | Silhueta de 0,325 |
| A3: Classificação (tipo de conta) | AdaBoost | Acurácia de 94,6% | Acurácia de 93,9% |

**O que os resultados mostram:**

- **Regressão:** a renda é o principal fator do valor da nota, e o erro cresce com o valor da compra (o modelo explica bem o perfil ESSENTIAL e pouco os perfis VIP e PRIME).
- **Clusterização:** o modelo separa os clientes PRIME dos demais, sem saber o tipo de conta. Cerca de 15% da base forma um segmento PRIME bem definido.
- **Classificação:** o tipo de conta é identificado com cerca de 94% de acerto, e o erro mais comum é confundir clientes VIP com PRIME.
- **Composição da amostra:** a amostra de Neyman tem mais clientes PRIME (38%) do que a base real (16%). As diferenças entre teste e base real vêm dessa mistura e foram confirmadas por reponderação.

## 🔗 Tecnologias

Python, Google Colab, pandas, NumPy, scikit-learn, SciPy, Matplotlib e Seaborn.

## 🔗 Vídeo do trabalho

- Parte 1 - https://youtu.be/15R0M3n8MPs?feature=shared
- Parte 2 - *(adicionar o link)*

## 🔗 Autor

Lucas Barbosa Simão
