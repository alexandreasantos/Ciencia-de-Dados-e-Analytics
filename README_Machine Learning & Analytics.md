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


## Limitações
- Série curta (2023–2024)  
- Modelos **univariados** (sem variáveis macro/exógenas)  
- LSTM obteve resultados fracos em escala de preços  
- Backtest simplificado (sem custos transacionais robustos)  
