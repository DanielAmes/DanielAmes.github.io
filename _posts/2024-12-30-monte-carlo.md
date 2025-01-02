---
layout: post
title: "The Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: 
---

The idea of the bootstrap is quite simple. However, as its name suggests, it is a device that at first glance seems to produce something from nothing, as if it were a statistical _perpetuum mobile_, an impression which can be perplexing to one who has only been exposed to the final product and not the reasoning through which it is derived. To dissolve the perplexities of the newly initiated, I will build up the bootstrap from its component parts, beginning with the empirical distribution of the sample. 

## Empirical Distribution

We will begin with a simple case.

Given a sample, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is simply

$$
P[X = x_i] = \frac{\text{Count}(x_{i})}{N} 
$$

Why should we care about this object? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].

Apart from its status as an MLE, we care about the empirical distribution because, unlike the unknown true distribution, it is a distribution that we can sample from though computational means, opening up to us the world of Monte Carlo simulation.


## Monte Carlo Simulation

In probability and statistics, problems often arise that can be easily stated in terms of the outcomes of well-defined data-generating mechanisms but for which a closed-form solution is hard to come by. To take an arbitrary example of some complexity, we might want to investigate the distribution of the ratio of the max and min of a sample of size $n$ from a standard Guassian, that is,

$$
\text{If} \hspace{15pt} \boldsymbol{X}_{n} \sim N(\boldsymbol{0}_{n},\boldsymbol{I}_{n\times n})
$$

$$
\text{Then} \hspace{15pt} | \text{max}(\boldsymbol{X}_{n})/\text{min}(\boldsymbol{X}_{n}) |  \sim \text{  ?}
$$

Though to my knowledge no closed form solution to this problem exists, if we simulate samples from a standard normal and then look at the distribution of the desired ratio, we will have solved the problem for most practical intents and purposes.

Below is displayed a histogram of 10,000 runs of $n = 100$.

![Figure 1]({{ site.baseurl }}/assets/img/monte_carlo_ex.jpg)

In this example, we can see the two ingredients of an important class of Monte Carlo simulations:

1. A well-defined distribution from which we can simulate samples with a random number generator.

2. A statistic whose distribution we want to know (that is, a function of the sample).

In its most rudimentary form, the bootstrap is nothing but the application of this kind of Monte Carlo simulation to the empirical distribution of a sample.


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

## Footnotes
[^1]: In the case of finite support, this result is equivalent to the fact that of all rectangles of a fixed perimeter, the square is the figure with the greatest area.



