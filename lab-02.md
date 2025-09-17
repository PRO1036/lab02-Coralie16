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

La transparence est réglé le geom_density, car la transparence est réglé
indépendemment des données. On est entrain de faire du setting.

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
ggplot(plastic_waste, aes(x= plastic_waste_per_cap,y=mismanaged_plastic_waste_per_cap,colour = continent)) +
  geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

Réponse à la question…

### Exercise 5

``` r
# insert code here
```

``` r
# insert code here
```

Réponse à la question…

## Conclusion

Recréez la visualisation:

``` r
# insert code here
```
