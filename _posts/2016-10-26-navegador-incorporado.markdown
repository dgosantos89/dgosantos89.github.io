---
title: "Aplicação com um Navegador incorporado"
layout: post
date: 2016-10-26 16:20
tag:
- UFT
- QTP
- Embedded browser
blog: true
star: false
---
  
![App](http://i66.tinypic.com/k0pbp.jpg)
  
  
Como automatizá-la?
===================
  
  
Recentemente me deparei com um objeto de navegador incorporado em uma aplicação desktop, como no exemplo acima, onde temos um navegador incorporado em uma planilha excel.  
Eu era capaz apenas de identificá-lo como um WinObject `navegador`,  
então não era possível acessar o conteúdo dentro desta página.  
  
Pesquisando sobre o assunto descobri que o UFT não identifica objetos Web se estes objetos estiverem em uma aplicação não Web.  
Foi então que encontrei uma solução utilizando a Register New Browser Control.  
Esta ferramenta permite a navegação, visualização de documentos  
e outras funcionalidades de navegador em um aplicativo não Web.  
  
Antes de mais nada, encerre o UFT e em seguida abra a ferramenta Register New Browser Control.  
Para abrir o Register New Browser Control, vá em:  
   
```
  Iniciar > 
      Todos os Programas > 
        HP Software > 
          HP Unified Functional Testing > 
            Tools > 
              Register New Browser Control.
```
  
Nesta janela insira o arquivo .exe da sua aplicação e clique em Registrar.  
  
Obs: Caso você queira especificar a aplicação localizada em um diretório  
você pode adicionar o caminho absoluto até o executável da aplicação,  
caso contrário o UFT reconhecerá todos os executáveis com o nome que você adicionou.
  
* Para remover uma aplicação registrada, entre com o caminho absoluto e clique em Cancelar Registro.  
  
Esta ferramenta é basicamente uma interface amigável que realiza uma alteração no arquivo mic.ini  
(contém as configurações padrão do UFT).  
Então caso você não tenha esta ferramenta à disposição, você pode alterar diretamente o arquivo mic.ini:   
Este arquivo pode ser encontrado em:  
    `C:\Program Files (x86)\HP\Unified Functional Testing\bin\`   
  
```
    1) Localize o arquivo mic.ini e edite utilizando o Notepad.  
    2) Procure pela seção [ie_hook] 
    3) Ao final da seção adicione o nome do executável da aplicação (ou seu caminho absoluto) e a defina como YES:  
        [ie_hook]  
        name=ie_hooks.dll  
        method=specific  
        explorer.exe=yes  
        iexplore.exe=yes  
        ie4.exe=yes  
        APLICAÇÃO.exe=yes  
```
