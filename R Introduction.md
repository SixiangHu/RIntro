R Introduction
========================================================
author: Sixiang Hu
date: 30th Nov, 2014
width: 1280
height: 1024
autosize: true

What is R?
========================================================
- The R statistical programming language is a free open source package based on - the S language developed by Bell Labs. 
- Many statistical functions are already built in.
Contributed packages expand the functionality to cutting edge research.
- Free


Getting Started
========================================================
* Download R 3.1.2 (Pumpkin Helmet):
  + http://cran.r-project.org/

* Download RStudio (Optional):
  + http://www.rstudio.com/products/rstudio/download/
  + To get a beautiful user interface
  + Easier maintains

Basic Assignment and Operations
========================================================
* Arithmetic Operations:

```r
1+2*exp(3)/sin(4)
```

```
[1] -52.08
```

* Assignment:

```r
a <- runif(4)
a
```

```
[1] 0.1926935 0.1130957 0.7909896 0.3856126
```

* Use help in R:

```r
?sin
```

Variables in R
========================================================
There are several types of variables can be used in R:
integer, numerical, character, date, vector, matrix, list, 
and data frame.


```r
a <- sample(LETTERS,5,replace=T)
a
```

```
[1] "P" "C" "E" "Y" "L"
```

```r
class(a)
```

```
[1] "character"
```

```r
class(data.frame(c(a=a,b=a)))
```

```
[1] "data.frame"
```

Data Frame
========================================================
Data frame is the widest used data type used in R.
It can have different type of value in different columns, but 
values in a column must keep the same.


```r
a <- c(1,2,3)
b <- c("a","b","c")
df <- data.frame(a=a,b=b)
df
```

```
  a b
1 1 a
2 2 b
3 3 c
```

```r
df$a
```

```
[1] 1 2 3
```

```r
df[2,2]
```

```
[1] b
Levels: a b c
```

List
========================================================
List can be used to store different types of variables with 
differnet length.


```r
a <- c(1,2,3)
b <- c("a","b","c")
lt <- list(a,b)
lt
```

```
[[1]]
[1] 1 2 3

[[2]]
[1] "a" "b" "c"
```

```r
lt[[2]]
```

```
[1] "a" "b" "c"
```

Function
========================================================
We can create functions that can be used repetitely:

```r
my_square <- function(x) {x*x}
my_square(5)
```

```
[1] 25
```

Plot
========================================================

```r
par(mfrow=c(2,2))
plot(cars,type="l")
hist(cars$speed)
plot(cars)
hist(cars$dist)
```

<img src="R Introduction-figure/unnamed-chunk-8-1.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" width="750px" />

Modelling
========================================================

```r
 model1 <- glm(mpg~gear+cyl,data=mtcars,family=Gamma)
summary(model1)
```

```

Call:
glm(formula = mpg ~ gear + cyl, family = Gamma, data = mtcars)

Deviance Residuals: 
     Min        1Q    Median        3Q       Max  
-0.34679  -0.08718  -0.01579   0.08210   0.25549  

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  0.0186841  0.0115534   1.617    0.117    
gear        -0.0020063  0.0021761  -0.922    0.364    
cyl          0.0067352  0.0008912   7.558 2.48e-08 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

(Dispersion parameter for Gamma family taken to be 0.02356935)

    Null deviance: 2.73529  on 31  degrees of freedom
Residual deviance: 0.70551  on 29  degrees of freedom
AIC: 166.14

Number of Fisher Scoring iterations: 4
```

We can use different family and link function for GLM 
modeling.  Interactions, offset, splines and transformation 
are all can be done within R.

For some large dataset (>100MB), it will be slow for a fit.
Some packages `bigGLM` can be used to accelarate to process.

Advanced Plot (ggplot2)
========================================================

```r
library(ggplot2)
library(ggthemes)
ggplot(data = msleep, aes(x = log(bodywt), y = sleep_total)) +
  geom_point(aes(shape=vore), size=3)+
  theme_wsj()
```

<img src="R Introduction-figure/unnamed-chunk-10-1.png" title="plot of chunk unnamed-chunk-10" alt="plot of chunk unnamed-chunk-10" width="750px" />

Further Online Tutorial
========================================================
* R Tutorial (Statistics)
  + http://www.r-tutor.com/

* CRAN R Tutorial
  + http://cran.r-project.org/doc/manuals/r-release/R-intro.html

* Data Camp R
  + https://www.datacamp.com/
  
* Kaggle
  + https://www.kaggle.com/
