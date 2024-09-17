Problem 2
================
Zicheng Wang
2024-09-16

Load necessary packages:

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

Create a data frame:

``` r
df <- tibble(
  sample_normal = rnorm(10, mean = 0, sd = 1),
  sample_logic = sample_normal > 0,
  sample_char = sample(letters, 10),
  sample_level = factor(sample(c("Level1", "Level2", "Level3"), 10, replace = TRUE))
)
```

Display the data frame to inspect:

``` r
print(df)
```

    ## # A tibble: 10 × 4
    ##    sample_normal sample_logic sample_char sample_level
    ##            <dbl> <lgl>        <chr>       <fct>       
    ##  1        -0.287 FALSE        o           Level2      
    ##  2        -0.761 FALSE        z           Level1      
    ##  3         0.782 TRUE         p           Level2      
    ##  4         0.635 TRUE         q           Level1      
    ##  5        -0.242 FALSE        s           Level2      
    ##  6        -0.500 FALSE        i           Level1      
    ##  7        -0.137 FALSE        b           Level1      
    ##  8        -0.564 FALSE        m           Level2      
    ##  9        -0.285 FALSE        j           Level3      
    ## 10         0.965 TRUE         c           Level2

Calculate means of each variable in the data frame:

``` r
mean(df %>% pull(sample_normal))
```

    ## [1] -0.03925313

``` r
mean(df %>% pull(sample_logic))
```

    ## [1] 0.3

``` r
mean(df %>% pull(sample_char))
```

    ## Warning in mean.default(df %>% pull(sample_char)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(df %>% pull(sample_level))
```

    ## Warning in mean.default(df %>% pull(sample_level)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

Change those type of variables that cannot calculate mean into numeric
type:

``` r
df$sample_logic <- as.numeric(df$sample_logic)
df$sample_char <- as.numeric(df$sample_char)
df$sample_level <- as.numeric(df$sample_level)
```

First two lines returned following message:
`Warning: NAs introduced by coercion`, the last line performed without
warnings.
