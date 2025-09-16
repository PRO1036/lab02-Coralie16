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
# insert code here
```

Réponse à la question…

### Exercise 3

Boxplot:

``` r
# insert code here
```

Violin plot:

``` r
# insert code here
```

Réponse à la question…

### Exercise 4

``` r
# insert code here
```

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
