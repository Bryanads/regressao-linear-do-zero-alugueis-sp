## Modelo de Regressão Linear Manual

Este documento descreve todas as etapas que usarei para construir um modelo de regressão linear simples **sem o uso de bibliotecas como scikit-learn**. O objetivo é entender profundamente o funcionamento interno da regressão linear, tanto do ponto de vista **matemático** quanto **computacional**.

---

## 1. Objetivo do Modelo

Nosso objetivo é prever o valor do **aluguel (`rent`)** de um imóvel com base em variáveis como:

* `area` (área útil)
* `bedrooms` (número de quartos)
* `garage` (número de vagas)
* `district_te` (bairro) 


Usarei **Regressão Linear Múltipla**, pois temos mais de uma variável independente.

---

## 2. Entendimento Matemático da Regressão Linear Múltipla

A Regressão Linear Múltipla é representada pela seguinte equação:

$$
\hat{y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_n x_n
$$

Onde:

* $\hat{y}$ é a variável que queremos prever (neste caso, `rent`)
* $x_1, x_2, ..., x_n$ são as variáveis independentes (`area`, `bedrooms`, `garage` e `district_te`)
* $\beta_0$ é o intercepto (valor de y quando todas as variáveis são 0)
* $\beta_1, \beta_2, ..., \beta_n$ são os coeficientes de regressão (pesos que indicam a contribuição de cada variável)

**Objetivo:** Encontrar os valores de $\beta$ que minimizam o erro entre a previsão e o valor real.

Essa minimização é feita por meio do método dos **mínimos quadrados ordinários (OLS)**:

$$
\boldsymbol{\beta} = (X^T X)^{-1} X^T y
$$

Onde:

* $X$ é a matriz com as variáveis preditoras (incluindo uma coluna de 1s para o intercepto)
* $y$ é o vetor de valores observados (aluguel)
* $\beta$ é o vetor de coeficientes a ser calculado

---

## 3. Preparação dos Dados

Antes de aplicar a fórmula, precisamos garantir que os dados estejam preparados:

### a) Seleção das variáveis

Selecionaremos apenas as colunas relevantes: `rent`, `area`, `bedrooms`, `garage`, `district_te`.

### b) Normalização:

Para melhor desempenho numérico, podemos normalizar os dados (subtrair a média e dividir pelo desvio padrão). Isso não é estritamente necessário, mas pode ajudar no ajuste.


### c) Separação em treino e teste

Dividiremos o conjunto de dados em duas partes:

* **Treinamento:** 80% dos dados
* **Teste:** 20% dos dados

Isso nos permite ajustar o modelo em um subconjunto e avaliar seu desempenho em dados não vistos.

---

## 4. Implementação do Algoritmo

Vamos codificar todas as operações com base em álgebra linear, usando apenas `numpy` para operações matriciais.

### a) Montagem da matriz X e vetor y

* Adicionamos uma coluna de 1s à matriz X para o intercepto $\beta_0$
* y será o vetor com os valores de `rent`

### b) Cálculo dos coeficientes $\beta$

Utilizaremos a fórmula:

$$
\beta = (X^T X)^{-1} X^T y
$$

Usaremos `numpy.linalg.inv` para a inversa e `numpy.dot` para multiplicações.

### c) Previsão (ŷ)

Depois de obter os coeficientes, aplicamos:

$$
\hat{y} = X \beta
$$

---

## 5. Avaliação do Modelo

Para medir o desempenho do modelo, calcularemos métricas como:

### a) Erro Quadrático Médio (MSE)

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^n (y_i - \hat{y}_i)^2
$$

### b) Coeficiente de Determinação ($R^2$)

$$
R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2}
$$

Esse valor indica o quão bem o modelo explica a variação da variável dependente. Quanto mais próximo de 1, melhor.

---

## 6. Visualizações (Opcional)

Podemos usar gráficos para verificar visualmente:

* Comparação entre valores previstos e reais
* Resíduos (diferença entre y e ŷ)

---

## 7. Conclusão

COm essas etapas, foi possível:

* Treinar um modelo de regressão linear **do zero**
* Compreender o que está por trás dos coeficientes gerados
* Avaliar o desempenho e possíveis limitações

---