Lab 02 - Plastic waste
================
Coralie Bodson
15 septembre 2025

## Chargement des packages et des données

``` r
library(tidyverse) 
```

    ## Warning: le package 'tidyverse' a été compilé avec la version R 4.3.3

    ## Warning: le package 'tibble' a été compilé avec la version R 4.3.3

    ## Warning: le package 'tidyr' a été compilé avec la version R 4.3.3

    ## Warning: le package 'readr' a été compilé avec la version R 4.3.3

    ## Warning: le package 'purrr' a été compilé avec la version R 4.3.3

    ## Warning: le package 'dplyr' a été compilé avec la version R 4.3.3

    ## Warning: le package 'forcats' a été compilé avec la version R 4.3.3

    ## Warning: le package 'lubridate' a été compilé avec la version R 4.3.3

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")
```

Commençons par filtrer les données pour retirer le point représenté par
Trinité et Tobago (TTO) qui est un outlier.

``` r
plastic_waste <- plastic_waste %>%
  filter(plastic_waste_per_cap < 3.5)
```

## Exercices

### Exercise 1

``` r
ggplot (plastic_waste, aes(x=plastic_waste_per_cap)) +
  geom_histogram(binwidth= 0.1)+
  facet_wrap (~continent)
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

### Exercise 2

``` r
ggplot(plastic_waste, aes(x=plastic_waste_per_cap, fill = continent)) +
  geom_density(alpha =0.4) 
```

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

La couleur (colour and fill) est réglé dans l’ aes dû au fait que l’on
associe différentes couleurs à différentes données. On est entrain de
faire du mapping.

La transparence est réglée dans le geom_density, car la transparence est
réglée indépendemment des données. On est entrain de faire du setting.

### Exercise 3

Boxplot:

``` r
ggplot(plastic_waste, aes(x= continent, y= plastic_waste_per_cap)) +
  geom_boxplot() +
  labs (x="continent", y="plastic_waste_per_cap")
```

![](lab-02_files/figure-gfm/plastic-waste-boxplot-1.png)<!-- -->

Violin plot:

``` r
ggplot(plastic_waste, aes(x= continent, y= plastic_waste_per_cap)) +
  geom_violin() +
  labs (x="continent", y="plastic_waste_per_cap")
```

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

Le graphique à violin permet de visualiser la quantité de personne qui
ont une certaine valeur de “plastic_waste_per_cap”. En effet, les
espaces plus larges repésentent un nombre d’individus élevé, alors que
les parties amincies représentent un nombre d’individus plus faible.

### Exercise 4

``` r
ggplot(plastic_waste, aes(x=mismanaged_plastic_waste_per_cap ,y=plastic_waste_per_cap,colour = continent)) +
  geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

Il est possible d’observer que plus la quantité de déchets par habitant
augmente, plus la quantité de déchets non-gérés par habitant augmente
aussi. Nous avons donc une relation positive entre ces deux variables.

### Exercise 5

``` r
ggplot(plastic_waste, aes(x= total_pop, y= plastic_waste_per_cap)) +
  geom_point()
```

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(plastic_waste, aes(x= coastal_pop, y= plastic_waste_per_cap)) +
  geom_point() 
```

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

Pour le graphique “plastic_waste_per_cap vs total_pop”, les données vont
au delà de 1e+09. Pour le graphique “plastic_waste_per_cap vs
coastal_pop”, les données se situent tous entre 0 et environ 2,80e+08.

À l’oeil nu, on dirait que les points sur le deuxième graphique sont
plus dispersés. Cependant, en regardant les valeurs sur l’axe des X, il
est possible de voir que c’est en fait le premier graphique qui présente
une plus grande dispersion des données.

Nous pouvons donc conclure que le deuxième graphique,
“plastic_waste_per_cap vs coastal_pop”, a une relation plus forte.

## Conclusion

Recréez la visualisation:

``` r
plastic_waste_coastal <- plastic_waste %>% 
  mutate(coastal_pop_prop = coastal_pop / total_pop) %>%
  filter(plastic_waste_per_cap < 3)


ggplot(plastic_waste, aes(x= coastal_pop/total_pop, y= plastic_waste_per_cap)) +
  geom_point(aes(colour = continent)) + 
  geom_smooth() +
  labs (title = "Quantité de déchets plastique vs Proportion de la population côtière",
        subtitle = "Selon le continent",
        x= "Proportion de la population côtière (Coastal/Total population)", 
        y= "Nombre de déchets plastiques par habitant")
```

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

    ## Warning: Removed 10 rows containing non-finite outside the scale range
    ## (`stat_smooth()`).

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/recreate-viz-1.png)<!-- -->
