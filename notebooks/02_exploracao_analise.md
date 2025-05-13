# Nessa sessão, adicionaremos à analise, os valores de `type` e `district`.


### Boxplot de `district_te`

* A mediana está próxima de 3.200, com a maioria dos valores concentrados entre 3.000 e 3.500.
* Há muitos outliers distribuídos em faixas específicas, indicando que alguns bairros têm codificações bem distintas.
* Isso sugere que o bairro é uma variável categórica codificada numericamente, e sua variabilidade pode indicar influência sobre o perfil dos imóveis.

### Boxplot de `type_te`

* A maioria dos valores está fortemente concentrada entre 3.000 e 3.300, com a mediana em torno de 3.200.
* Muitos outliers ocorrem em valores mais altos, acima de 3.500, o que pode representar diferentes tipos de imóveis menos comuns.
* Como é uma variável codificada de tipo (provavelmente casa, apartamento, kitnet etc.), essa distribuição reforça que há **poucos tipos predominantes** e **outros menos frequentes**, mas com potencial influência nos preços.

---


### Distribuição de `district_te`

* A distribuição apresenta **múltiplos picos** (multimodal), indicando **vários bairros com forte presença no dataset**.
* Os valores se concentram principalmente entre **2.800 e 3.500**, o que sugere que alguns bairros são significativamente mais representados.
* Como `district_te` é uma variável **codificada por Target Encoding**, essa variação pode refletir **diferenças nos aluguéis médios por bairro**, o que pode influenciar diretamente os modelos preditivos.

### Distribuição de `type_te`

* A distribuição tem dois picos principais, um em torno de **2.250** e outro entre **3.200 e 3.300**, sugerindo **dois grupos de tipos de imóvel bem distintos**.
* Isso pode indicar, por exemplo, a separação entre casas e apartamentos, ou imóveis residenciais e comerciais.
* O uso de Target Encoding também aqui reforça a ideia de que **certos tipos de imóveis têm maior influência no valor do aluguel**.

---

## 3. Matriz de Correlação entre Variáveis

A matriz de correlação mostra como as variáveis estão linearmente relacionadas entre si. Destaques:

* `rent` apresenta correlação **moderada** com `area` (0.67) e `garage` (0.62), indicando que essas variáveis influenciam mais fortemente o valor do aluguel.
* `bedrooms` também possui correlação relevante com `area` (0.73) e `garage` (0.66), o que é esperado, já que mais quartos exigem mais espaço e frequentemente vagas adicionais.
* A correlação entre `garage` e `area` também é alta (0.73), sugerindo que imóveis maiores tendem a ter mais vagas de garagem.
* `district_te` e `type_te` apresentam correlações fracas com as demais variáveis (valores abaixo de 0.45), indicando que características como localização codificada e tipo de imóvel têm menor relação linear com os outros atributos quantitativos.

Essas correlações indicam um **perfil integrado** dos imóveis: imóveis maiores têm mais quartos, mais vagas e aluguéis mais altos.

---

## Conclusão

Principais informações capturadas por essa exploração.

* A relação entre o valor do aluguel e as variávies de bairro e tipo tem uma relação menor do que o esperado.
* Ainda que mais baixas que as outras variáveis, vemos que o distrito ainda tem forte influência em aluguel (0.45)
* Muito mais baixa que as outras variáveis, vemos que o tipo tem somente (0.16) de influência com o aluguel. 
    * Vale ressaltar que a maior relação de tipo está com o destrito, logo, podemos fazer um estudo sobre isso, já que aparentemente os bairros mostram incidências proporcionais do tipo. 
    * Provavelmente **não usaremos o tipo como atributo para o nosso modelo**, devido a baixa influência.





