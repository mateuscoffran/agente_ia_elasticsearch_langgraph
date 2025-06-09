# Agente de IA para Elasticsearch utilizando LangGraph

## 🤖 O que é este projeto?

Este projeto implementa um Agente de IA que funciona como uma interface inteligente para bancos de dados Elasticsearch. O agente recebe perguntas em português e retorna consultas DSL do Elasticsearch junto com interpretações dos resultados, tornando a análise de dados mais acessível.

## 🏗️ Arquitetura

O agente é construído usando LangGraph, um dos frameworks mais poderosos para desenvolvimento de agentes de IA. A arquitetura é baseada em grafos com 8 nós especializados:

Fluxo de Processamento:

🔀 1º Nó - Router

- Classifica se a pergunta do usuário é sobre dados
- Retorna o mapeamento do índice Elasticsearch via tool call, caso o Nó entenda que a pergunta do usuário é sobre dados
- Rejeita perguntas fora do escopo

📝 2º Nó - ES Query Writer

- Gera consultas Elasticsearch DSL baseadas na pergunta do usuário
- Utiliza o mapeamento do índice para criar consultas precisas

🔍 3º Nó - QA Engineer

- Valida a qualidade das consultas geradas pelo ES Query Writer, aceitando-as ou não.

👔 4º Nó - Chief DBA

- Fornece feedback técnico para o ES Query Writer, para consultas rejeitadas pelo QA Engineer

⚡ 5º Nó - Execute Query

- Executa as consultas validadas no Elasticsearch

📊 6º Nó - Interpret Results

- Analisa e interpreta os resultados em português
- Gera títulos para possíveis visualizações

👤 7º Nó - Human Interaction

- Permite interação do usuário (Human in the Loop)
- O usuário decide se deseja visualizações gráficas

📈 8º Nó - Plot Results

- Gera visualizações automáticas dos dados, por meio de gráficos baseados nos resultados da consulta

## 🌟 Características Principais
- Validação Multi-camada: Sistema de validação com loops de até 3 iterações de revisão
- Tool Calling: Implementado com decorators @ e método .bind_tools()
- Human in the Loop: Interação humana para controle do fluxo
- Memória Persistente: O agente mantém contexto das conversas

## 🛠️ Tecnologias

- LangGraph: Framework principal para construção do agente
- Elasticsearch: Banco de dados para consultas
- Python: Linguagem de desenvolvimento
- Large Language Models (LLM): Para processamento de linguagem natural

## 🚀 Como Usar

- Configure sua instância do Elasticsearch
- Configure as credenciais de acesso
- Execute o agente
- Faça perguntas em português sobre seus dados
- Receba consultas DSL e interpretações automáticas
- Opte por visualizar gráficos quando solicitado
