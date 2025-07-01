---
title: "QiA: Como rodar o copiloto de QA com IA no Slack"
layout: post
date: 2025-06-30 23:20
tag:
- Slackbot
- LLM
- IA
- QA
blog: true
star: false
---

QiA: Como rodar o copiloto de QA com IA no Slack
===============================================

Neste post, vou te mostrar como rodar o QiA localmente com Node.js + ngrok e também como fazer o deploy em produção com Docker.

Pré-requisitos
--------------

- Node.js 18+
- Conta no Slack com permissão para criar apps
- Chave da OpenAI (ou outro provedor LLM)
- Conta no ngrok (opcional para testes locais)

### 1. Clone o projeto

```bash
git clone https://github.com/dgosantos89/qia-slackbot.git
cd qia-slackbot
npm install
```

### 2. Crie seu app no Slack


1. Acesse https://api.slack.com/apps
2. Clique em "Create New App > From scratch"
3. Dê um nome (ex: QiA) e selecione seu workspace
4. Em "OAuth & Permissions", adicione os escopos:
   - chat:write
   - app_mentions:read
   - channels:history
   - groups:history
5. Instale o app e copie o Bot Token (xoxb...)
6. Em "App-Level Tokens", crie um com connections:write (xapp-...)
7. Em "Event Subscriptions":
   - Ative a opção
   - Use uma URL do ngrok com /slack/events (ver abaixo)
   - Adicione o evento: app_mention

### 3. Configure o .env

Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:

```YAML
SLACK_BOT_TOKEN=xoxb-...
SLACK_SIGNING_SECRET=...
OPENROUTER_API_KEY=org-...
OPENROUTER_API_KEY=...
OPENROUTER_BASE_URL=https://openrouter.ai/api/v1
OPENROUTER_MODEL=mistralai/mistral-7b-instruct:free
```

### 4. Rode localmente com ngrok

Em um terminal:

`npm start`

Em outro terminal:

`ngrok http 3000`

Copie a URL do ngrok e use em "Event Subscriptions" no Slack:

https://abc123.ngrok.io/slack/events


### 5. Teste no Slack

No canal onde o app está instalado, mencione o bot:

@qia O que devo testar nesse fluxo de reembolso parcial?

O bot irá responder com sugestões de testes, aplicando técnicas como:

- Valores-limite
- Fluxos alternativos
- Casos negativos

### 6. Deploy (exemplo com Docker)

Você pode criar uma imagem Docker do QiA e fazer o deploy em qualquer ambiente com suporte a containers, como:

- AWS ECS Fargate
- Google Cloud Run
- Azure App Service
- Railway / Render / Fly.io

> Basta garantir que a aplicação esteja acessível publicamente e exponha o endpoint /slack/events para o Slack.

### 7. Contribua!

O QiA é um projeto em evolução. Se você quiser testar, melhorar, adaptar ou sugerir algo, acesse:

https://github.com/dgosantos89/qia-slackbot


### 8. Rode com Docker (alternativa ao Node local)

Se preferir, você pode rodar o QiA com Docker, sem precisar instalar dependências localmente.

## Usando Docker Compose

O repositório já inclui um `docker-compose.yml` pronto. Basta executar:

```bash
docker-compose --env-file .env up --build
```

Isso irá subir o bot na porta 3000, usando as variáveis do `.env`.

Certifique-se de que seu endpoint `/slack/events` esteja acessível ao Slack local via ngrok ou no ambiente.
