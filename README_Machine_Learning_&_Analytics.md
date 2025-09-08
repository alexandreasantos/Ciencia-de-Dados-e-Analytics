# MVP — Análise de Dados para Mercado Financeiro

Este projeto faz parte do desenvolvimento de um MVP para análise exploratória de dados financeiros, com o objetivo de entender a influência dos principais ativos locais (Brasil) e globais sobre os contratos futuros **Mini Índice (WINFUT)** e **Mini Dólar (DOLFUT)** negociados na B3.

## Sobre o Projeto

- Análise baseada em dados históricos de preços coletados via **Yahoo Finance**.
- Construção de **índices sintéticos locais e globais**, que representam a força relativa do mercado interno e externo.
- Avaliação de **correlações, sensibilidades e padrões contextuais** para apoiar a geração futura de sinais operacionais.
- Este projeto é a **etapa inicial de um pipeline de Machine Learning**, focado na geração de sinais de compra, venda ou neutralidade no mercado de renda variável.

---

## Objetivo do MVP

- Entender a **relação estatística** entre ativos locais e globais.
- Avaliar como o contexto macroeconômico impacta o comportamento dos contratos futuros (WINFUT e DOLFUT).
- Construir ferramentas analíticas que serão utilizadas como base para a implementação de modelos de **Inteligência Artificial (IA)** na próxima etapa do projeto.

---

## Fontes de Dados

- **Período:** 01/01/2023 até 01/01/2025.
- **Fonte:** [Yahoo Finance](https://finance.yahoo.com/).
- **Dados:** Preço de fechamento ajustado (Adjusted Close) de ativos locais e globais.

---

## 🏛️ Ativos Analisados

### 🔹 **Ativos Locais**
- Ações: VALE3, PETR4, ITUB4, PETR3, BBAS3, BBDC4, B3SA3, ABEV3, WEGE3, RENT3
- Índice IBOV (^BVSP) — Proxy do WINFUT
- USDBRL=X — Proxy do DOLFUT

### **Ativos Globais**
- S&P500 (^GSPC)
- NASDAQ (^IXIC)
- DOW JONES (^DJI)
- DXY (Índice do Dólar)
- Treasury 10Y (^TNX)
- Petróleo WTI (CL=F)
- Bitcoin (BTC-USD)
- Índice México (^MXX)

---

## Principais Ferramentas e Tecnologias

- **Python**
- **Pandas, NumPy** — Manipulação e análise de dados
- **Matplotlib, Seaborn, Plotly** — Visualização de dados
- **yFinance** — API para coleta de dados do mercado
- **Jupyter Notebook / Google Colab** — Ambiente de desenvolvimento

---

## Etapas Realizadas

1. ✅ **Coleta dos Dados:** Download dos preços históricos dos ativos selecionados.
2. ✅ **Tratamento dos Dados:** Limpeza, alinhamento temporal e remoção de valores ausentes.
3. ✅ **Normalização:** Dados escalados entre 0 e 1 para análises comparativas.
4. ✅ **Estatísticas Descritivas:** Análise de médias, desvios padrão, quartis e outliers.
5. ✅ **Matriz de Correlação:** Avaliação das relações lineares entre ativos locais e globais.
6. ✅ **Análise de Sensibilidade:** Cálculo da influência dos grupos econômicos no WINFUT e DOLFUT.
7. ✅ **Construção dos Índices Sintéticos:** Representação do contexto local e global de mercado.
8. ✅ **Visualização:** Gráficos e dashboards para interpretação dos dados.

---

## Exemplos de Resultados

-  O WINFUT é altamente sensível ao setor financeiro (bancos) e commodities no Brasil.
-  O DOLFUT é mais influenciado por fatores externos, como o DXY (índice do dólar) e os juros dos EUA (Treasury10Y).
-  A correlação entre ativos locais é muito mais forte que com ativos globais no comportamento do WINFUT.

---

## Observações Importantes

> Este projeto não se destina a ser uma recomendação financeira, mas sim uma **ferramenta acadêmica e experimental** para estudo de análise de dados no contexto financeiro.

> Fatores como **guerras, crises, pandemias e eventos inesperados não são previsíveis** e podem afetar os resultados, gerando falsos positivos nos modelos preditivos futuros.

---

## Próximos Passos

- Implementação de modelos de **Machine Learning**:
  - Classificação binária, multiclasses e regressão.
- Construção de pipelines de dados para uso em tempo real.
- Deploy de modelos em produção (API, WebApp ou integração com plataformas de trading).

---

## Licença

Este projeto é acadêmico e para fins educacionais, desenvolvido no contexto da disciplina **"Análise de Dados e Boas Práticas" da PUC-Rio**.

---

## Autor

**Alexandre Alves dos Santos de Campos**  
**Matrícula:** 2025000  

---
