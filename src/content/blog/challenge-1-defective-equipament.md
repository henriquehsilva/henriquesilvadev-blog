---
title: "Challenge 1: Defective Equipament"
description: "Dada uma relação entre 8 equipamentos e 17 sensores, o objetivo é determinar qual equipamento pode estar defeituoso com base no número de acionamentos registrados por cada sensor."
pubDate: "Feb 24 2024"
badge: "#I2A2"
tags: ["I2A2", "CHALLENGE-1", "PCA"]
slug: "challenge-1-defective-equipament"
heroImage: "/naive-bayes-cover.png"
---

<p style="text-align: justify">
    Dada uma relação entre 8 equipamentos e 17 sensores, a análise objetiva identificar possíveis defeitos nos equipamentos com base no número de acionamentos registrados por cada sensor. O conjunto de dados inclui exclusivamente informações sobre o número de vezes que cada sensor foi acionado para cada equipamento. A estratégia adotada envolve a aplicação de técnicas estatísticas, incluindo a Análise de Componentes Principais (PCA).
</p>

!['Defective Equipament - XLSX'](https://henriquesilva.dev/defective-equipament-xlsx.png "Defective Equipament - XLSX")


<p style="text-align: justify">
    Ao empregar a PCA, é possível reduzir a dimensionalidade dos dados e identificar padrões nas variações dos acionamentos entre os sensores. A análise estatística utiliza a média dos acionamentos como referência, permitindo identificar equipamentos que apresentam padrões significativamente diferentes da média, indicando potenciais falhas ou comportamentos anômalos.
</p>

<p style="text-align: justify">
    Destaca-se que a conclusão da análise sugere a capacidade de distinguir o <b>equipamento V3</b>, o qual exibe o maior número de sensores com acionamentos muito abaixo da média.
</p>


<b>GitHub:</b> [Challenge 1: Defective Equipament](https://github.com/henriquehsilva/I2A2-Training/tree/main/Challenge%201/Defective%20Equipament)
