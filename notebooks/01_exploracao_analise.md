# Análise Exploratória de Dados de Imóveis

Análise detalhada de três visualizações gráficas dos dados numericos de imóveis: (1) boxplot, (2) historiograma e (3) matriz de correlação entre essas variáveis. Essas análises têm como objetivo entender melhor o comportamento das variáveis e suas relações.

---

## 1. Boxplot

### Boxplot de `rent`
* A mediana (linha central da caixa) está entre R$2.000 e R$2.500, o que indica que metade dos imóveis tem aluguel abaixo desse valor.
* A maioria dos valores está concentrada até R$4.000, como mostra a caixa e os “bigodes”.
* Existem muitos outliers acima de R$4.000, alguns chegando a mais de R$25.000

### Boxplot de `bedrooms`
* A mediana está em 2 quartos, com a maioria dos imóveis tendo entre 1 e 3 quartos.
* Há alguns outliers com 5 e 6 quartos, indicando imóveis maiores e menos comuns.
* O gráfico é bastante simétrico, o que sugere que não há uma grande distorção nos dados.

### Boxplot de `garage`
* A maioria dos imóveis tem entre 0 e 2 vagas, com a mediana próxima de 1 vaga.
* Existem outliers com até 6 vagas, o que novamente sugere imóveis de alto padrão.
* Esse dado pode ser interessante como fator discriminante em modelos, já que imóveis com mais vagas tendem a ter perfil mais caro.

### Boxplot de `area`
* A mediana está por volta de 60 a 80 m², típico de apartamentos em áreas urbanas.
* A maior parte dos imóveis está entre 40 e 120 m², mas há muitos outliers chegando a 600 m².
* Assim como o aluguel, a área tem uma distribuição assimétrica com muitos extremos altos.

---

## 2. Histogramas com curvas de distribuição


### Distribuição de `rent`

* Distribuição **altamente assimétrica** (cauda longa à direita).
* Pico em torno de **R\$ 1.500 a R\$ 2.000**, o que sugere que a maioria dos aluguéis se concentra nessa faixa.
* Valores superiores a **R\$ 10.000** são raros e possivelmente correspondem a imóveis de luxo.

### Distribuição de `bedrooms`

* Distribuição **discreta multimodal**, com picos claros em **1, 2 e 3 quartos**.
* Isso reflete a oferta predominante no mercado residencial.
* Poucos imóveis têm mais de 4 quartos.

### Distribuição de `garage`

* Distribuição também discreta, com maior concentração em **0, 1 e 2 vagas de garagem**.
* Não é comum haver mais de 3 vagas, o que é coerente com o padrão de imóveis urbanos.

### Distribuição de `area`

* Distribuição fortemente assimétrica, semelhante à de `rent`.
* A maioria dos imóveis tem área **entre 50 e 100 m²**, com poucos acima de 300 m².

Essas distribuições ajudam a entender o perfil dos imóveis disponíveis no mercado.

---

## 3. Matriz de Correlação entre Variáveis


A matriz de correlação mostra como as variáveis estão linearmente relacionadas entre si. Destaques:

* `rent` apresenta correlação **moderada** com `area` (0.67) e `garage` (0.62), indicando que essas variáveis influenciam mais fortemente o valor do aluguel.
* `bedrooms` também possui correlação relevante com `area` (0.73) e `garage` (0.66), o que é esperado, já que mais quartos exigem mais espaço e frequentemente vêgas adicionais.
* A correlação entre `garage` e `area` também é alta (0.73), sugerindo que imóveis maiores tendem a ter mais vêgas de garagem.

Essas correlações indicam um **perfil integrado** dos imóveis: imóveis maiores têm mais quartos, mais vêgas e aluguéis mais altos.

---

## Conclusão

Principais informações capturadas por essa exploração.

* A maioria dos imóveis possui até 3 quartos, 2 vagas de garagem e área entre 50 e 150 m².
* O valor do aluguel é influenciado mais fortemente pela área e pela disponibilidade de garagem.
* Existem muitos valores extremos no aluguel e na área.


