[<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/banner.png" width="888" alt="Visit QuantNet">](http://quantlet.de/)

## [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/qloqo.png" alt="Visit QuantNet">](http://quantlet.de/) **MSEex0706** [<img src="https://github.com/QuantLet/Styleguide-and-FAQ/blob/master/pictures/QN2.png" width="60" alt="Visit QuantNet 2.0">](http://quantlet.de/)

```yaml

Name of QuantLet: MSEex0706

Published in: 'Modern Mathematical Statistics : Exercises and Solutions'

Description: 'Plots and illustrates the spectral model and the linear model in this exercise.'

Keywords: 'estimation, spectral, linear, model, linear-model, plot, visualization'

Author: Vladimir Spokoiny, Vladimir Panov, Weining Wang

Submitted: Tue, November 13 2012 by Dedy Dwi Prastyo

Example: Shows the model over time
```

![Picture1](plot.png)

### R Code
```r

A     = 2
B     = 0.5
sigma = 0.8  # variance of the 
y     = numeric(0)

for (t in 1:500) {
    y[t] = A * cos((0.04) * t) + A * sin((0.04) * t) + B * cos((0.5) * t) + B * sin((0.5) * t) + rnorm(1, sd = sigma)
}

T = c(1:500)
plot(T, y, xlab = "Time", ylab = "y(t)", type = "l", col = "blue3", cex.lab = 1.2, cex.axis = 1.2) 

```

automatically created on 2018-05-28