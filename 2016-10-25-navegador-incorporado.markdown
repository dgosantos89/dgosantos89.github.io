---
title: "Navegador incorporado em aplicação"
layout: post
date: 2016-10-25 16:20
tag:
- UFT
- QTP
- WPF
blog: true
star: false
---

Aplicação com um Navegador incorporado
======================================
Como automatizá-la?
--------------------

Recentemente me deparei com um objeto de navegador incorporado em uma aplicação.  
Eu era capaz apenas de identificá-lo como um WinObject `navegador`,  
então não era possível acessar o conteúdo dentro desta página.

Foi então que encontrei uma solução na internet, utilizando a Register New Browser Control.  
Esta ferramenta permite a navegação, visualização de documentos  
e outras funcionalidades de navegador em um aplicativo não Web.  
O UFT não é capaz de reconhecer automaticamente funcionalidades de navegador  
em sua aplicação não Web como objetos Web, para isso é necessário utilizar esta ferramenta.  
  
  
Para abrir o Register New Browser Control, vá em: 
```
  Iniciar > 
      Todos os Programas > 
        HP Software > 
          HP Unified Functional Testing > 
            Tools > 
              Register New Browser Control.
```
  
Nesta janela insira o caminho absoluto para o arquivo .exe da sua aplicação e clique em Registrar.  
  
* Para remover uma aplicação registrada, entre com o caminho absoluto e clique em Cancelar Registro.  
