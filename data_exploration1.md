Introduction
------------

Please include introduction here.

``` r
dt_train <- fread("train.csv")
dt_store <- fread("store.csv")
```

Taking a peek at the data
-------------------------

Let's first look at the data we have by looking at the first few rows.

### train.csv

``` r
kable(head(dt_train), caption = "First few rows of train.csv")
```

|  Store|  DayOfWeek| Date       |  Sales|  Customers|  Open|  Promo| StateHoliday | SchoolHoliday |
|------:|----------:|:-----------|------:|----------:|-----:|------:|:-------------|:--------------|
|      1|          5| 2015-07-31 |   5263|        555|     1|      1| 0            | 1             |
|      2|          5| 2015-07-31 |   6064|        625|     1|      1| 0            | 1             |
|      3|          5| 2015-07-31 |   8314|        821|     1|      1| 0            | 1             |
|      4|          5| 2015-07-31 |  13995|       1498|     1|      1| 0            | 1             |
|      5|          5| 2015-07-31 |   4822|        559|     1|      1| 0            | 1             |
|      6|          5| 2015-07-31 |   5651|        589|     1|      1| 0            | 1             |

### store.csv

``` r
kable(head(dt_store), caption = "First few rows of store.csv")
```

|  Store| StoreType | Assortment |  CompetitionDistance|  CompetitionOpenSinceMonth|  CompetitionOpenSinceYear|  Promo2|  Promo2SinceWeek|  Promo2SinceYear| PromoInterval   |
|------:|:----------|:-----------|--------------------:|--------------------------:|-------------------------:|-------:|----------------:|----------------:|:----------------|
|      1| c         | a          |                 1270|                          9|                      2008|       0|               NA|               NA|                 |
|      2| a         | a          |                  570|                         11|                      2007|       1|               13|             2010| Jan,Apr,Jul,Oct |
|      3| a         | a          |                14130|                         12|                      2006|       1|               14|             2011| Jan,Apr,Jul,Oct |
|      4| c         | c          |                  620|                          9|                      2009|       0|               NA|               NA|                 |
|      5| a         | a          |                29910|                          4|                      2015|       0|               NA|               NA|                 |
|      6| a         | a          |                  310|                         12|                      2013|       0|               NA|               NA|                 |
