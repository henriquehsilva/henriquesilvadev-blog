---
title: "Challenge 2: Titanic - Machine Learning from Disaster"
description: "As necessidades do negócio para o projeto Titanic - Machine Learning from Disaster envolvem a criação de um modelo preditivo capaz de determinar a probabilidade de sobrevivência dos passageiros do Titanic com base em uma variedade de características. Essa previsão é vital para compreender melhor os fatores que influenciaram as chances de sobrevivência dos passageiros e, consequentemente, auxiliar na formulação de políticas de segurança marítima mais eficazes."
pubDate: "Mar 16 2024"
badge: "#I2A2"
tags: ["I2A2", "CHALLENGE-2", "TITANIC"]
slug: "challenge-2-titanic"
heroImage: "/titanic.jpeg"
---

<h3>CRISP-DM</h3>

<p style="text-align: justify">
    A metodologia Cross-Industry Standard Process for Data Mining (CRISP-DM) consiste em 6 fases, incluindo compreensão do negócio, preparação de dados e análise exploratória de dados (EDA), modelagem, avaliação, implantação, bem como manutenção e monitoramento. Para este estudo de caso, será utilizado o desafio <a href="https://www.kaggle.com/competitions/titanic" target="_blank">Titanic - Machine Learning from Disaster</a> do Kaggle.
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

data_path = "/Users/henriquesilvadev/Projects/I2A2-Training/Challenge 2/data"

df = pd.read_csv(f"{data_path}/train.csv")
```
<p style="text-align: justify">
    Usando Dataframe.info(), sabemos que o conjunto de dados é composto por 12 colunas e 891 linhas. 5 colunas de dados estão na forma de números inteiros, 2 colunas de dados estão na forma de números de ponto flutuante, enquanto o restante está na forma de string. Também podemos concluir que há valores ausentes em 3 colunas [Age, Cabin, Embarked] dos dados.
</p>

```python

df.info()

```

[!['Dataframe.info()'](https://henriquesilva.dev/df_info.png "Dataframe.info()")]