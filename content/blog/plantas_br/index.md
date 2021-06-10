---
title: "Histórico de descrições de plantas brasileiras"
excerpt: |
  Pequena análise temporal da taxa de descrição de plantas brasileiras. Nela observo como o número de descrições se comportou ao longo dos anos, a diferença entre os séculos, grupos taxonômicos e entre os estados brasileiros.
author:
  - name: Lucas Moraes
    url: https://lucasmoraes.io
date: 2021-01-02
categories:
  - Análise de dados
  - Leitura rápida
  - Data viz
  - Flora
---
<link href="{{< blogdown/postref >}}index_files/pagedtable/css/pagedtable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/pagedtable/js/pagedtable.js"></script>
<link href="{{< blogdown/postref >}}index_files/pagedtable/css/pagedtable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/pagedtable/js/pagedtable.js"></script>



# Teste

Teste

# Dados - Flora 2020

Nessa análise usei dados extraídos do projeto [Flora 2020](http://floradobrasil.jbrj.gov.br/reflora/PrincipalUC/PrincipalUC.do;jsessionid=1BF8C99966A4F63202D27DF3CFBA80B0) do Jardim Botânico do Rio de Janeiro, para gerar algumas visualizações. Como a compilação destes dados foi um processo longo, não vou tratar dela nesse post, mas todas etapas podem ser conferidas [em minhas Github pages](https://moraessaur.github.io/flora2020_analysis/), na íntegra e com código. A idéia aqui era fazer uma análise mais enxuta e pragmática.

Os dados estão organizados em uma tabela deinida como `df_master`, que contém uma série de informações sobre espécies nativas de plantas brasileiras:


```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──
```

```
## ✓ ggplot2 3.3.3     ✓ purrr   0.3.4
## ✓ tibble  3.1.2     ✓ dplyr   1.0.5
## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
## ✓ readr   1.4.0     ✓ forcats 0.5.1
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   id = col_double(),
##   major_group = col_character(),
##   family = col_character(),
##   scientific_name = col_character(),
##   desc_year = col_double(),
##   descriptor = col_character(),
##   life_form = col_character(),
##   vegetation_type = col_character(),
##   endemism = col_character(),
##   phytogeographic_domains = col_character(),
##   states = col_character(),
##   vernacular_name = col_character()
## )
```

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
  </script>
</div>

Das 12 colunas ddessa tabela, vou usar as informações contidas em cinco:

1. `desc_year`: ano de descrição da espécie
2. `desc_author`: nome do autor vinculado à descrição da espécie.
3. `scientific_name`: nome científico.
4. `states`: estados da federação em que a espécie ocorre.
5. `major_group`: a qual grande grupo taxonômico ela pertence.
6. `Endemism`: se a espécie é endêmica do Brasil ou não.


Vou fazer minhas análises e construir as visualizações com base nessas informações e derivações delas.

# Descrições ao longo do tempo
***

Como botânico, sei que o número de descrições de plantas brasileiras vem aumentando ao longo dos anos. Mas quero entender como que esses números se comportaram ao longo do tempo. Para isso agrupei o número de espécies descritas por ano e plotei um gráfico de linhas. Já aproveitei o trabalho e dividi também as informações por século, colocando diferentes cores para cada um:


```
## Warning: Ignoring unknown parameters: label.size
```

```
## `geom_smooth()` using method = 'loess' and formula 'y ~ x'
```

```
## Warning: Removed 1 rows containing non-finite values (stat_smooth).
```

```
## Warning: Removed 4 rows containing missing values (geom_smooth).
```

```
## Warning: Removed 253 rows containing missing values (geom_curve).
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

O sistema linneaniano foi criado em 1750, então é de se esperar que o número de descrições seja menor nessa época. A curva indica um aumento na taxa de descrições ao longo do século 18, seguida por leve diminuição na taxa em meados do século 19, onde finalmente assume uma taxa de crescimento constante a partir daí, com o ano com maior número de descrições sendo 2001. É bastante evidente a elevada taxa de descrição do século 21, informação que fica mais evidente quando comparamos os valores absolutos e a distribuição destes, por século:


```
## Warning: Removed 1 rows containing non-finite values (stat_boxplot).
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />
Os boxplots deixam clara a alta taxa de descrições do século 21, que tem uma mediana de aproximadamente 300 espécies descritas por ano. Os gráficos de barras (B) indicam que, embora apenas 20% do século 21 tenha passado, ele já tem cerca de 80% do total de descrições do século 20 inteiro.

Vou dar uma investigada mais a fundo no ano de 2001, olhando os autores mais prolíficos, em termos de descrições, para esse ano:

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":[""],"name":["_rn_"],"type":[""],"align":["left"]},{"label":["autor"],"name":[1],"type":["fct"],"align":["left"]},{"label":["total_descricoes"],"name":[2],"type":["int"],"align":["right"]}],"data":[{"1":"Menezes, M. & Dias, I.C.A. (Orgs.)","2":"504","_rn_":"1"},{"1":"Esteves, G.L.","2":"33","_rn_":"2"},{"1":"Torgan, L.C., Barreda, K.A. & Fortes, D.F.","2":"30","_rn_":"3"},{"1":"Berg, C.C.","2":"24","_rn_":"4"},{"1":"Dias, I.C.A. et al.","2":"23","_rn_":"5"},{"1":"Cristóbal, C.L.","2":"20","_rn_":"6"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>
O fato de o termo *Orgs.* aparecer no autor com maior número de descrições de 2001, indica se tratar de uma obra. Ainda, o número de espécies descritas associadas com esse nome é muito maior que a média dos demais autores, o que faz sentido, dado que a obra deve compilar descrições de vários. Uma busca rápida me mostrou que um livro entitulado [“Biodiversidade de algas de ambientes continentais do Estado do Rio de Janeiro”](https://www.researchgate.net/publication/44430175_Biodiversidade_de_algas_de_ambientes_continentais_do_Estado_do_Rio_de_Janeiro_organizadoras_Mariangela_Menezes_Izabel_Cristina_Alves_Dias), com as referidas autoras, foi publicado em 2001. Partindo do título, podemos pressupor que uma grande quantidade de algas foram descritas nesse ano. 

Normalmente, espera-se que o número absoluto de angiospermas descritas por ano seja maior que os demais grandes grupos (devido à sua diversidade), isso fica evidente quando os dados são agrupados por século e grupo taxonômico:

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />
A escala do eixo y foi convertida para log, dado que o baixo número relativo de descrições de gimnospermas acaba mascarando a presença delas. Gimnospermas aparecem descritas apenas no século 19 e 21, sendo a maioria no primeiro. Angiospermas correspondem ao grupo com maior número de descrições em todos séculos, embora a diferença entre estas e as algas seja bem menor no século 21. Isso em parte ocorre, de fato, pela alta de descrições de algas no ano de 2001, que teve mais algas descritas que angiospermas:

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />
O total de algas descritas nesse ano foi mais que o dobro que o de angiospermas, sendo que destas algas descritas, 90% estão vinculadas à obra citada anteriormente. 

Generalizando esses números, podemos investigar a distribuição do total de descrições/ano por grupo taxonômico, que também rende alguns *insights* interessantes:



```
## Warning: Ignoring unknown parameters: label.size
```

```
## Scale for 'fill' is already present. Adding another scale for 'fill', which
## will replace the existing scale.
```

```
## Warning: Ignoring unknown parameters: label.size
```

```
## Warning: Removed 14664 rows containing non-finite values (stat_ydensity).
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-1.png" width="672" />

Nesse gráfico é possível ver o pico na descrição de algas no ano de 2001. Também é interessante o fato de que, ao contrário das demais distribuições, os valores de densidade para as gimnospermas são maiores no século 19, fenômeno observado apenas neste grupo.

# Descrições entre estados da federação
***

Quero adicionar mais uma variável na análise: os estados de ocorrência das espécies. Além de algas terem tido alto número de descrições em 2001, a referida obra destas trata-se de espécies com ocorrência no estado do Rio de Janeiro. O quão marcante é essa diferença em relação aos demais estados? Isso pode ser observado plotando um *heatmap*:


<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-8-1.png" width="672" />
Este gráfico foi reduzido para englobar o intervalo entre 1990 e 2019. Entretanto, os valores de densidade se referem à amostra inteira, não apenas a esse intervalo. Fica evidente nele a importância do ano de 2001 (e das algas) no histórico de descrições anuais de plantas brasileiras, mesmo quando em comparação com os outros estados nesse período. Além disso, embora a tendência na taxa de descrições anuais seja aumentar conforme o tempo passa, a década entre 2000 e 2010 foi a com os maiores valores de descrições anuais de plantas (região demarcada por linhas tracejadas). 

Existe outra característica interessante nesse plot. Os estados foram ordenados, propositadamente, de acordo com suas regiões. Os estados localizados na parte inferior do gráfico são todos do sudeste do Brasil e pode-se ver uma clara concentração de maiores valores de densidade de descrições entre eles. A parte destes, apenas os estados da Bahia e do Amazonas parecem ter uma concentração significante o suficiente para ser vista, no gráfico pelo menos, o que indica um desbalanço no número de coletas entre os estados brasileiros.

Poderia ser argumentado que essas características estão ligadas à extensão territorial e, embora não seja minha proposta testar isso a fundo, essa questão pode ser testada graficamente: estados maiores tem maior número de espécies descritas?

Vou juntar mais algumas informações à tabela para plotar o gráfico abaixo: vou incluir a área dos estados em `\(km^2\)`, a proporção de espécies endêmicas do total descrito para cada estado e se os estados contém ou não fronteiras internacionais:


<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-1.png" width="672" />
O tamanho dos pontos e siglas no gráfico representa a área dos estados. A cor indica se um estado possui (vermelho) ou não possui (azul), fronteiras com outros **países**. O que pode ser visto, primeiramente, é que não necessariamente um estado grande possui um maior número número de espécies descritas. Nenhum dos maiores estados brasileiros (Amazonas, Pará e Mato Grosso), estão entre aqueles com maior número total de espécies descritas, sendo estes os estados de Minas Gerais, Bahia, Rio de Janeiro e São Paulo. O Rio de Janeiro, inclusive, é um dos menores estados do Brasil, embora tenha alta quantidade de espécies descritas. Isso em parte pode ser explicado por um viés em investimento em pesquisa e esforço de coleta.

Em relação ao endemismo, o tamanho dos estados parecem ter menos influência ainda na proporção destas. Entretanto, conforme o esperado, a presença de fronteiras internacionais nos estados tem grande relação com a proporção de espécies endêmicas dos mesmos: nenhum estado com proporção de espécies endêmicas maior que 40%, possui fronteiras internacionais. O contrário também é verdadeiro, no sentido de que todos estados com menos de 20% desta proporção possuem fronteiras internacionais.























































