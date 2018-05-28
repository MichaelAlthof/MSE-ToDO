[<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/banner.png" width="888" alt="Visit QuantNet">](http://quantlet.de/)

## [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/qloqo.png" alt="Visit QuantNet">](http://quantlet.de/) **MSEglmest** [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/QN2.png" width="60" alt="Visit QuantNet 2.0">](http://quantlet.de/)

```yaml

Name of QuantLet: MSEglmest

Published in: 'Modern Mathematical Statistics: Exercises and Solutions'

Description: 'Computes GLM coefficients, standard errors, z- and p-values and gives overall model fit.'

Keywords: logit, regression, GLM, model, financial

Author: Wolfgang K. Haerdle, Weining Wang, Shih Kang Chao

Submitted: Mon, October 04 2010 by Maria Osipenko

Datafile: kredit.csv
```

### R Code
```r

graphics.off()
rm(list = ls(all = TRUE))

install.packages("MASS")
library(MASS)

# setwd('C:/...')

file = read.csv("kredit.csv", sep = ";", dec = ".")  #load credit data

y = 1 - file$kredit  # default set to 1
prev = (file$moral > 2) + 0  # previous loans were OK
employ = (file$beszeit > 1) + 0  # employed (>=1 year)
dura = (file$laufzeit)  # duration
d9.12 = ((file$laufzeit > 9) & (file$laufzeit <= 12)) + 0  #  9 < duration <= 12
d12.18 = ((file$laufzeit > 12) & (file$laufzeit <= 18)) + 0  # 12 < duration <= 18
d18.24 = ((file$laufzeit > 18) & (file$laufzeit <= 24)) + 0  # 18 < duration <= 24
d24 = (file$laufzeit > 24) + 0  # 24 < duration
amount = file$hoehe  # amount of loan
age = file$alter  # age of applicant
savings = (file$sparkont > 4) + 0  # savings >= 1000 DM
phone = (file$telef == 1) + 0  # applicant has telephone
foreign = (file$gastarb == 1) + 0  # non-german citizen
purpose = ((file$verw == 1) | (file$verw == 2)) + 0  # loan is for a car
house = (file$verm == 4) + 0  # house owner

# Logit: dependence on several rating factors (with model choice)
g11 = glm(y ~ age + amount + prev + d9.12 + d12.18 + d18.24 + d24 + savings + purpose + house, family = binomial)
summary(g11)

# model choice
s11 = stepAIC(g11)
s11$anova
summary(s11)

# show est. PDs
s11$null.deviance - s11$deviance
s11$df.null - s11$df.residual
dchisq(s11$null.deviance - s11$deviance, s11$df.null - s11$df.residual) 

```

automatically created on 2018-05-28