---
title: "Probabilidade Part-2 (Naive Bayes)"
description: "Algumas anotações de estudo inicial sobre probabilidade, Naive Bayes: Como funciona esse algoritimo de classificação."
pubDate: "Feb 03 2024"
badge: "#I2A2"
tags: ["PROBABILIDADE", "IA", "CLASSIFICAÇÃO"]
slug: "probabilidade-part-2"
heroImage: "/bayes.png"
---

<h2>Distribuição Condicional</h2>

<p style="text-align: justify">
    Se já sabemos que um evento X ocorreu, isso pode (ou não) mudar a probabilidade de outro evento Y.
    Definindo a nova probabilidade nova como P(Y|X)(probabilidade de Y dado X)
</p>

<h2>Problema Proposto</h2>

<p style="text-align: justify">
    Imagina que temos um teste que detecta se temos ou não câncer. Esse teste tem uma acurácia de 90% para qualquer um dos lados.
    O que isso significa:
    <ul>
        <li>Se a pessoa tem câncer e faz o teste, 90% dos casos o teste diz que a pessoa tem câncer.</li>
        <li>Se a pessoa não tem câncer e faz o teste, 90% dos casos o teste diz que a pessoa não tem câncer.</li>
    </ul>
</p>

<h3>Vamos a questão:</h3>

<p style="text-align: justify">
    Uma pessoa fez o teste e foi diagnosticada com câncer. Qual a probabilidade dessa pessoa ter câncer? (Em um primeiro momento a maioria das pessoas cai em uma armadilha instintiva, responendendo que a probabilidade é de 90%.)
</p>

<h3>Porque do erro:</h3>

<p style="text-align: justify">
    O problema é que falta uma informação para responder a questão, que é:
    <ul>
        <li>Qual a porcentagem da população que tem câncer?</li>
    </ul>
</p>

<h3>Vamos aplicar em um cenário hipotético</h3>

- Vamos imaginar que 1% da população tem câncer;
- Vamos imaginar que temos uma população de 1000 pessoas;

!['cenário hipotético'](https://henriquesilva.dev/draw-01.jpeg "cenário hipotético")

<p style="text-align: justify">
    Nesse cenário a quantidade de pessoas que o teste diagnosticou com câncer foi de:
    <mark>108 pessoas</mark>.
    Mas dessas 108 pessoas <mark>apenas 9 de fato tem câncer</mark>.
    Então qual a probabilidade da pessoa ter câncer, nesse nosso cenârio?
</p>

!['resultado cenário hipotético'](https://henriquesilva.dev/prob-part2-img2.jpeg "resultado cenário hipotético")

<p style="text-align: justify">
    O motivo dessa porcentagem está no fato de que apenas 1% da população tem câncer.
    Mesmo o teste tendo um precisão alta de 90% de acurácia, é gerado um grande número de falsos positivos, sendo maior que a quantidade de pessoas que o teste diz ter a doença.
</p>

<h2>Naive Bayes (Conceito Teórico)</h2>

<p style="text-align: justify">
    O teorema de Bayes <mark>é o método principal para compreender a probabilidade de algum evento</mark>, P(A|B), dado alguma nova informação, P(B|A), e uma crença prévia na probabilidade do evento, P(A):
</p>

!['Teorema de Bayes'](https://henriquesilva.dev/naive-bayes.jpeg "Teorema de Bayes")

