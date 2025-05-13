# Codificação de Variáveis Categóricas em Modelos Preditivos

Variáveis categóricas, precisam ser convertidas para valores numéricos antes de serem usadas em modelos de machine learning. A escolha da técnica adequada pode influenciar diretamente o desempenho e a capacidade de generalização do modelo. Neste documento, explicarei essa transformação de variáveis categóricas em representações numéricas. As opções pensadas foram:  **One-Hot Encoding**, **Label Encoding**, **Frequency Encoding** e **Target Encoding**. Justificarei a escolha do **Target Encoding** para aplicação na variável `district` e `type`. 

---

## Comparação entre técnicas

### 1. One-Hot Encoding

**Descrição**: Cria uma coluna binária (0 ou 1) para cada categoria.

**Vantagens**:
- Simples e amplamente utilizado.
- Funciona bem com modelos lineares e árvores de decisão.

**Desvantagens**:
- Pode gerar **grande explosão de colunas** (alta dimensionalidade).
- Ineficiente para variáveis com **alta cardinalidade** (como bairros, com centenas de valores).

#### A alta cardinalidade gerada por essa técnica foi o que me afastou de usa-la.

---

### 2. Label Encoding

**Descrição**: Atribui um número inteiro sequencial a cada categoria.

**Vantagens**:
- Rápido e simples.
- Sem aumento do número de colunas.

**Desvantagens**:
- Pode **induzir uma ordem artificial** entre categorias (ex: 0 < 1 < 2...), o que não é apropriado para variáveis nominais.
- Pode confundir modelos que interpretam magnitudes numericamente (como regressões).

#### A ordem que seria induzida, por mais que pareça fazer sentido, já que de alguma maneira, normalmente, casas são mais caras que apartamentos e bairros mais luxosos tem o metro quadrado mais caro, nem sempre é verdade.

---

### 3. Frequency Encoding

**Descrição**: Substitui cada categoria pela frequência com que ela aparece no dataset.

**Vantagens**:
- Simples e eficiente.
- Preserva informações úteis (ex: bairros mais comuns podem indicar imóveis mais acessíveis).

**Desvantagens**:
- Não considera diretamente a relação com a variável-alvo (ex: `rent`).

#### O fato de não ter nenhuma relação com a variável-alvo me fez acreditar que não seria uma boa escolha.

---

### 4. Target Encoding (ou Mean Encoding)

**Descrição**: Substitui cada categoria pela **média da variável-alvo** para aquele grupo. Por exemplo, o bairro “Moema” passa a ser representado pela média do aluguel nos imóveis localizados nele.

**Vantagens**:
- Reduz a cardinalidade para **uma única coluna numérica**.
- Captura diretamente a **influência da categoria sobre a variável-alvo**.
- Efetivo em modelos que utilizam relações estatísticas (regressões, árvores, etc).

**Desvantagens**:
- Pode causar **overfitting**, especialmente se o número de observações for pequeno para certas categorias.
- Requer cuidados como regularização ou aplicação com validação cruzada.


---

##  Escolha Justificada: Target Encoding

Optei por usar **Target Encoding**, pelas seguintes razões:

1. O Target Encoding **captura a relação direta entre o bairro e tipo com o valor de aluguel**, o que é fundamental neste problema.
2. Analisando a lógica por trás, separar bairros com a por média de aluguel parece uma boa tática para explicitar a relação. A mesma coisa para o tipo.
3. Não tem problemas com a alta cardinalidade, evita ordens artificais.

Apesar de parecer a melhor escolha de fato, preciso explicitar problemas e cuidados dessa técnica:

*Como o target encoding utiliza a variável alvo (rent) para codificar categorias, ele corre o risco de gerar **data leakage** — isto é, de permitir que o modelo “veja” informações do futuro durante o treinamento. Isso pode levar o modelo a memorizar os dados de treino, gerando **overfitting**, especialmente quando algumas categorias possuem poucas observações.
Por isso, técnicas como validação cruzada com **K-Fold**, **suavização (smoothing)** e **injeção de ruído** são frequentemente aplicadas para reduzir esses efeitos.

---

## Técnicas para evitar problemas no uso do Target Encoding

### K-Fold:

A técnica de K-Fold Target Encoding mitiga o vazamento de dados ao garantir que a codificação de uma observação seja feita sem usar sua própria variável-alvo. Isso é feito dividindo os dados em K partes (folds), calculando as médias em K-1 partes e aplicando na parte restante. Assim, cada instância recebe uma codificação baseada apenas em dados “externos”, simulando melhor um cenário de generalização.

Como?
* Para cada categoria, as médias serão calculadas usando somente dados de outros folds, sem acesso direto aos dados das médias.

### Suavização:

Combinar as médias do bairro com a média global do dataset.

### Ruido aleatório:

Isso adiciona um leve ruído para evitar que o modelo memorize valores exatos.
