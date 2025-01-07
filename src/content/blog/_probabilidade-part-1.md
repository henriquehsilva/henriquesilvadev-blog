---
title: "Probabilidade Part-1"
description: "Algumas anotações de estudo inicial sobre probabilidade, tentando entender conceitos sobre modelo determinístico e probabilístico."
pubDate: "Feb 01 2024"
badge: "#I2A2"
tags: ["PROBABILIDADE", "IA"]
slug: "probabilidade-part-1"
heroImage: "/cara-coroa.png"
---

<h2>Determinístico</h2>

<p style="text-align: justify">
    A <b>sequência recursiva</b>, amplamente utilizada em campos como matemática e ciência da computação, destaca-se pela <mark>previsibilidade de seus elementos</mark>, devido sua regra de construção. A capacidade de antecipar com precisão qualquer elemento torna essa abordagem valiosa em modelagem de padrões e processos iterativos.
</p>

<p style="text-align: justify">
    Quanto a <b>modelos determinísticos</b>, podemos destacar a possibilidade de repetições, onde conhecendo-se a <mark>semente inicial e a regra de construção</mark> podemos predizer o seu comportamento. Esse conceito, presente em fundamentos físicos como eletricidade, mecânica e cinemática, permite a previsão exata da saída de experimentos sob <mark>condições iniciais conhecidas</mark>.
</p>

<h2>Probabilístico</h2>

<p style="text-align: justify">
    A transição para <mark>experimentos aleatórios</mark> introduz a incerteza, onde a <mark>predição exata da saída torna-se impossível</mark>. No entanto, os modelos probabilísticos entram em cena, permitindo a determinação das <u>probabilidades associadas a cada possível resultado</u>. Mesmo diante da imprevisibilidade individual de cada experimento, <mark>a análise de um grande conjunto de dados revela padrões</mark>.
</p>

<p style="text-align: justify">
    Conceitos fundamentais, como <mark>espaço amostral e eventos</mark>, fazem parte do cenário probabilístico. O <mark>espaço amostral é o conjunto de saídas possíveis</mark>, enquanto <mark>eventos representam os elementos desse conjunto</mark>. A <mark>relação entre eventos é definida por situações como evento impossível, evento certo, união e interseção, e a complementaridade (não ocorrer) de um evento</mark>.
</p>

<h3>Exemplo</h3>
<p style="text-align: justify">
    Qual a frequência com que sai cara frente ao número de experimentos?
</p>

```python
import numpy as np
import matplotlib.pyplot as plt

def coin_toss():
    result = np.random.choice([{1: 'cara'}, {0: 'coroa'}])
    return result

def is_heads(coin_toss_result):
    return coin_toss_result.get(1) == 'cara'

def experiment(n_attempts):
    arr_results = []

    for _ in range(n_attempts):
        coin_toss_result = coin_toss()
        arr_results.append(coin_toss_result)
    return arr_results

def n_heads(experiment_result):
    result = 0
    for coin_toss_result in experiment_result:
        if is_heads(coin_toss_result):
            result += 1
    return result

# Número máximo de experimentos
max_attempts = 1000

# Listas para armazenar os resultados
num_experiments = []
head_frequencies = []

# Realizar os experimentos variando o número de tentativas
for n_attempts in range(1, max_attempts + 1):
    results = experiment(n_attempts)
    head_count = n_heads(results)
    
    # Calcular a frequência de caras
    head_frequency = head_count / n_attempts
    
    # Armazenar os resultados
    num_experiments.append(n_attempts)
    head_frequencies.append(head_frequency)

# Criar o gráfico de linha
plt.plot(num_experiments, head_frequencies, marker='o')
plt.xlabel('Número de Experimentos')
plt.ylabel('Frequência de Cara')
plt.title('Variação da Frequência de Cara com o Número de Experimentos')
plt.grid(True)
plt.show()
```
<h3>Plot</h3>

!['Variação da Frequência de Cara com o Número de Experimentos'](https://henriquesilva.dev/plot_freq_cara.png "Variação da Frequência de Cara com o Número de Experimentos")