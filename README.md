# 🔍 Análise Comparativa: Regressão Logística vs. Naive Bayes em Detecção de Fraudes

Repositório desenvolvido para fins acadêmicos e práticos, com o objetivo de comparar o desempenho, o comportamento interno, a robustez a *outliers* e a calibração de probabilidade de dois algoritmos de Machine Learning (**Regressão Logística** e **Gaussian Naive Bayes**) aplicados a um cenário simulado de transações financeiras fraudulentas.

---

## 🚀 O que o projeto faz?
O script implementa um pipeline completo utilizando `scikit-learn` que engloba:
1. **Geração de dados sintéticos** (`make_classification`) simulando transações bancárias equilibradas (`weights=[0.5, 0.5]`).
2. **Redução de dimensionalidade** com `PCA` para visualização dos dados.
3. **Divisão e injeção de ruído/outliers** (`train_test_split` e alteração em `X_test`) para testar a robustez dos modelos.
4. **Treinamento e Avaliação** comparando métricas de `classification_report` (Precision, Recall, F1-Score).
5. **Inspeção de parâmetros internos** (`lr.coef_` e `nb.class_prior_`) para analisar a compacticidade dos modelos.
6. **Análise de confiança** utilizando `predict_proba`.

---

## 🛠️ Implementações Técnicas Relevantes
Durante a prática, utilizamos as seguintes funções e extrações para analisar qualitativamente os modelos:
* **Ajuste de Pesos (`weights=[0.5, 0.5]`):** Usado na criação dos dados para garantir um balanceamento equitativo entre as classes.
* **Atributo `lr.coef_` (Regressão Logística):** Puxa os pesos lineares diretos, demonstrando a alta compacticidade e o baixo consumo de memória do modelo.
* **Atributo `nb.class_prior_` (Naive Bayes):** Inspeciona as probabilidades iniciais a priori calculadas pelo modelo estatístico.
* **Método `predict_proba`:** Extrai as probabilidades preditivas de cada amostra para analisar o nível de calibração de confiança frente a transações reais e fraudulentas.

---

## 📊 Principais Conclusões da Análise
* **Compacticidade:** A Regressão Logística se mostrou mais enxuta e direta (resumindo o aprendizado em um vetor fixo de pesos), enquanto o Naive Bayes, por trás da fachada simples, acumula uma carga estatística maior (médias e variâncias de cada feição).
* **Robustez a Outliers:** A Regressão Logística manteve seus números intactos após a injeção de valores discrepantes, provando ser mais estável. Já o Naive Bayes sentiu o impacto e teve uma leve queda nas métricas.
* **Cenário Real (Sistema Bancário):** A Regressão Logística leva vantagem em ambientes de produção devido à sua estabilidade, velocidade de inferência, interpretabilidade e menor risco de erro frente a dados extremos.
