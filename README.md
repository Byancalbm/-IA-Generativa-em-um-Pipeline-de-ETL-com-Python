# 📊 IA Generativa em um Pipeline de ETL com Python
## 📌 Visão Geral

Este projeto demonstra como integrar IA Generativa (ChatGPT/OpenAI) a um pipeline de ETL (Extract, Transform, Load) para criar mensagens de marketing altamente personalizadas no contexto do setor bancário.

O cenário simula um desafio real do Santander, no qual o objetivo é aumentar o engajamento dos clientes por meio de comunicações customizadas, com foco em educação financeira e investimentos, utilizando dados estruturados e inteligência artificial.

Aqui, tecnologia, dados e estratégia de negócio caminham juntos.

## 🎯 Objetivo do Projeto

Consumir uma base de dados de clientes a partir de um arquivo CSV

Extrair informações individuais de cada usuário

Utilizar IA Generativa para criar mensagens personalizadas sobre investimentos

Atualizar a lista de comunicações (“news”) de cada cliente

Tudo isso seguindo o conceito clássico de ETL, agora potencializado por IA.

## 🧠 Arquitetura do Pipeline ETL
CSV (IDs dos Clientes)
        ↓
     Extract
        ↓
     Transform
        ↓
 IA Generativa (OpenAI)
        ↓
       Load

## 📁 Estrutura de Dados

O projeto parte de um arquivo CSV simples (dados_cli.csv) contendo informações básicas dos clientes, como:

UserId

UserName

Esses dados são a base para personalização das mensagens.

## 🔹 Etapas do Pipeline
### 🟢 1. Extract (Extração)

Nesta etapa, os dados são carregados a partir do arquivo CSV utilizando Pandas. O foco é extrair os identificadores dos usuários e preparar os dados para processamento.

import pandas as pd

df = pd.read_csv('dados_cli.csv', sep='\t')
user_ids = df['UserId'].tolist()
print(user_ids)

### 🟡 2. Transform (Transformação)

Aqui os dados são organizados em uma estrutura padronizada, simulando o formato esperado por um sistema de backend ou API corporativa.

Cada usuário passa a ter:

id

name

news (lista onde serão inseridas as mensagens geradas pela IA)

import json

users = []
for index, row in df.iterrows():
    users.append({
        'id': row['UserId'],
        'name': row['UserName'],
        'news': []
    })

print(json.dumps(users, indent=2))


Essa estrutura facilita a integração com serviços externos e garante escalabilidade.

### 🔵 3. Geração de Mensagens com IA Generativa

Nesta fase, a API do ChatGPT (OpenAI) é utilizada para gerar mensagens personalizadas de marketing para cada cliente.

As mensagens:

São adaptadas ao perfil do usuário

Destacam a importância de investimentos

Seguem uma linguagem clara, educativa e estratégica

💡 Essa etapa representa o grande diferencial do projeto: transformar dados brutos em valor percebido pelo cliente.

### 🟣 4. Load (Carga)

Por fim, as mensagens geradas são inseridas na lista news de cada usuário, simulando a atualização de dados em um sistema bancário ou CRM.

🚀 Tecnologias Utilizadas

Python

Pandas

JSON

OpenAI API (ChatGPT)

Conceitos de ETL

IA Generativa aplicada a negócios

## 📈 Benefícios do Projeto

Comunicação personalizada em escala

Aumento do engajamento do cliente

Uso estratégico de IA no contexto financeiro

Pipeline simples, extensível e reutilizável

## 🔮 Próximos Passos (Evolução do Projeto)

Integração com APIs reais de clientes

Persistência em banco de dados

Segmentação avançada por perfil financeiro

Monitoramento de engajamento das mensagens

Deploy em ambiente cloud

## 🤝 Considerações Finais

Este projeto vai além do código. Ele demonstra como dados + IA + visão de negócio podem gerar impacto real em estratégias de marketing financeiro.