Projeto MVP: Engenharia de Dados - Wine Dataset
Identificação
Nome: Maiara Cezar da Silva

Matrícula: 4052025001072

Objetivo do Projeto
Este projeto consiste na construção de um pipeline de dados completo utilizando a plataforma Databricks. O fluxo abrange as etapas de coleta, armazenamento, modelagem, transformação, catalogação e análise de dados, seguindo a arquitetura de medalhão (camadas Bronze, Silver e Gold). O objetivo final é extrair insights químicos de amostras de vinhos para responder a 15 perguntas analíticas específicas.

Dataset Utilizado
Nome: Wine Recognition Dataset.

Fonte: UCI Machine Learning Repository.

Descrição: O conjunto contém 178 registos de vinhos italianos, descritos por 13 atributos físico-químicos (como teor alcoólico, acidez málica, intensidade de cor, entre outros) e uma variável de classe.

Arquitetura do Pipeline
O processamento foi dividido em quatro fases principais:

Ingestão (Bronze): Upload manual do ficheiro original (.data / .txt) e carregamento inicial como tabela bruta em formato texto.

Transformação (Silver): Estruturação e tipagem dos dados em colunas específicas.

Refinação (Gold): Preparação dos dados para consultas SQL e análises estatísticas.

Catalogação: Criação de um catálogo de dados rastreável e documentado no ambiente Databricks.

Modelagem de Dados
Foi adotado o modelo Star Schema (Esquema Estrela) para organizar os dados analíticos:

Tabela Fato (fact_wine): Contém os identificadores e as métricas numéricas das amostras de vinho (álcool, cinzas, magnésio, fenóis, etc.).

Tabela Dimensão (dim_wine_class): Armazena as descrições das classes de vinho (Classes 1, 2 e 3).

Relacionamento: 1:N entre dim_wine_class e fact_wine através do campo Class.

Exemplos de Perguntas Respondidas
O pipeline foi validado através da execução de consultas para identificar:

Vinho com maior teor alcoólico.

Média de atributos (como cinzas e flavonoides) por classe de vinho.

Percentagem de vinhos com intensidade de cor acima de um determinado limite.

Desvios padrão e medianas de variáveis químicas específicas.

Tecnologias e Ferramentas
Plataforma: Databricks.

Linguagens/Processos: SQL para análise, ingestão de dados e transformações seguindo os princípios de engenharia de dados.
