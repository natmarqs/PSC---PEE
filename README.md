# PSC---PPEE (UnB)
#Aluna: Natália Andrade Marques
Repositório para comportailhamento das atividades realizadas na disciplina Privacidade e Segurança Cibernética do programa de Mestrado Profissional de Engenharia Elétrica (PPEE) da Universidade de Brasília
#####################################################################################################################################################################################################################

MVP: Modelagem Preditiva do Desmatamento no Brasil (Séries Temporais Univariadas)

**Visão Geral do Projeto**

Este projeto consiste em um Produto Mínimo Viável (MVP) de Machine Learning focado na previsão do desmatamento total anual (km^2) nos biomas brasileiros. O objetivo principal foi construir e comparar diferentes modelos de séries temporais univariadas (utilizando apenas o ano como feature) e aplicar a Otimização de Hiperparâmetros para encontrar a melhor solução preditiva.

O código foi desenvolvido em Python, utilizando o ambiente Google Colab, e a lógica de treinamento foi aplicada individualmente por bioma para capturar suas particularidades.

**Fonte de Dados**
Os dados utilizados são séries históricas de desmatamento provenientes do projeto PRODES (Monitoramento do Desmatamento na Amazônia Legal por Satélite) e foram agregados por bioma e ano.
Disponível em (última data visualizada em 29/09/2024): https://basedosdados.org/dataset/e5c87240-ecce-4856-97c5-e6b84984bf42?table=d7a76d45-c363-4494-826d-1580e997ebf0

  Granularidade: Desmatamento total anual em km^2 por bioma.
  Target: desmatado_anual_total_km2.
  Feature: ano.

**Metodologia e Modelos Avaliados**
A metodologia seguiu o ciclo padrão de forecasting: Separação Temporal, Modelagem, Otimização e Avaliação de Resultados.

  - Separação Temporal: A base foi dividida em Treino (dados históricos) e Teste (últimos 3 anos), estritamente sem o uso de validação cruzada (K-Fold tradicional) para evitar Vazamento de Dados (Data Leakage).

  - Modelos de Benchmark:

  - Baseline (Ingênuo): Previsão igual ao último valor observado (o benchmark mais difícil para séries temporais).

  - Regressão Linear (RL): Modelo de tendência simples para capturar a taxa de variação histórica.

**Modelo de Machine Learning:**

Random Forest Regressor (RF): Modelo não-linear robusto, treinado em duas versões (Inicial e Otimizada).

Otimização: Aplicada ao Random Forest utilizando Grid Search com Validação Cruzada (CV=3) para encontrar a melhor combinação de n_estimators e max_depth.

 **Resultados Finais e Conclusão**
A performance dos modelos foi avaliada no conjunto de Teste utilizando as métricas RMSE, MAE (ambos em km^2) e R2 Score.

<img width="714" height="257" alt="image" src="https://github.com/user-attachments/assets/0de60d76-34d5-49ef-b8ae-658c9932f4ff" />

**Melhor Solução:**

O Modelo Baseline obteve o menor erro (RMSE/MAE).
Conclusão: Este resultado, embora inesperado, indica que a volatilidade do desmatamento no período de teste foi baixa, fazendo com que o valor do último ano conhecido fosse o estimador mais preciso.

Melhor Modelo de Machine Learning: O Random Forest Regressor Otimizado foi o melhor modelo de ML, superando a Regressão Linear em mais de 1600 km2.

**Bibliotecas Utilizadas**
   - pandas (Manipulação e Agregação de Dados)

   - numpy (Cálculos Numéricos)

   - scikit-learn (Modelagem, Otimização - LinearRegression, RandomForestRegressor, GridSearchCV)

   - matplotlib e seaborn (Visualização)
