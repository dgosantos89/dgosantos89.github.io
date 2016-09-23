---
title: "Exemplo de teste de APIs"
layout: post
date: 2016-09-23 16:20
tag:
- API
- REST
- PHP
blog: true
star: false
---

Exemplo de teste de APIs
========================

Este é um exemplo de teste automatizado de uma API utilizando frameworks PHP.
Para este exemplo iremos utilizar a API pública [Postmon](http://postmon.com.br/), que dado um determinado CEP ela retorna as suas informações. O modelo da chamada é o seguinte:

```
GET - http://api.postmon.com.br/v1/cep/01001001
```

Resposta:

```json
  {  
    "complemento": "lado par",  
    "bairro": "Sé",  
    "cidade": "São Paulo",  
    "logradouro": "Praça da Sé",  
    "estado_info": {  
      "area_km2": "248.222,362",  
      "codigo_ibge": "35",  
      "nome": "São Paulo"  
    },  
    "cep": "01001001",  
    "cidade_info": {  
      "area_km2": "1521,11",  
      "codigo_ibge": "3550308"  
    },  
    "estado": "SP"  
  } 
```

Para este teste escrevi a seguinte [Feature](https://raw.githubusercontent.com/dgosantos89/qa-walmart-php/master/features/SegundoExercicio.feature)

E para esta feature desenvolvi esta [Context](https://raw.githubusercontent.com/dgosantos89/qa-walmart-php/master/features/bootstrap/SegundoExercicioContext.php)
