# Análise de Gêneros Musicais com Clustering e SVD

Este repositório contém a resolução do trabalho final da disciplina "Álgebra Linear e Aplicações" (sme0142). O projeto foca na aplicação da Decomposição de Valores Singulares (SVD) e do algoritmo de clustering K-means para analisar um dataset de atributos musicais do Spotify, com o objetivo de identificar e visualizar padrões entre diferentes gêneros musicais.

**Autor:** Felipe de Castro Azambuja
**Data de Entrega:** 10/12/2023

## Descrição do Projeto

O objetivo principal deste trabalho é utilizar técnicas de Álgebra Linear para reduzir a complexidade de um grande conjunto de dados musicais e, em seguida, agrupar as músicas em clusters para identificar semelhanças com base em suas características sonoras.

O projeto segue as diretrizes propostas no documento `trabalho-alglin-1.pdf`, que sugere temas para o trabalho final, incluindo "Clustering SVD", o tema escolhido para este desenvolvimento.

## Metodologia Aplicada

A análise foi dividida em duas partes principais: uma teórica, que fundamenta os métodos utilizados, e uma prática, que demonstra a aplicação em Python.

### 1\. Pré-processamento e Tratamento dos Dados

1.  **Seleção de Características:** Foram selecionadas 9 características musicais relevantes do dataset do Spotify, como `danceability`, `energy`, `loudness`, `tempo`, entre outras.
2.  **Tratamento de Dados Ausentes:** Valores ausentes em colunas numéricas foram preenchidos com a média, enquanto a coluna `genre` teve seus valores ausentes preenchidos com a moda (o gênero mais frequente).
3.  **Agrupamento de Gêneros:** O dataset continha 523 subgêneros únicos. Para facilitar a análise, esses subgêneros foram mapeados para 15 categorias mais amplas, como "Pop", "Rock", "Electronic", "Hip-Hop/Rap", etc.
4.  **Codificação e Padronização:** Os gêneros categóricos foram transformados em formato numérico usando *One-Hot Encoding*. Em seguida, todas as características numéricas foram padronizadas (média 0 e desvio padrão 1) para garantir que todas as variáveis tivessem a mesma escala.

### 2\. Redução de Dimensionalidade com SVD

A Decomposição de Valores Singulares (SVD) foi aplicada à matriz de dados para reduzir sua dimensionalidade. O critério foi preservar pelo menos 80% da variância total dos dados. Isso permitiu reduzir o número de dimensões de 22 (após o *one-hot encoding*) para 5, mantendo a maior parte da informação relevante.

$$A = U \Sigma V^T$$

Onde $A$ é a matriz original, $U$ e $V$ são matrizes ortogonais e $\\Sigma$ é uma matriz diagonal com os valores singulares.

### 3\. Clustering com K-means

1.  **Determinação do Número de Clusters:** Foram utilizados o **Método do Cotovelo** e o **Silhouette Score** para encontrar o número ideal de clusters. O Silhouette Score atingiu seu pico em $k=2$, indicando que esta era a quantidade ótima de clusters para a melhor separação dos dados.
2.  **Aplicação do K-means:** O algoritmo K-means foi executado nos dados de dimensionalidade reduzida com $k=2$. O resultado obteve um Silhouette Score final de 0.37, indicando uma separação de qualidade moderada.

## Principais Resultados

A análise da distribuição dos "Grandes Gêneros" em cada um dos dois clusters revelou os seguintes padrões:

  * **Cluster 0:** Apresenta uma alta concentração de gêneros como **Pop**, **Alternative**, **Hip-Hop/Rap**, **Rock** e **Electronic**. Este cluster parece agrupar músicas com características sonoras mais populares e diversificadas.
  * **Cluster 1:** Contém uma frequência maior de gêneros como **Alternative**, **Lo-Fi**, **Pop**, **Classical** e **Soundtrack**. Este grupo sugere uma combinação de estilos musicais que, embora variados, compartilham características distintas dos gêneros predominantes no Cluster 0.

A sobreposição observada entre os clusters sugere que muitos gêneros, embora classificados de forma diferente, compartilham características sonoras semelhantes, o que é uma conclusão interessante sobre a música popular moderna.

## Visualização dos Clusters

O gráfico abaixo mostra a separação dos dois clusters após a redução de dimensionalidade com SVD. Cada ponto representa uma música, e as cores indicam o cluster ao qual pertence.

## Como Executar o Projeto

O projeto foi desenvolvido em um ambiente Google Colab. Para executá-lo:

1.  Faça o download do notebook `.ipynb`.
2.  Abra o Google Colab: [https://colab.research.google.com/](https://colab.research.google.com/)
3.  Vá em `File > Upload notebook` e selecione o arquivo `.ipynb`.
4.  Execute as células de código em sequência para reproduzir a análise.

### Dependências

As principais bibliotecas Python utilizadas são:

  * `pandas`
  * `numpy`
  * `scikit-learn`
  * `matplotlib`
  * `seaborn`

## Arquivos no Repositório

  * **`Projeto-Algelin.pdf`**: O relatório final do projeto, contendo toda a análise teórica, o código e a interpretação dos resultados.
  * **`trabalho-alglin-1.pdf`**: O documento original com as instruções e sugestões de temas para o trabalho final da disciplina.


Nota de Autoria

Este projeto foi desenvolvido para a disciplina de Álgebra Linear na USP, sob a orientação da Prof.ª Cynthia Lage Ferreira. O trabalho foi submetido academicamente em conformidade com as regras da disciplina, em trio. O código e o relatório contidos neste repositório refletem a minha contribuição individual para o projeto.
