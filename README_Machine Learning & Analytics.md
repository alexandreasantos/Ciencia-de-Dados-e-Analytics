# MVP — Machine Learning & Analytics

## Autor  
- **Nome:** Alexandre Alves dos Santos de Campos  
- **Matrícula:** 2025000  

## Contexto do Projeto  
O mercado financeiro é altamente volátil e difícil de prever. Este MVP explora o uso de **modelos de regressão e classificação aplicados a séries temporais** para prever tendências no **Mini Dólar (DOLFUT)**, com base em dados de proxies do **Yahoo Finance** (`USDBRL=X`).  

## Objetivo
- Avaliar a aplicação de **modelos de Machine Learning** (regressão e classificação) sobre ativos locais e globais.  
- Investigar se é possível transformar dados históricos em **sinais operacionais mais robustos**, buscando vantagem preditiva em cenários de decisão.  

## Hipótese  
> É possível reduzir parcialmente a dificuldade de prever movimentos de mercado utilizando **regressões e modelos baseados em séries temporais** para extrair tendências a partir de variáveis locais e globais.  

## Dataset
- **Fonte:** Yahoo Finance  
- **Período:** 01/01/2023 – 31/12/2024  
- **Frequência:** diária  
- **Atributos coletados:**  
  - `Open`, `High`, `Low`, `Close`, `Adj Close`, `Volume`  
- **Feature engineering:**  
  - Retornos diários (`pct_change`, log-returns)  
  - Médias móveis, z-scores, índices sintéticos  
  - Normalização (MinMaxScaler, RobustScaler)  

##Pré-processamento
  - Tratamento de valores ausentes e reamostragem para dias úteis  
  - Cálculo de retornos (`pct_change`) e log-retornos  
  - Normalização (MinMaxScaler) para padronizar a escala dos preços  
  - Criação de features derivadas (lags, médias móveis, z-score)

## Modelos Utilizados
- **LSTM (Long Short-Term Memory)** — abordagem univariada sobre preços  
- **GBM (Gradient Boosting Machines)**  
  - Regressão: previsão de magnitude do retorno (`t+1`)  
  - Classificação: previsão direcional (↑/↓)  

## Técnicas Aplicadas  
- **Cross-validation temporal** (TimeSeriesSplit)  
- **Perdas robustas** (Huber Loss)  
- **Pesos amostrais** para dar mais relevância a grandes movimentos  
- **Baseline de Persistência** (preço de amanhã = preço de hoje)  

##Avaliação e Backtest
   - Métricas: RMSE, MAE, MAPE, MASE, acurácia direcional, F1, AUC  
   - Comparação com estratégia de **Buy & Hold**  
   - Cálculo de indicadores financeiros: Sharpe, CAGR, Max Drawdown  
   - Backtest simples com custo de transação configurável

## Resultados

### LSTM (Preços)  
- **RMSE:** ~0.196  
- **MAE:** ~0.159  
- **Acurácia direcional:** ~47%  
- → Não superou o baseline de persistência  

### GBM Regressão  
- **RMSE:** ~0.009  
- **MAE:** ~0.007  
- **Acurácia direcional:** ~51%  
- Melhor desempenho em **magnitude numérica**  

### GBM Classificação  
- **Accuracy:** ~0.52  
- **F1-Score:** ~0.53  
- **AUC:** ~0.51  
- **Backtest simples:** **+8.28%** acumulado (*possível efeito de ruído*)

## Requisitos
- Python 3.10 ou superior
- Bibliotecas principais:
  - `pandas`, `numpy`, `scipy`, `yfinance`
  - `matplotlib`, `plotly`
  - `scikit-learn`
  - `tensorflow` (para LSTM)
  - (opcional) `xgboost`, `lightgbm`, `prophet`, `statsmodels`

## Principais Conclusões
- A **persistência** (baseline) é um benchmark forte para o DOLFUT, devido à sua alta autocorrelação diária.  
- A **LSTM univariada** não superou a persistência usando apenas preços brutos.  
- O **GBM para classificação direcional** obteve alta acurácia, porém retorno financeiro inferior ao Buy & Hold.  
- Para superar o baseline, recomenda-se:
  - Uso de **log-retornos** ou janelas de previsão diferentes (ex.: média de 5 dias)  
  - Inclusão de **variáveis externas** (DXY, S&P500, juros, volatilidade)  
  - Ajuste fino de hiperparâmetros e maior complexidade de rede.

## Limitações
- Série curta (2023–2024)  
- Modelos **univariados** (sem variáveis macro/exógenas)  
- LSTM obteve resultados fracos em escala de preços  
- Backtest simplificado (sem custos transacionais robustos)  
