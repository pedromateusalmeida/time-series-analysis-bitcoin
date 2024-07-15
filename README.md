![Case time series using bitcoin](https://github.com/pedromateusalmeida/time-series-analysis-bitcoin/blob/main/btc_gif.gif)

# Estrutura do Projeto
- Pacotes e Funções
- Extração de Dados
- Análise Exploratória de Dados
- Pré-processamento de Dados
- Modelagem
- Avaliação de Modelos
- Conclusão

# Extração de Dados
Os dados foram extraídos de várias fontes financeiras, incluindo yfinance, e foram armazenados em dataframes pandas para análise posterior.

# Tratamento de valores ausentes.
Transformações de variáveis.
Criação de novas features.
Normalização e padronização de dados.

# Análise Exploratória de Dados (EDA)
Foi realizada uma análise exploratória detalhada dos dados para entender suas características principais. Isso incluiu:

Visualizações de distribuição de dados.
Análise de correlação.
Visualizações de dados ausentes usando missingno.
Pré-processamento de Dados
O pré-processamento dos dados incluiu:


# Modelagem
Foram realizados alguns testes estatísticas na etapa de modelagem. 

- Correlação de Pearson
- Power Predict Score (PPscore)
- Decomposição da serie temporal
- Teste de Hurst
- Teste de Variância Reescalonada
- Teste Dickey-Fuller
- Teste de Kpss
- Teste Phillips-Perron
- Teste de Shapiro-Wilk
- Teste de Skewness e Kurtosis
- Autocorrelação (ACF e PACF)
- Teste de Ljung-Box

# Treinamento 
Vários modelos foram testados para prever séries temporais e outras variáveis dependentes. Entre os modelos testados estão:

- Regressão Linear
- ARIMA/ARIMAX
- SARIMA/SARIMAX
- Exponential Smoothing
- Prophet
- XGBoost
- LSTM
- Modelo Estrutural

# Avaliação de Modelos
Os modelos foram avaliados utilizando diversas métricas, incluindo:

Mean Squared Error (MSE)
Root Mean Squared Error (RMSE)
Mean Absolute Error (MAE)
R-squared (R²)
Testes Utilizados

Foram utilizados diversos testes estatísticos para avaliar a qualidade dos modelos, tais como:
Teste de Durbin-Watson
Teste de Ljung-Box
Teste de Breusch-Pagan

# Resultados

| Metric/Model                        | Regressão Simples | Regressão Múltipla | Sklearn MultiLinear | Exp Smoothing Simple | Exp Smoothing Trend | ARIMA (1,1,0) | ARIMA (2,1,0) | ARIMA (3,1,0) | ARIMA (5,1,0) | SARIMA (Sem Refit) | SARIMA (Com Refit) | XGBoost       | Prophet         | LSTM             | Modelo Estrutural |
|-------------------------------------|-------------------|--------------------|---------------------|----------------------|---------------------|---------------|---------------|---------------|---------------|--------------------|--------------------|----------------|-----------------|------------------|-------------------|
| R-squared                           | 0.000             | 0.364              | 0.3346              | -                    | -                   | -             | -             | -             | -             | -                  | -                  | 0.8681         | 0.9005          | -                |            |
| Teste de Breusch-Pagan              | -                 | (488.66, <0.001)   | -                   | -                    | -                   | (0.92, 0.336) | (0.31, 0.573) | (0.64, 0.421) | (0.13, 0.714) | (10.68, <0.001)    | (10.68, <0.001)    | (80.68, <0.001) | (922.19, <0.001) | -                | (206.69, <0.001)  |
| MSE (Mean Squared Error)            | -                 | 447789.09          | -                   | 970481.54            | 960754.67           | 2285065.57    | 1961931.09    | 1803275.09    | 1712470.34    | 1662679.20         | 1659616.23         | 39525916.03    | 30965251.12      | 1839383.90       | 864105.24         |
| MAE (Mean Absolute Error)           | -                 | 417.20             | 433.39              | 582.08               | 576.97              | 1019.51       | 949.73        | 917.30        | 882.59        | 830.29             | 829.99             | 3273.99        | 3959.51          | 855.29           | 404.40            |
| RMSE (Root Mean Squared Error)      | -                 | 669.17             | 719.96              | 985.13               | 980.18              | 1511.64       | 1400.69       | 1342.86       | 1308.61       | 1289.45            | 1288.26            | 6286.96        | 5564.64          | 1356.24          | 929.57            |
| Durbin-Watson                       | 2.101             | 1.994              | 1.5813              | -                    | -                   | 2.3358        | 2.1504        | 2.0913        | 2.0239        | 2.4469             | 2.4469             | 2.0461         |            |           | 2.0353            |
| Shapiro-Wilk Test (residuals)       | (0.9456, <0.001)  | (0.8288, <0.001)   | (0.8304, 0.0)       | (0.8386, <0.001)     | (0.8385, <0.001)    | (0.9368, <0.001) | (0.9416, <0.001) | (0.9468, <0.001) | (0.9377, <0.001) | (0.8768, <0.001)   | (0.8768, <0.001)   | (0.7443, <0.001) | (0.9456, <0.001)  | (0.8862, <0.001)  | (0.6495, 0.0)    |
| Ljung-Box (L1) (Q)                  | -                 | -                  | -                   | -                    | -                   | 130.17        | 33.77         | 9.11          | 1.12          | 32.34              | 11.43             | -               | -                | -                | 0.88              |
| Skew                                | -0.132            | -0.562             | -0.4365             | 0.2037               | 0.1706              | 0.31          | 0.20          | 0.10          | -0.07         | 0.40               | 0.39               | 1.0031          | -0.8437          | 1.007            | -0.3223           |
| Kurtosis                            | 15.928            | 15.333             | 11.7013             | 8.8726               | 8.9037              | 15.42         | 14.54         | 15.40         | 16.69         | 12.84              | 12.60             | 15.3332         | 2.1454           | 9.082            | 18.5532           |
| Jarque-Bera (JB)                    | 21861.03          | 16039.215          | 18002.12            | -                    | -                   | 22555.43      | 19458.83      | 22442.43      | 27324.48     | 12643.70           | 12029.96           | 8509.06        | 1087.38          | 1193.74          | 39620.17          |
