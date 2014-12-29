tableone (developmental repo)
===============================================================================

**An R package to create "Table 1", description of baseline characteristics**

This package creates "Table 1", i.e., description of baseline patient characteristics, which is essential every medical research. This package provides functions to create such summaries for continuous and categorical variables, optionally with subgroup comparisons. The package was inspired by and based on descriptive statistics functions in Deducer, a Java-based GUI package by Ian Fellows. This package does not require GUI or Java, and intended for command-line users.


tableone in action
-------------------------------------------------------------------------------

![screencast](tableone.gif "screencast")

The code being executed can be found in the introduction vignette.

A higher quality version is available at YouTube: https://www.youtube.com/watch?v=IZgDKmOC0Wg&feature=youtu.be


Table 1 in three lines
-------------------------------------------------------------------------------

In this table, continuous and categorical variables can be ordered however you like. The p-valeus are from exact tests for pre-specified variables. For nonnormal variables, it shows median and IQR instead of mean and SD, and p-values are from nonparametric tests.

```
> tableOne <- CreateTableOne(vars = vars, strata = "trt", data = pbc)
> print(tableOne, nonnormal = c("bili","chol","copper","alk.phos","trig"),
+       exact = c("status","stage"), cramVars = "sex")

                          Stratified by trt
                          1                         2                         p      test
  n                       158                       154
  time (mean (sd))        2015.62 (1094.12)         1996.86 (1155.93)          0.883
  status (%)                                                                   0.884 exact
     0                         83 (52.5)                 85 (55.2)
     1                         10 ( 6.3)                  9 ( 5.8)
     2                         65 (41.1)                 60 (39.0)
  age (mean (sd))           51.42 (11.01)             48.58 (9.96)             0.018
  sex = m/f (%)            21/137 (13.3/86.7)        15/139 (9.7/90.3)         0.421
  ascites = 1 (%)              14 (8.9)                  10 (6.5)              0.567
  hepato = 1 (%)               73 (46.2)                 87 (56.5)             0.088
  spiders = 1 (%)              45 (28.5)                 45 (29.2)             0.985
  edema (%)                                                                    0.877
     0                        132 (83.5)                131 (85.1)
     0.5                       16 (10.1)                 13 ( 8.4)
     1                         10 ( 6.3)                 10 ( 6.5)
  bili (median [IQR])        1.40 [0.80, 3.20]         1.30 [0.72, 3.60]       0.842 nonnorm
  chol (median [IQR])      315.50 [247.75, 417.00]   303.50 [254.25, 377.00]   0.544 nonnorm
  albumin (mean (sd))        3.52 (0.44)               3.52 (0.40)             0.874
  copper (median [IQR])     73.00 [40.00, 121.00]     73.00 [43.00, 139.00]    0.717 nonnorm
  alk.phos (median [IQR]) 1214.50 [840.75, 2028.00] 1283.00 [922.50, 1949.75]  0.812 nonnorm
  ast (mean (sd))          120.21 (54.52)            124.97 (58.93)            0.460
  trig (median [IQR])      106.00 [84.50, 146.00]    113.00 [84.50, 155.00]    0.370 nonnorm
  platelet (mean (sd))     258.75 (100.32)           265.20 (90.73)            0.555
  protime (mean (sd))       10.65 (0.85)              10.80 (1.14)             0.197
  stage (%)                                                                    0.205 exact
     1                         12 ( 7.6)                  4 ( 2.6)
     2                         35 (22.2)                 32 (20.8)
     3                         56 (35.4)                 64 (41.6)
     4                         55 (34.8)                 54 (35.1)
```


Installation
-------------------------------------------------------------------------------

This version of tableone package for R is developmetal, and is not available from the CRAN. You can install it using one of the following way.

**Direct installation from github**

You first need to install the devtools package to do the following. You can choose from the latest stable version and the latest development version.
```
## Install devtools (if you do not have it already)
> install.packages("devtools")
## Load devtools
> library(devtools)
## Install directly from github (develop branch)
> install_github(repo = "kaz-yos/tableone", ref = "develop")
```

Using devtools requires some preparation, please see the following link for information.

http://www.rstudio.com/projects/devtools/
