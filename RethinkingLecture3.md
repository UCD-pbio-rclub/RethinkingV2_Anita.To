---
title: "RethinkingLecture3_hw"
author: "Anita To"
date: "4/26/2019"
output: 
  html_document:
    keep_md: yes
---

Lecture:
Why does µi have a sub i? (Refer to lecture slides) µi depends on β*xi. So it is kind of like a mean for that particular individual/sample that has some normal disbribution around xi (predictor), therefore µi depends on the individual or sample. Which will all be used to estimate our observed value yi.

# Chapter 4 - Easy Problems

## 4E1.

In the model definition below, which line is the likelihood?
yi ∼ Normal(μ, σ) 
μ ∼ Normal(0, 10) 
σ ∼ Uniform(0, 10)

Answer: yi is the likelihood

## 4E2.

In the model definition just above, how many parameters are in the posterior distribution?

Answer: Two parameters are in the posterior distribution (µ and σ).

## 4E3.
 
Using the model definition above, write down the appropriate form of Bayes’ theorem that
includes the proper likelihood and priors.

Answer: ??? (pg 84)

## 4E4.

In the model definition below, which line is the linear model?
yi ∼ Normal(μ, σ) 
μi =α+βxi
α ∼ Normal(0, 10) 
β ∼ Normal(0, 1)
σ ∼ Uniform(0, 10)

Answer: µi is the linear model.

## 4E5.

In the model definition just above, how many parameters are in the posterior distribution?

Answer: Three -- α, β, and σ.

# Chapter 4 - Medium Problems

## 4M1. 

For the model definition below, simulate observed heights from the prior (not the posterior).
yi ∼ Normal(μ, σ) 
μ ∼ Normal(0, 10) 
σ ∼ Uniform(0, 10)


```r
knitr::opts_chunk$set(echo = TRUE)

library(rethinking)
```

```
## Loading required package: rstan
```

```
## Loading required package: ggplot2
```

```
## Loading required package: StanHeaders
```

```
## rstan (Version 2.18.2, GitRev: 2e1f913d3ca3)
```

```
## For execution on a local, multicore CPU with excess RAM we recommend calling
## options(mc.cores = parallel::detectCores()).
## To avoid recompilation of unchanged Stan programs, we recommend calling
## rstan_options(auto_write = TRUE)
```

```
## Loading required package: parallel
```

```
## rethinking (Version 1.88)
```

```r
sample_mu <- rnorm(1e4, 0, 10)
sample_sigma <- runif(1e4, 0, 10)
prior_y <- rnorm(1e4, sample_mu, sample_sigma)
dens(prior_y)
```

![](RethinkingLecture3_files/figure-html/4M1-1.png)<!-- -->

## 4M2. 

Translate the model just above into a quap formula.


```r
knitr::opts_chunk$set(echo = TRUE)

flist <- alist(
    y ~ dnorm( mu , sigma ),
    mu <- dnorm(0, 10),
    sigma ~ dunif(0, 10)
)
```

## 4M3. 

Translate the quap model formula below into a mathematical model definition. 
flist <- alist(
    y ~ dnorm( mu , sigma ),
    mu <- a + b*x,
    a ~ dnorm( 0 , 50 ),
    b ~ dunif( 0 , 10 ),
    sigma ~ dunif( 0 , 50 )
)

Answer: ("mathematical equations/latex in R Markdown" can recapitulate real math equation fonts)
$$
y_i \sim Normal(µ, σ) \\
µ \sim \alpha + \beta x_i \\
α \sim Normal(0, 50) \\
β \sim Uniform(0, 10) \\ 
σ \sim Uniform(0, 50)
$$
