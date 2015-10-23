<!-- README.md is generated from README.Rmd. Please edit that file -->
EEM
===

All functions start with `eem_`.

``` r
library(eem)

fluo <- "/home/persican/Desktop/test/eem/"

b <- "/home/persican/Desktop/test/nano.csv"

ex <- seq(220, 450, by = 5)
em <- seq(230, 600, by = 2)

eem1 <- eem_read(fluo, ex, em)
blank <- eem_read(b, ex, em)

## Test remove scattering
eem2 <- eem_remove_scattering(eem = eem1, type = "raman", order = 1, width = 10)
eem2 <- eem_remove_scattering(eem = eem2, type = "rayleigh", order = 1, width = 10)

plot(eem1[[1]])
plot(eem2[[1]])

## Test blank removal
eem3 <- eem_remove_blank(eem2, blank)

plot(eem3[[1]])

## Test raman normalisation
eem4 <- eem_raman_normalisation(eem3, blank)

plot(eem4[[1]])


## Test metrics
eem_fluorescence_index(eem4)
eem_coble_peaks(eem1)
```
