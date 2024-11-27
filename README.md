# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Administração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Classificação de Grãos de Trigo com Machine Learning

## Integrantes: 
- <a href="https://www.linkedin.com/in/joseandrefilho">Jose Andre Filho</a>

## Professores:
### Tutor 
- <a href="https://www.linkedin.com/in/lucas-gomes-moreira-15a8452a/">Lucas Gomes Moreira</a>
### Coordenador
- <a href="https://www.linkedin.com/in/profandregodoi/">André Godoi Chiovato</a>


## Introdução

Este projeto visa automatizar o processo de classificação de grãos de trigo utilizando aprendizado de máquina, aplicando a metodologia CRISP-DM. Em cooperativas agrícolas de pequeno porte, a classificação dos grãos é realizada manualmente, o que pode ser demorado e sujeito a erros humanos. Com o uso de modelos de aprendizado de máquina, é possível aumentar a eficiência e precisão deste processo.

## Objetivo

O objetivo deste projeto é aplicar diferentes algoritmos de classificação para identificar variedades de grãos de trigo com base em suas características físicas. O projeto consiste em analisar e pré-processar os dados, treinar e comparar diferentes modelos de classificação, otimizar os modelos e extrair insights relevantes sobre o desempenho de cada algoritmo.

## Estrutura do Projeto
```
.
├── assets/                                       # Recursos visuais utilizados no projeto (logos, imagens)
├── data/                                         # Dados utilizados no projeto
│   └── seeds_dataset.txt                         # Conjunto de dados 'Seeds Dataset' para treinamento e teste
├── notebooks/                                    # Notebooks Jupyter contendo o código e análise
│   └── classificacao_graos_ml_notebook.ipynb     # Notebook principal com análise e modelagem dos dados
└── requirements.txt                              # Arquivo com as dependências do projeto
```

## Etapas do Projeto

### 1. Análise e Pré-processamento dos Dados

- Importamos o dataset "Seeds" e exibimos as primeiras linhas para nos familiarizarmos com sua estrutura.
- Calculamos estatísticas descritivas, como média, mediana e desvio padrão para cada característica.
- Visualizamos a distribuição das características utilizando histogramas e boxplots, e utilizamos gráficos de dispersão para identificar relações entre os atributos.
- Tratamos valores ausentes e aplicamos normalização utilizando `StandardScaler` para preparar os dados para os modelos de classificação.

### 2. Implementação e Comparação dos Modelos de Classificação

- Os dados foram divididos em conjuntos de treinamento (70%) e teste (30%).
- Foram utilizados três algoritmos de classificação: **K-Nearest Neighbors (KNN)**, **Support Vector Machine (SVM)** e **Random Forest**. Esses modelos foram escolhidos por suas características complementares:
  - **K-Nearest Neighbors (KNN)**: O KNN é um algoritmo simples e intuitivo, que classifica os pontos de acordo com seus vizinhos mais próximos. Ele é frequentemente utilizado como baseline para verificar o desempenho inicial dos modelos, pois é fácil de entender e implementar. O KNN é particularmente útil para detectar padrões locais nos dados, mas pode ser sensível a outliers e a escalas diferentes dos atributos, sendo necessário o pré-processamento dos dados (como normalização).
  - **Support Vector Machine (SVM)**: O SVM é um algoritmo poderoso para problemas de classificação e é eficaz quando há uma clara separação entre as classes. Ele funciona muito bem em conjuntos de dados de alta dimensionalidade e utiliza um hiperplano para maximizar a margem entre as diferentes classes, garantindo uma boa generalização dos resultados. O SVM é adequado para lidar com conjuntos de dados que apresentam margens de separação complexas e pode ser ajustado para lidar com casos onde os atributos não são linearmente separáveis.
  - **Random Forest**: O Random Forest é um algoritmo de ensemble que combina diversas árvores de decisão, sendo robusto e menos suscetível a overfitting em comparação com modelos individuais de árvores. Ele cria várias árvores de decisão em subconjuntos dos dados e tira uma média dos resultados, o que melhora a robustez e a precisão do modelo. Além disso, o Random Forest fornece estimativas da importância dos atributos, o que ajuda a entender quais características dos grãos mais influenciam na classificação, sendo muito útil para insights sobre os dados.

- Cada modelo foi treinado e avaliado com base em métricas de desempenho como acurácia, precisão, recall, F1-score e matrizes de confusão.
- Foi realizada uma comparação dos desempenhos dos diferentes algoritmos.

##### Por que não escolhemos Naive Bayes e Regressão Logística?

- **Naive Bayes**: O Naive Bayes é um algoritmo eficiente e rápido, especialmente para problemas de classificação de texto e dados categóricos. No entanto, ele assume independência entre os atributos, o que nem sempre é verdade no caso dos atributos físicos dos grãos de trigo, como área, perímetro e compacidade. Esses atributos são correlacionados, o que pode prejudicar a precisão do modelo. Portanto, preferimos algoritmos que conseguem lidar melhor com correlações entre os atributos, como o Random Forest.

- **Logistic Regression**: A Regressão Logística é um método linear que funciona bem quando há uma clara separação linear entre as classes. No entanto, os dados dos grãos podem ter relações mais complexas, que não são facilmente capturadas por um modelo linear. Modelos como o SVM e o Random Forest conseguem capturar essas relações complexas de forma mais eficaz, garantindo uma melhor separação entre as classes.

### 3. Otimização dos Modelos

- Utilizamos a técnica de **Grid Search** para encontrar os melhores hiperparâmetros para cada modelo.
- Cada modelo foi re-treinado utilizando os melhores hiperparâmetros encontrados, e a acurácia e outras métricas de desempenho foram novamente avaliadas.
- Houve uma melhora significativa no desempenho dos modelos após a otimização, especialmente para o Random Forest.

### 4. Interpretação dos Resultados

- **Random Forest** apresentou o melhor desempenho geral, seguido pela **SVM**.
- **KNN** foi mais sensível à presença de outliers e teve um desempenho inferior em relação aos demais modelos.
- A técnica de **Grid Search** ajudou a otimizar os modelos e melhorar a capacidade de generalização.

## Como Executar o Projeto

1. **Clonar o Repositório**: Clone o repositório em sua máquina local.
2. **Instalar Dependências**: Instale as bibliotecas necessárias listadas no arquivo `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```
3. **Executar o Notebook**: Abra o notebook Jupyter (`.ipynb`) localizado na pasta `notebooks` e siga as células passo a passo para reproduzir a análise e os resultados obtidos.

## Tecnologias Utilizadas

- **Python**: Linguagem principal para análise de dados e aprendizado de máquina.
- **Jupyter Notebook**: Ambiente interativo para desenvolvimento e documentação.
- **Bibliotecas**: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.

## Conclusão

A aplicação de modelos de aprendizado de máquina para classificação de grãos de trigo mostrou-se eficiente, com o modelo **Random Forest** apresentando os melhores resultados. A metodologia CRISP-DM foi utilizada para garantir um processo estruturado e bem documentado, permitindo otimizar os modelos e extrair insights significativos a partir dos dados analisados.

## Licença
<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>

