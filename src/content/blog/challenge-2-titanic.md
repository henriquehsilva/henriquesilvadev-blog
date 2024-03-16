---
title: "Challenge 2: Titanic - Machine Learning from Disaster"
description: "As necessidades do negócio para o projeto Titanic - Machine Learning from Disaster envolvem a criação de um modelo preditivo capaz de determinar a probabilidade de sobrevivência dos passageiros do Titanic com base em uma variedade de características. Essa previsão é vital para compreender melhor os fatores que influenciaram as chances de sobrevivência dos passageiros e, consequentemente, auxiliar na formulação de políticas de segurança marítima mais eficazes."
pubDate: "Mar 16 2024"
badge: "#I2A2"
tags: ["I2A2", "CHALLENGE-2", "TITANIC"]
slug: "challenge-2-titanic"
heroImage: "/titanic_4-61.jpg"
---

<h3>CRISP-DM</h3>

<p style="text-align: justify">
    A metodologia Cross-Industry Standard Process for Data Mining (CRISP-DM) consiste em 6 fases, incluindo compreensão do negócio, preparação de dados e análise exploratória de dados (EDA), modelagem, avaliação, implantação, bem como manutenção e monitoramento. Para este estudo de caso, será utilizado o desafio <a href="https://www.kaggle.com/competitions/titanic" target="_blank">Titanic - Machine Learning from Disaster</a> do Kaggle.
</p>

<h3>Objetivos do Trabalho</h3>

- Coletar e limpar os dados do conjunto de dados do Titanic.
- Explorar e analisar os dados para entender as tendências e padrões.
- Desenvolver e treinar um modelo de machine learning que possa prever a sobrevivência dos passageiros com base em atributos como idade, sexo, classe socioeconômica, etc.
- Avaliar o desempenho do modelo e refiná-lo conforme necessário para alcançar uma precisão satisfatória.
- Fornecer insights acionáveis para melhorar as políticas de segurança em futuras viagens marítimas.

<h3>Critérios de Aceite</h3>

Os critérios de aceite para o projeto Titanic - Machine Learning from Disaster são:

- O modelo deve ser capaz de prever com precisão a sobrevivência dos passageiros com uma taxa de acerto superior a X%.
- A análise exploratória de dados deve fornecer insights significativos sobre os fatores que influenciaram a sobrevivência dos passageiros.
- O código deve ser bem documentado, modular e replicável.
- O relatório final deve resumir claramente os resultados obtidos, incluindo as limitações do modelo e possíveis melhorias futuras.

<p style="text-align: justify">
    Ao seguir a metodologia CRISP-DM (Cross-Industry Standard Process for Data Mining), podemos abordar sistematicamente esses requisitos para garantir o sucesso do projeto Titanic - Machine Learning from Disaster e fornecer resultados valiosos para a melhoria da segurança marítima.
</p>

<h3>Fase 1: Entendimento do Negócio</h3>

<p style="text-align: justify">
    As necessidades do negócio para o projeto Titanic - Machine Learning from Disaster envolvem a criação de um modelo preditivo capaz de determinar a probabilidade de sobrevivência dos passageiros do Titanic com base em uma variedade de características. Essa previsão é vital para compreender melhor os fatores que influenciaram as chances de sobrevivência dos passageiros e, consequentemente, auxiliar na formulação de políticas de segurança marítima mais eficazes.
</p>

<h3>Fase 2: Preparação de Dados/Análise Exploratória de Dados (EDA)</h3>

<p style="text-align: justify">
    Baixar o conjunto de dados de <a href="https://www.kaggle.com/competitions/titanic/data" target="_blank">Titanic - Machine Learning from Disaster Data</a> e salvar em local. Abrir o Jupyter Notebook e importar as bibliotecas necessárias. Para carregar o conjunto de dados.
</p>

``` python
import numpy as np # linear algebra
import pandas as pd # data processing
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns

# Input files
file_train='./data/train.csv'
file_test='./data/test.csv'

seed = 69
np.random.seed(seed)

train_df = pd.read_csv(file_train,index_col='PassengerId')
test_df = pd.read_csv(file_test,index_col='PassengerId')
```

```python
train_df.columns.values
```
!['Show columns'](https://henriquesilva.dev/show_columns.png "Show columns")

```python
train_df.shape
```
!['Show shape'](https://henriquesilva.dev/shape_titanic.png "Show shape")

<p style="text-align: justify">
    Usando Dataframe.info(), sabemos que o conjunto de dados é composto por 12 colunas e 891 linhas. 5 colunas de dados estão na forma de números inteiros, 2 colunas de dados estão na forma de números de ponto flutuante, enquanto o restante está na forma de string. Também podemos concluir que há valores ausentes em 3 colunas [Age, Cabin, Embarked] dos dados.
</p>

```python
train_df.info()
```

!['Dataframe.info()'](https://henriquesilva.dev/df_info.png "Dataframe.info()")


<p style="text-align: justify">
    Para obter uma compreensão básica dos dados, podeamos usar função DataFrame.describe(). Por padrão, esta função retorna estatísticas descritivas para as variáveis numéricas. No entanto, podemos descobrir as informações dos objetos incluindo include=’object’ como parâmetro.
</p>

```python
train_df.describe()
```

!['Dataframe.describe()'](https://henriquesilva.dev/df_describe.png "Dataframe.describe()")

```python
train_df.isnull().sum()
````

!['Dataframe.isnull().sum()'](https://henriquesilva.dev/isnull.png "Dataframe.isnull().sum()")