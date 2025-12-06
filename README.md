 MVP – Engenharia de Dados
Análise Química do Wine Dataset (UCI Machine Learning Repository)
 Objetivo

Este MVP tem como objetivo construir um pipeline de dados em nuvem utilizando o Databricks Community Edition para analisar o Wine Dataset, um conjunto de dados amplamente utilizado em projetos de Machine Learning. O pipeline envolve as etapas de busca, coleta, modelagem, carga, transformação e análise dos dados, utilizando a Arquitetura Medallion (Bronze, Silver e Gold).

O problema que este MVP busca resolver é a necessidade de compreender como os atributos químicos dos vinhos se relacionam entre si e como influenciam características como classe, intensidade e composição química. Para isso, serão respondidas 15 perguntas analíticas, definidas antes da fase de coleta e essenciais para o entendimento do comportamento do dataset.

As perguntas são:

Qual vinho apresenta o maior valor alcoólico (Alcohol)?

Qual é o menor valor de acidez málica (Malic_acid) registrado?

Qual é a média de Ash para cada classe de vinho?

Qual é a mediana da variável Hue?

Qual é o valor máximo de Proline encontrado?

Quantos vinhos possuem teor alcoólico acima de 13?

Qual é a média de Flavanoids por classe?

Qual vinho apresenta a maior Color_intensity e qual sua classe?

Qual é a média de Alcohol para cada classe?

Qual é o valor mínimo e máximo de Total_phenols?

Quantos vinhos possuem Nonflavanoid_phenols acima de 0.4?

Qual é a média de Magnesium para vinhos da Classe 3?

Qual é o desvio padrão de Alcalinity_of_ash?

Qual é a porcentagem de vinhos com Color_intensity acima de 5?

Qual a média de Proline entre vinhos com teor alcoólico acima de 13?

Ao final, espera-se fornecer uma análise clara e estruturada das propriedades químicas do vinho, além de demonstrar a construção de um pipeline completo dentro do Databricks.

 Fonte dos Dados e Coleta

Os dados utilizados neste projeto pertencem ao clássico Wine Dataset, disponibilizado publicamente no UCI Machine Learning Repository.

🔗 Fonte oficial dos dados

UCI Machine Learning Repository – Wine Dataset
https://archive.ics.uci.edu/ml/datasets/wine

O dataset original contém 178 amostras de vinho e 13 variáveis químicas, além da variável-alvo (Class).

2.1 Tabela Fato – Wine (fact_wine_gold)

A tabela fato contém os valores numéricos representando medições químicas de cada amostra de vinho. Os dados foram disponibilizados originalmente em formato .csv/.data. No MVP, eles foram:

Baixados localmente

Carregados no Databricks via Upload Data

Armazenados inicialmente no DBFS

Processados pelas camadas Bronze → Silver → Gold

2.2 Características do Dataset

As variáveis representam medições laboratoriais, incluindo:

Alcohol

Malic acid

Ash

Alcalinity of ash

Magnesium

Total phenols

Flavanoids

Nonflavanoid phenols

Proanthocyanins

Color intensity

Hue

OD280/OD315

Proline

A variável Class identifica a categoria do vinho (1, 2 ou 3).

Por se tratar de dados numéricos laboratoriais, não há informações sensíveis, e o dataset é amplamente aceito para fins acadêmicos.

Modelagem e Catálogo de Dados

Para estruturar e organizar os dados, foi adotado o modelo Esquema Estrela, onde:

A tabela fato armazena todas as variáveis químicas.

A tabela dimensão corresponde a uma única dimensão: dim_wine_class, contendo as descrições das classes.

3.1 Estrutura do Esquema Estrela

Tabela Fato: fact_wine_gold
Contém os valores numéricos medidos para cada vinho.

 Tabela Dimensão: dim_class_gold
Contém as informações das classes 1, 2 e 3.

3.2 Catálogo de Dados

A seguir, alguns exemplos do catálogo:

Nome da Coluna	Descrição	Tipo	Variação Geral
Alcohol	Teor alcoólico	double	11.0 – 14.8
Malic_acid	Acidez málica	double	0.7 – 5.8
Ash	Cinzas	double	1.36 – 3.23
Alcalinity_of_ash	Alcalinidade das cinzas	double	10 – 30
Magnesium	Magnésio	int	70 – 162
Total_phenols	Fenóis totais	double	0.98 – 3.88
Color_intensity	Intensidade da cor	double	1.28 – 13.0
Proline	Prolina	int	278 – 1680
Class	Categoria do vinho	int	1, 2, 3

Esse catálogo auxilia na compreensão dos intervalos esperados e também na validação de qualidade dos dados.

Carga (ETL e Arquitetura Medallion)

A arquitetura utilizada segue o padrão Medallion:

 Bronze

Recebe os dados exatamente como foram carregados.

 Silver

Inclui:

padronização de nomes das colunas

conversão de tipos

criação de ID

remoção de inconsistências

 Gold

Tabelas finais otimizadas para análise e consultas SQL.

Todo o processo de carga está documentado no notebook.

 Análise

A análise contempla:

5A – Qualidade dos Dados

Foi verificado:

ausência de valores nulos

distribuição estatística

coerência dos valores

normalidade de variáveis

O dataset é considerado limpo e pronto para análise, pois é amplamente utilizado para fins acadêmicos.

5B – Análise das Perguntas

As 15 perguntas foram respondidas utilizando:

Spark SQL

Python

Matplotlib

Seaborn

Foram incluídos:

tabelas

métricas

histogramas

scatter plots

gráficos de pizza

comparações entre classes

Cada resposta inclui uma interpretação explicativa.

Todas as análises encontram-se no notebook principal.

 Autoavaliação
6.1 Atingimento dos Objetivos

O objetivo de construir um pipeline de dados completo no Databricks foi atingido com sucesso. As etapas contempladas incluem:

Coleta e ingestão dos dados

Modelagem em arquitetura Medallion

Construção de tabelas Delta

Análise SQL + Python

Visualizações interpretativas

Documentação técnica

As 15 perguntas foram respondidas de maneira clara e com suporte visual.

6.2 Dificuldades Encontradas

As principais dificuldades envolveram:

Entendimento da estrutura do Databricks Community Edition

Ajuste dos tipos de dados

Construção do pipeline Bronze → Silver → Gold

Execução dos gráficos no cluster gratuito

Apesar disso, nenhuma dificuldade comprometeu o objetivo final.
