MVP de Engenharia de Dados | Wine Dataset
MVP de Engenharia de Dados – Análise do Wine Dataset (UCI)

Este repositório contém o desenvolvimento completo de um pipeline de engenharia de dados utilizando o Wine Dataset (UCI Machine Learning Repository) dentro da plataforma Databricks, aplicando a Arquitetura Medallion (Bronze, Silver e Gold), consultas SQL, visualizações em Python, modelagem e análise exploratória dos dados.

O objetivo principal foi responder 15 perguntas analíticas relacionadas às características químicas dos vinhos, demonstrando a construção de um fluxo completo de ingestão, limpeza, transformação e análise no ambiente de nuvem.

 Objetivos do Projeto

Construir um pipeline de dados na nuvem usando Databricks

Aplicar a arquitetura Medallion (Bronze, Silver e Gold)

Criar tabelas estruturadas com Spark e SQL

Realizar análises estatísticas e exploratórias

Desenvolver visualizações em Python (Matplotlib, Seaborn)

Responder às 15 perguntas analíticas propostas

Documentar modelagem, qualidade dos dados e autoavaliação

 Tecnologias Utilizadas

Databricks Community Edition

Apache Spark (SQL + DataFrames)

Python

Pandas

Matplotlib

Seaborn

Arquitetura Medallion

Bronze → dados crus

Silver → dados limpos

Gold → dados prontos para análise

GitHub para versionamento

                   

 Perguntas Respondidas no Projeto

Maior valor de Alcohol

Menor valor de Malic_acid

Média de Ash por classe

Mediana de Hue

Maior valor de Proline

Quantidade de vinhos com Alcohol > 13

Média de Flavanoids por classe

Maior Color_intensity e sua classe

Média de Alcohol por classe

Min e Max de Total_phenols

Qtde de vinhos com Nonflavanoid_phenols > 0.4

Média de Magnesium da Classe 3

Desvio padrão de Alcalinity_of_ash

% de vinhos com Color_intensity > 5

Média de Proline nos vinhos com Alcohol > 13

Cada pergunta contém:

SQL

Gráfico em Python

Texto interpretativo

Modelagem e Arquitetura

O pipeline foi construído conforme a Arquitetura Medallion:

 Bronze

Dados crus carregados no DBFS via upload.

 Silver

Tratamentos aplicados:

renomeação de colunas

conversões numéricas

criação de chave id_wine

verificação de consistência

 Gold

Tabela analítica final utilizada nas 15 perguntas.

 Relatório Completo

 Para visualizar todos os gráficos, tabelas e interpretações:
relatorio_mvp_wine.html (se você exportar o HTML)

Pipeline completo desenvolvido em Databricks
 Pós-graduação em Ciência de Dados
