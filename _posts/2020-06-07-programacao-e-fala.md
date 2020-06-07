---
layout: post
title: Programação na era da neurociência
---

## Intro

Em um estudo que saiu recentemente na revista *Communications of the ACM*, Janet Siegmund et al. usaram aparelhos de ressonância magnética, além de outros, para *scannear* o cérebro de estudantes em sessões de compreensão de código. O intuito era entender quais regiões do cérebro seriam ativadas nesse tipo de atividade. 

## Metodologia

Eles desenvolveram uma metodologia na qual os participantes tinham 60 segundos para compreender pequenos trechos de código, seguidos por um período de 30 segundos de descanso para a que o nível de desoxigenação do cérebro voltasse ao *baseline*, seguido por um período de 30 segundos em que os participantes identificavam erros de sintaxe em *snippets* de código, seguido por mais 30 segundos de descanso. Esse experimento era repetido 12 vezes. Eles então subtraíram das imagens geradas pela primeira sessão (compreensão de código), as imagens geradas pela sessão de identificação de erros de sintaxe. A ideia por trás da subtração é que as nas primeiras imagens, geradas pela compreensão de código, áreas subjacentes do cérebro, que não teriam a ver, propriamente, com a compreensão de código, seriam ativadas durante essa etapa do experimento. Ao subtrair as duas imagens, eles poderiam obter imagens que, teoricamente, estariam relacionadas apenas à compreensão de código.

![Figura extraída do paper](/img/program-comprehension.png "O método da subtração")

## Resultado surpreendente

Para a surpresa dos cientistas, as áreas ativadas pelo cérebro durante as sessões de compreensão de código estavam ligadas à compreensão da fala. OMG. Muito se fala que a programação esta intimamente ligada ao raciocínio lógico/matemático, porém eles não identificaram, nas imagens, partes do cérebro relacionadas a esse tipo de faculdade mental, o que é bastante surpreendente. Como os autores citam no texto, o grande cientista da computação Dijkstra já havia dito que para ser bem sucedido em programação, as pessoas deveriam ter uma boa educação em línguas. Portanto, podemos afirmar que a compreensão de programas está muito mais ligada à comunicação e expressão, do que com raciocínio lógico/matemático. O *paper* encontra-se disponível em sua totalidade em [2].

## Referências

[1] [https://medicalxpress.com/news/2020-06-language-brain-scans-reveal-coding.html](https://medicalxpress.com/news/2020-06-language-brain-scans-reveal-coding.html)

[2] [https://dl.acm.org/doi/10.1145/3347093](https://dl.acm.org/doi/10.1145/3347093)
