---
layout: post
title: "Notes on the Foundations of the Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
hide_related_posts: true
---

The idea of the bootstrap is quite simple. However, as its name suggests, it is a device that at first glance seems to produce something from nothing, like a statistical _perpetuum mobile_. To dissolve my own perplexities concerning this matter, I compiled the following notes upon the foundations of the bootstrap.

## Empirical Distribution

We will begin with the one-sample case.

Given a sample, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is simply

$$
P[X = x_i] = \frac{\text{Count}(x_{i})}{N} 
$$

Why should we care about this object? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumption about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].

## Ideal Bootstrap Estimate

These are the estimates of inferential quantities of interest (standard errors, confidence intervals, etc.) obtained by evaluating a statistic (in the sense of the function of a sample) across all possible samples of a certain size from the empirical distribution.


As the sample size increases, however, such an exhaustive approach becomes computationally infeasible: the number of bootstrap samples to be evaluated for an original sample size of $n$ is $\binom{2n-1}{n}$, which asymptotically is $4^n / \sqrt{n\pi}$.[^2]


We overcome this computational constraint by approximating the ideal bootstrap estimate using Monte Carlo methods.


## Review of Monte Carlo Simulation and Estimation

In probability and statistics, problems often arise that can be easily stated in terms of the outcomes of well-defined data-generating mechanisms but for which a closed-form solution is hard to come by. To take an arbitrary example of some complexity, we might want to investigate the distribution of the ratio of the max and min of a sample of size $n$ from a standard Guassian, that is,

$$
\text{If} \hspace{15pt} \boldsymbol{X}_{n} \sim N(\boldsymbol{0}_{n},\boldsymbol{I}_{n\times n})
$$

$$
\text{Then} \hspace{15pt} | \text{max}(\boldsymbol{X}_{n})/\text{min}(\boldsymbol{X}_{n}) |  \sim \text{  ?}
$$

Though to my knowledge no closed-form solution to this problem exists, if we simulate samples from a standard normal and then look at the distribution of the desired ratio, we will have solved the problem for most practical intents and purposes.

Below is displayed a histogram of 10,000 runs of $n = 100$; its shape suggests a log-normal distribution.

![Figure 1]({{ site.baseurl }}/assets/img/monte_carlo_ex.jpg)

In this example, we can see the two ingredients of an important class of Monte Carlo simulations:

1. A well-defined distribution from which we can simulate samples with a random number generator.

2. A statistic whose distribution we want to know (that is, a function of the sample).

In its most rudimentary form, **the bootstrap is nothing but the application of this kind of Monte Carlo simulation to a function of the empirical distribution of a sample**. 

But the beauty and simplicity of the bootstrap lies in the fact that we can choose extremely complex functions of the empirical distrbution without adding complications to the bootstrap procedure.

## Failure Cases

The bootstrap is not the panacea of inferential statistics that it at first may seem. 

## Code
```R
library(ggplot2)


norm_max_min_sim <- function(samp_size, num_of_runs){
  samp_mat <- matrix(rnorm(n = samp_size*num_of_runs), nrow = num_of_runs)
  samp_max <- apply(samp_mat, 1, max)
  samp_min <- apply(samp_mat, 1, min)
  samp_ratio <- abs(samp_max/samp_min)
  samp_df <- data.frame('ratio' = samp_ratio)
  return(samp_df)
}


ex_1 <- norm_max_min_sim(100, 10000)


ggplot(ex_1, aes(x = ratio)) +
  geom_histogram(fill = "skyblue", color = "black") +
  theme_minimal()
```
## Sources
* _An Introduction to the Bootstrap_ by Efron and Tibshirani
* _All of Nonparametric Statistics_ by Wasserman

## Footnotes
[^1]: Incidentally, in the case of finite support, this result is equivalent to the fact that of all rectangles of a fixed perimeter, the square is the figure with the greatest area.

[^2]: To see where this binomial coefficient comes from, imagine you are iterating through the original sample arranged in an arbitrary order. You begin with the first value, $x_1$, and you have two choices: you either include an instance of $x_1$ in the bootstrap sample or you move on to $x_2$. This algorithm will necessarily terminate after $2n-1$ steps because it takes that many steps to both produce the desired sample size ($n$ steps) and iterate through all of the values ($n-1$ steps), and for each bootstrap sample, $n$ of those steps must be the action of the inclusion of a value. The binomial coefficient $\binom{2n-1}{n}$, then, is the number of ways to select $n$ inclusion steps out of $2n-1$ total steps.


