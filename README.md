# MVP – Engenharia de Dados  
## Análise Química do Wine Dataset  
*(UCI Machine Learning Repository)*

---

## 1.  Objetivo

Este MVP tem como objetivo construir um **pipeline de dados em nuvem** utilizando o **Databricks Community Edition** para analisar o **Wine Dataset**, um conjunto de dados amplamente utilizado em projetos de *Machine Learning*.

O pipeline contempla todas as etapas fundamentais de um projeto de Engenharia de Dados:

- Busca e coleta dos dados  
- Modelagem  
- Carga  
- Transformação  
- Análise exploratória  

Foi adotada a **Arquitetura Medallion (Bronze, Silver e Gold)** para garantir qualidade, governança e escalabilidade.

O problema central deste MVP é compreender **como os atributos químicos dos vinhos se relacionam entre si** e como influenciam características como **classe, intensidade e composição química**.

Para isso, são respondidas **15 perguntas analíticas**, listadas abaixo.

---

## 2.  Perguntas Analíticas

1. Qual vinho apresenta o maior valor alcoólico (*Alcohol*)?  
2. Qual é o menor valor de acidez málica (*Malic_acid*) registrado?  
3. Qual é a média de *Ash* para cada classe de vinho?  
4. Qual é a mediana da variável *Hue*?  
5. Qual é o valor máximo de *Proline* encontrado?  
6. Quantos vinhos possuem teor alcoólico acima de 13?  
7. Qual é a média de *Flavanoids* por classe?  
8. Qual vinho apresenta a maior *Color_intensity* e qual sua classe?  
9. Qual é a média de *Alcohol* para cada classe?  
10. Qual é o valor mínimo e máximo de *Total_phenols*?  
11. Quantos vinhos possuem *Nonflavanoid_phenols* acima de 0.4?  
12. Qual é a média de *Magnesium* para vinhos da Classe 3?  
13. Qual é o desvio padrão de *Alcalinity_of_ash*?  
14. Qual é a porcentagem de vinhos com *Color_intensity* acima de 5?  
15. Qual é a média de *Proline* entre vinhos com teor alcoólico acima de 13?

---

## 3.  Fonte dos Dados e Coleta

Os dados utilizados neste projeto pertencem ao clássico **Wine Dataset**, disponibilizado publicamente no **UCI Machine Learning Repository**.

- **Fonte oficial:** UCI Machine Learning Repository – Wine Dataset  
- **Descrição:**  
  O dataset contém **178 amostras de vinho**, com **13 variáveis químicas** e uma variável-alvo (**Class**).

---

### 3.1 Processo de Ingestão

O fluxo de ingestão seguiu as seguintes etapas:

1. Download local dos arquivos  
2. Upload dos dados no Databricks  
3. Armazenamento inicial no **DBFS**  
4. Processamento nas camadas:
   - **Bronze → Silver → Gold**

A tabela fato armazena os valores numéricos das medições químicas de cada amostra.

---

### 3.2 Características do Dataset

As variáveis representam medições laboratoriais, incluindo:

- Alcohol  
- Malic acid  
- Ash  
- Alcalinity of ash  
- Magnesium  
- Total phenols  
- Flavanoids  
- Nonflavanoid phenols  
- Proanthocyanins  
- Color intensity  
- Hue  
- OD280/OD315  
- Proline  

>  Por se tratar de dados laboratoriais, **não há dados sensíveis**, estando em conformidade com a **LGPD**.

---

## 4.  Modelagem e Catálogo de Dados

Para organização analítica, foi adotado o **Esquema Estrela (Star Schema)**.

### Estrutura:

- **Tabela Fato (`fact_wine_gold`)**  
  Armazena todas as métricas e variáveis químicas.

- **Tabela Dimensão (`dim_class_gold`)**  
  Contém as descrições das classes de vinho (1, 2 e 3).

---

### 4.1 📘 Catálogo de Dados

| Nome da Coluna           | Descrição                     | Tipo   | Variação Geral |
|--------------------------|-------------------------------|--------|----------------|
| Alcohol                  | Teor alcoólico                | double | 11.0 – 14.8    |
| Malic_acid               | Acidez málica                 | double | 0.7 – 5.8      |
| Ash                      | Cinzas                        | double | 1.36 – 3.23    |
| Alcalinity_of_ash        | Alcalinidade das cinzas       | double | 10 – 30        |
| Magnesium                | Magnésio                      | int    | 70 – 162       |
| Total_phenols            | Fenóis totais                 | double | 0.98 – 3.88    |
| Color_intensity          | Intensidade da cor            | double | 1.28 – 13.0    |
| Proline                  | Prolina                       | int    | 278 – 1680     |
| Class                    | Categoria do vinho            | int    | 1, 2, 3        |

---

## 5.  Carga (ETL) e Arquitetura Medallion

A arquitetura Medallion foi utilizada para garantir qualidade e governança dos dados:

- **Bronze:**  
  Dados brutos (*raw*), exatamente como ingeridos.

- **Silver:**  
  - Padronização de nomes  
  - Conversão de tipos  
  - Criação de identificadores  
  - Remoção de inconsistências  

- **Gold:**  
  Tabelas finais otimizadas para análises e consultas SQL.

---

## 6.  Análise

### 6.1 Qualidade dos Dados

Foram verificados:

- Ausência de valores nulos  
- Distribuição estatística  
- Coerência dos valores  
- Normalidade das variáveis  

O dataset foi validado como **pronto para análise**.

---

### 6.2 Análise das Perguntas

As 15 perguntas analíticas foram respondidas utilizando:

- **Spark SQL**
- **Python (Matplotlib / Seaborn)**

O notebook contém:

- Tabelas de métricas  
- Histogramas  
- Gráficos de dispersão  
- Gráficos de pizza  
- Comparações entre classes  
- Interpretação textual dos resultados  

---

## 7.  Autoavaliação

### 7.1 Atingimento dos Objetivos

O objetivo de construir um **pipeline completo de Engenharia de Dados no Databricks** foi atingido com sucesso, abrangendo ingestão, transformação, análise e documentação técnica.

---

### 7.2 Dificuldades Encontradas

As principais dificuldades enfrentadas foram:

- Compreensão da estrutura do **Databricks Community Edition**  
- Ajustes finos de **tipos de dados no ETL**  
- Construção da lógica de transição entre as camadas **Bronze, Silver e Gold**

---



Projeto desenvolvido como parte do portfólio acadêmico e profissional.
