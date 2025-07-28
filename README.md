# 📊 Telecom X – Parte 2: Prevendo Churn de Clientes

## 🧠 Descrição do Desafio

Dando continuidade à primeira etapa de análise exploratória, agora assumimos o papel de **Analista de Machine Learning Júnior** na Telecom X. Nossa missão é construir modelos preditivos que antecipem quais clientes têm maior chance de **cancelar os serviços (churn)**, auxiliando a empresa na tomada de decisões estratégicas de retenção.

---

## 🎯 Objetivos

- Realizar pré-processamento dos dados (limpeza, encoding, normalização).
- Analisar a correlação entre variáveis.
- Balancear as classes utilizando **SMOTE**.
- Treinar e comparar dois modelos preditivos distintos.
- Avaliar desempenho e gerar insights estratégicos.

---

## 🛠️ Etapas do Projeto

### 🔧 1. Preparação dos Dados

- **Remoção de colunas irrelevantes:** Eliminado o identificador único.
- **Encoding:** Aplicado `OneHotEncoder` com `ColumnTransformer` para variáveis categóricas.
- **Normalização:** Aplicada com `StandardScaler` apenas para modelos sensíveis à escala.
- **Balanceamento de Classes:** Utilizado **SMOTE** para lidar com desbalanceamento entre classes (`churn` ≈ 26%).

### 📊 2. Análise de Correlação

- Correlação negativa moderada entre `tenure` e churn (-0.35).
- Correlação perfeita entre `monthly_charges` e `contas_diarias` → variável `contas_diarias` removida.
- Outras variáveis como `total_charges` e `paperless_billing` mostraram correlação fraca, mas relevante.

### 📈 3. Análises Direcionadas

Realizadas visualizações para entender a relação entre variáveis numéricas e a evasão:

- **Boxplots** e **scatterplots** mostraram padrões claros:
  - Clientes com menor tempo de contrato (tenure) são mais propensos a churn.
  - Maiores valores de `monthly_charges` estão levemente associados a churn.

### ✂️ 4. Separação dos Dados

- Dados divididos em **80% treino** e **20% teste**, com estratificação para manter a proporção de churn.

---

## 🤖 Modelos Treinados

Foram treinados dois modelos distintos com abordagens complementares:

| Modelo               | Normalização | Sensível à Escala | Tipo              |
|----------------------|--------------|--------------------|-------------------|
| Regressão Logística  | ✅ Sim       | ✅ Sim             | Linear, baseline  |
| Random Forest        | ❌ Não       | ❌ Não             | Baseado em árvore |

---

## 📊 Avaliação dos Modelos

### 🔍 Regressão Logística

- **Acurácia:** 75%
- **Recall (Saiu):** 80%
- **F1-score (Saiu):** 0.63
- **AUC:** 0.84

### 🌲 Random Forest

- **Acurácia:** 78%
- **Recall (Saiu):** 49%
- **F1-score (Saiu):** 0.54
- **AUC:** 0.82

### 📋 Comparativo

| Métrica         | Regressão Logística | Random Forest  |
|-----------------|---------------------|----------------|
| Acurácia        | 75%                 | **78%**        |
| Precisão (Saiu) | 52%                 | **60%**        |
| Recall (Saiu)   | **80%**             | 49%            |
| F1-score (Saiu) | **0.63**            | 0.54           |
| AUC             | **0.84**            | 0.82           |

---

## 📌 Conclusões Estratégicas

- A **Regressão Logística** apresentou melhor capacidade de identificar clientes que irão cancelar (maior recall e AUC).
- O **Random Forest** apresentou melhor **precisão**, reduzindo falsos positivos.
- Ambos os modelos podem ser ajustados para melhor desempenho, especialmente com **ajuste do limiar de decisão**.
- O balanceamento com SMOTE foi essencial para tratar o desbalanceamento da classe minoritária.

---

## 🚀 Próximos Passos

- **Ajuste de hiperparâmetros** (GridSearch, RandomSearch).
- Aplicação de **XGBoost** como modelo adicional.
- Testar **Threshold Tuning** na Regressão Logística para equilibrar precisão e recall conforme objetivo de negócio.
- Implantação do modelo com melhores métricas de recall/precisão balanceadas.

---

## 👨‍💻 Autor

**Mateus Fernandes**  
Analista de Machine Learning Júnior | Técnico em Desenvolvimento de Sistemas  
[LinkedIn](https://www.linkedin.com) | [GitHub](https://github.com)

---
