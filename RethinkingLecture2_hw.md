---
title: "RethinkingLecture2_hw"
author: "Anita To"
date: "4/12/2019"
output: 
  html_document:
    keep_md: yes
---

# Chapter 2 - Easy Problems

## 2E1.

Which of the expressions below correspond to the statement: the probability of rain on Monday?

(1) Pr(rain)
(2) Pr(rain|Monday)
(3) Pr(Monday|rain)
(4) Pr(rain,Monday)/Pr(Monday)

Answer: (2) Pr(rain|Monday) AND (4) Pr(rain,Monday)/Pr(Monday)

## 2E2.

Which of the following statements corresponds to the expression: Pr(Monday|rain)?

(1) The probability of rain on Monday.
(2) The probability of rain, given that it is Monday.
(3) The probability that it is Monday, given that it is raining.
(4) The probability that it is Monday and that it is raining.

Answer: (3) The probability that it is Monday, given that it is raining. and sort of (4), but you have to divide it by Pr(rain)

## 2E3.
 
Which of the expressions below correspond to the statement: the probability that it is Monday,
given that it is raining?

(1) Pr(Monday|rain)
(2) Pr(rain|Monday)
(3) Pr(rain|Monday)Pr(Monday)
(4) Pr(rain|Monday)Pr(Monday)/Pr(rain)
(5) Pr(Monday|rain)Pr(rain)/Pr(Monday)

Answer: (2) Pr(rain|Monday)

# Chapter 2 - Medium Problems

## 2M1. 

Recall the globe tossing model from the chapter. Compute and plot the grid approximate posterior distribution for each of the following sets of observations. In each case, assume a uniform prior for p.
### (1) W,W,W


### ((2) W,W,W,L


### ((3) L,W,W,L,W,W,W


## 2M2. 

Now assume a prior for p that is equal to zero when p < 0.5 and is a positive constant when p ≥ 0.5. Again compute and plot the grid approximate posterior distribution for each of the sets of observations in the problem just above.



## 2M3. 

Suppose there are two globes, one for Earth and one for Mars. The Earth globe is 70% covered in water. The Mars globe is 100% land. Further suppose that one of these globes—you don’t know which—was tossed in the air and produced a “land” observation. Assume that each globe was equally likely to be tossed. Show that the posterior probability that the globe was the Earth, conditional on seeing “land” (Pr(Earth|land)), is 0.23.



## 2M4. 

Suppose you have a deck with only three cards. Each card has two sides, and each side is either black or white. One card has two black sides. The second card has one black and one white side. The third card has two white sides. Now suppose all three cards are placed in a bag and shuffled. Someone reaches into the bag and pulls out a card and places it flat on a table. A black side is shown facing up, but you don’t know the color of the side facing down. Show that the probability that the other side is also black is 2/3. Use the counting method (Section 2 of the chapter) to approach this problem. This means counting up the ways that each card could produce the observed data (a black side facing up on the table).



## 2M5. 

Now suppose there are four cards: B/B, B/W, W/W, and another B/B. Again suppose a card is drawn from the bag and a black side appears face up. Again calculate the probability that the other side is black.



# Chapter 3 - Easy Problems

These problems use the samples from the posterior distribution for the globe tossing example. This code will give you a specific set of samples, so that you can check your answers exactly.


```r
p_grid <- seq( from=0 , to=1 , length.out=1000 )
prior <- rep( 1 , 1000 )
likelihood <- dbinom( 6 , size=9 , prob=p_grid )
posterior <- likelihood * prior
posterior <- posterior / sum(posterior)
set.seed(100)
samples <- sample( p_grid , prob=posterior , size=1e4 , replace=TRUE )
```

Use the values in samples to answer the questions that follow.

## 3E1. 
How much posterior probability lies below p = 0.2?

```r
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
# dens(samples)
sum(posterior[p_grid < 0.2])
```

```
## [1] 0.0008560951
```

```r
sum(samples < 0.2)/1e4
```

```
## [1] 5e-04
```

## 3E2. 
How much posterior probability lies above p = 0.8?

```r
sum(posterior[p_grid > 0.8])
```

```
## [1] 0.1203449
```

```r
sum(samples > 0.8)/1e4
```

```
## [1] 0.1117
```

## 3E3. 
How much posterior probability lies between p = 0.2 and p = 0.8?

```r
sum(posterior[p_grid > 0.2 & p_grid < 0.8])
```

```
## [1] 0.878799
```

```r
sum(samples > 0.2 & samples < 0.8)/1e4
```

```
## [1] 0.8878
```

## 3E4. 
20% of the posterior probability lies below which value of p?

```r
quantile(samples, 0.2)
```

```
##       20% 
## 0.5195195
```

## 3E5. 
20% of the posterior probability lies above which value of p?

```r
quantile(samples, 1) - quantile(samples, 0.8)
```

```
##      100% 
## 0.2202202
```

## 3E6. 
Which values of p contain the narrowest interval equal to 66% of the posterior probability?

```r
HPDI(samples, prob = 0.66)
```

```
##     |0.66     0.66| 
## 0.5205205 0.7847848
```

## 3E7. 
Which values of p contain 66% of the posterior probability, assuming equal posterior probabil      ity both below and above the interval?

```r
knitr::opts_chunk$set(echo = TRUE)
```

# Chapter 3 - Medium Problems

## 3M1. 
Suppose the globe tossing data had turned out to be 8 water in 15 tosses. Construct the poste-
rior distribution, using grid approximation. Use the same flat prior as before.

```r
p_grid <- seq( from=0 , to=1 , length.out=1000 )
prior <- rep( 1 , 1000 )
likelihood <- dbinom(  8, size=15 , prob=p_grid )
posterior <- likelihood * prior
posterior <- posterior / sum(posterior)
set.seed(100)
samples <- sample( p_grid , prob=posterior , size=1e4 , replace=TRUE )
dens(samples)
```

![](RethinkingLecture2_hw_files/figure-html/3M1-1.png)<!-- -->

## 3M2. 
Draw 10,000 samples from the grid approximation from above. Then use the samples to cal-
culate the 90% HPDI for p.

```r
HPDI(samples, prob = 0.9)
```

```
##      |0.9      0.9| 
## 0.3243243 0.7157157
```

## 3M3. 
Construct a posterior predictive check for this model and data. This means simulate the distribution of samples, averaging over the posterior uncertainty in p. What is the probability of observing 8 water in 15 tosses?

```r
knitr::opts_chunk$set(echo = TRUE)
```

## 3M4. 
Using the posterior distribution constructed from the new (8/15) data, now calculate the probability of observing 6 water in 9 tosses.

```r
knitr::opts_chunk$set(echo = TRUE)
```
