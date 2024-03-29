---
title: "Challenge 1: Defective Equipment"
description: "Dada uma relação entre 8 equipamentos e 17 sensores, o objetivo é determinar qual equipamento pode estar defeituoso com base no número de acionamentos registrados por cada sensor."
pubDate: "Feb 24 2024"
badge: "#I2A2"
tags: ["I2A2", "CHALLENGE-1", "PCA"]
slug: "challenge-1-defective-equipment"
heroImage: "/i2a2-bg.jpeg"
---

<p style="text-align: justify">
    Dada uma relação entre 8 equipamentos e 17 sensores, a análise objetiva identificar possíveis defeitos nos equipamentos com base no número de acionamentos registrados por cada sensor. O conjunto de dados inclui exclusivamente informações sobre o número de vezes que cada sensor foi acionado para cada equipamento.
</p>

!['Defective Equipament - XLSX'](https://henriquesilva.dev/defective-equipment-xlsx.png "Defective Equipament - XLSX")

<p style="text-align: justify">
    A estratégia adotada envolve a aplicação de técnicas estatísticas, incluindo a Análise de Componentes Principais (PCA).
</p>

!['Defective Equipament - Median'](https://henriquesilva.dev/defective-equipment-median.png "Defective Equipament - Median")

<p style="text-align: justify">
    Ao empregar a PCA, é possível reduzir a dimensionalidade dos dados e identificar padrões nas variações dos acionamentos entre os sensores. A análise estatística utiliza a média dos acionamentos como referência, permitindo identificar equipamentos que apresentam padrões significativamente diferentes da média, indicando potenciais falhas ou comportamentos anômalos.
</p>

!['Defective Equipament - PCA'](https://henriquesilva.dev/defective-equipment-pca.png "Defective Equipament - PCA")

<p style="text-align: justify">
    Destaca-se que a conclusão da análise sugere a capacidade de distinguir o <b>equipamento V3</b>, o qual exibe o maior número de sensores com acionamentos muito abaixo da média.
</p>

<p style="text-align: justify">
    <b>Obs.:</b> Variância explicada dos componentes: [0.45778535]
</p>

<b>GitHub:</b> [Challenge 1: Defective Equipment](https://github.com/henriquehsilva/I2A2-Training/tree/main/Challenge%201/Defective%20Equipment)
