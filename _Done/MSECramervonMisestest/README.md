[<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/banner.png" width="888" alt="Visit QuantNet">](http://quantlet.de/)

## [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/qloqo.png" alt="Visit QuantNet">](http://quantlet.de/) **MSECramervonMisestest** [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/QN2.png" width="60" alt="Visit QuantNet 2.0">](http://quantlet.de/)

```yaml

Name of QuantLet: MSECramervonMisestest



Published in: 'Modern Mathematical Statistics: Exercise and Solution'

Description: 'Performes a Cramer von Mises normality test on DAX log return data from 2009-12-21 to 2011-12-22'



Keywords: Cramer von Mises test, Testing, test, normal-distribution, normal, normality test




Author: Shih-Kang Chao



Submitted:
 Tue, November 13 2012 by Dedy Dwi Prastyo


Example: 'Performes a Cramer von Mises normality test on DAX log return data from 2009-12-21 to 2011-12-22. Test results reject normality at any common significance level'
```

### R Code
```r

# clear history
rm(list = ls(all = TRUE))
graphics.off()

# install/load packages
libraries = c("foreign", "nortest")
lapply(libraries, function(x) if (!(x %in% installed.packages())) {
    install.packages(x)
})
lapply(libraries, library, quietly = TRUE, character.only = TRUE)

DAX = read.csv("data_DAX091222-111222.csv")
dax1 = DAX[2:(length(DAX[, 7]) - 1), 7]
dax2 = DAX[3:length(DAX[, 7]), 7]
z = log(dax1) - log(dax2)

cvm.test(z) 

```

automatically created on 2018-05-28