---
title: "Exemplo utilizando Behat e Mink"
layout: post
date: 2016-09-21 16:20
tag:
- Behat
- Mink
- Exemplo
blog: true
star: false
---

Exemplo de teste utilizando Behat e Mink
========================================

Este é um exemplo de teste automatizado utilizando o Behat e o Mink. 
Este exemplo foi retirado da prova para a vaga de QA do Walmart.com. 

No site vamos validar a seguinte sequência de ações: 
----------------------------------------------------

* Procurar pelo termo "tv" na busca 
* Validar que a busca teve resultados 
* Clicar em um dos resultados e validar que a página do produto abriu corretamente 
* Adicionar o Produto ao carrinho 
* Abrir o carrinho e validar que o mesmo foi adicionado com sucesso 

Para este teste escrevi a seguinte ![Feature](https://raw.githubusercontent.com/dgosantos89/qa-walmart-php/master/features/PrimeiroExercicio.feature)

E para esta feature desenvolvi esta ![Context](https://raw.githubusercontent.com/dgosantos89/qa-walmart-php/master/features/bootstrap/PrimeiroExercicioContext.php)
