# wintime
[![CRAN Status](https://www.r-pkg.org/badges/version/wintime)](https://CRAN.R-project.org/package=wintime)

An R package that implements the methods proposed in Troendle et al. Use of win time for ordered composite endpoints in clinical trials [Internet]. Stat Med. 2024 May 10 [cited 2025 Apr 30];43(10):1920-1932. Available from: https://pubmed.ncbi.nlm.nih.gov/38417455/. Performs analyses of time-to-event data using various "win time" methods. The functions in this package were written to calculate and compare treatment effects on ordered composite endpoints in clicical trial data. The wintime package can handle censoring and `n` enpoints. It supports calculations on observed and resampled data. 

**CRAN Link:** https://CRAN.R-project.org/package=wintime

Developed by Samuel Lawrence during an internship at the National Institutes of Health (NIH).

## Installation

You can install the current version of wintime from CRAN with:

```R
install.packages("wintime")
```

## Example Usage
```R
# ------ Prepare Data -------

# Event time vectors
TIME_1 <- c(256,44,29,186,29,80,11,380,102,33)
TIME_2 <- c(128,44,95,186,69,66,153,380,117,33)
TIME_3 <- c(435,44,95,186,69,270,1063,380,117,33)

# Event time matrix
Time <- rbind(TIME_1, TIME_2, TIME_3)

# Event indicator vectors
DELTA_1 <- c(1,0,1,0,1,1,1,0,1,0)
DELTA_2 <- c(1,0,0,0,0,1,1,0,0,0)
DELTA_3 <- c(0,0,0,0,0,0,0,0,0,0)

# Event indicator matrix
Delta <- rbind(DELTA_1, DELTA_2, DELTA_3)

# Treatment arm indicator vector
trt <- c(1,1,1,1,1,0,0,0,0,0)

# Covariate vectors
cov1 <- c(66,67,54,68,77,65,55,66,77,54)
cov2 <- c(3,6,4,2,3,5,8,5,3,5)
cov3 <- c(34.6,543.6,45.8,54.7,44.3,55.6,65.9,54.7,77.9,31.2)

# Covariate matrix
cov <- cbind(cov1, cov2, cov3)

# --------- Run main wintime function (with WTR method) ------------
# Run wtr
result <- wintime("wtr", Time, Delta, trt)
print(result)
```

For a more detailed walkthrough, open the wintime_vignette file.
