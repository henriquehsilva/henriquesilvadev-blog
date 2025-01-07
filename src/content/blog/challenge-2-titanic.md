---
title: "Dia #1: Aprendendo a Correr"
description: ""
pubDate: "Jan 07 2025"
badge: "#instrucional"
tags: ["TREINO DE CORRIDA", "TREINO DE FORÇA", "SONO", "DIETA"]
slug: "dia-1-aprendendo-a-correr"
heroImage: "/aprendendo-a-correr.jpg"
---

<h3>06h - Iniciando o Dia</h3>

<p style="text-align: justify">
    Acordei hoje as 06h após uma boa noite de sono.
</p>

!['Registro SONO 070125'](https://henriquesilva.dev/registro-sono-070125.png")

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
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns

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


```python
train_df.head()
````

!['train_df.head()'](https://henriquesilva.dev/head_titanic.png "train_df.head()")

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

```python
def prepare_data(df):
    # Remove colunas não relevantes
    df.drop(['Name', 'Ticket', 'Cabin'], axis = 'columns', inplace = True)

    # Binarizar sexo
    df['Sex'] = df['Sex'].map({'female': 1, 'male': 0}).astype(int)

    # Preencha os dados faltantes: media de [Fare] e [Embarked] com valor mais frequente
    df[['Fare']] = df[['Fare']].fillna(value=df[['Fare']].mean())
    df[['Embarked']] = df[['Embarked']].fillna(value=df['Embarked'].value_counts().idxmax())

    # Converter [Embarked] para "one-hot"
    enbarked_one_hot = pd.get_dummies(df['Embarked'], prefix='Embarked', dtype=int)
    df.drop('Embarked', axis= 'columns', inplace = True)
    df = df.join(enbarked_one_hot)

    # Define index ao [PasseId]
    df.rename_axis(None, axis = 'rows', inplace = True)
    df.rename_axis('PasserId', axis = 'columns', inplace = True)

    return df
````

```python
train_df = prepare_data(train_df)
```

!['Prepare data'](https://henriquesilva.dev/prep_data_titanic.png "Prepare data")

<p style="text-align: justify">
<b>Imputação com base em outras variáveis:</b> agrupando os dados por sexo e classe socioeconômica em seguida, calcula a mediana da idade em cada grupo para preencher os valores faltantes.
</p>

```python
def filter_ages_to_sex_and_pclass(sex_id, pclass_id, df):
    df = df[df['Sex'].isin([sex_id])]
    df = df[df['Pclass'].isin([pclass_id])]
    df.loc[:, 'Age'] = round(df['Age'].fillna(value=df['Age'].median()))

    return df
```

```python
df1 = filter_ages_to_sex_and_pclass(1, 1, train_df)
df2 = filter_ages_to_sex_and_pclass(1, 2, train_df)
df3 = filter_ages_to_sex_and_pclass(1, 3, train_df)
df4 = filter_ages_to_sex_and_pclass(0, 1, train_df)
df5 = filter_ages_to_sex_and_pclass(0, 2, train_df)
df6 = filter_ages_to_sex_and_pclass(0, 3, train_df)
```

```python
frames = [df1, df2, df3, df4, df5, df6]
train_df = pd.concat(frames).sort_index()

train_df.info()
```

!['Imputação com base em outras variáveis'](https://henriquesilva.dev/info_total.png "Imputação com base em outras variáveis")

<h3>Scatterplot Matrix</h3>

```python
sns.set_theme(style = "ticks")
sns.pairplot(train_df, hue = "Survived")
```
!['Scatterplot Matrix'](https://henriquesilva.dev/scatterplot_m_titanic.png "Scatterplot Matrix")

<p style="text-align: justify">
<b>Obs.:</b> Após replicar o processo de preparação dos dados em <b>test_df</b> temos: 
</p>

```python
test_df.info()
```

!['Info total test'](https://henriquesilva.dev/info_total_test.png "Info total test")