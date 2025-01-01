---
layout: post
title: "The Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: cutting.jpg
---

The idea of the bootstrap is quite simple. However, as its name suggests, it is a device that at first glance seems to produce something from nothing, like a statistical _perpetuum mobile_, an impression which can be perplexing to one who has only been exposed to the final product and not the reasoning through which it is derived. To dissolve the perplexities of the newly initiated, I will build up the bootstrap from its component parts, beginning with the empirical distribution of the sample. 

## Empirical Distribution

We will begin with a simple case.

Given a sample, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is simply

$$
P[X = x_i] = \frac{\text{Count}(x_{i})}{N} 
$$

In other words, it is a discrete uniform distribution over the sample values (rather than over the natural numbers).

Why should we care about this object? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].

Apart from its status as an MLE, we care about the empirical distribution because, unlike the unknown true distribution, it is a distribution that we can sample from though computational means, opening up to us the world of Monte Carlo estimates.


## Monte Carlo Simulation and Estimation

In probability and statistics, problems often arise that can be easily stated in terms of the outcomes of well-defined data-generating mechanisms but for which a closed-form solution is hard to come by. To take an arbitrary example, we might like to know what the distribution of the ratio of the maximum and minimum of a sample of size $n$ from a standard normal distribution would look like, that is,

$$
\text{If} \hspace{20pt} \boldsymbol{X}_{n} \sim N(\boldsymbol{0}_{n},\boldsymbol{I}_{n\times n})
$$

$$
\text{Then} \hspace{20pt} | max(\boldsymbol{X}_{n})/min(\boldsymbol{X}_{n}) |  \sim \text{  ?}
$$

Though to my knowledge no closed form solution to this problem exists, if we simulate samples from a standard normal and then look at the distribution of the desired ratio, we will have solved the problem for most intents and purposes.

Figure 1 shows a histogram of 10,000 runs of $n = 100$

![Figure 1]({{ site.baseurl }}/assets/img/monte_carlo_ex.jpg)
<figcaption> Figure 1 </figcaption>

[^1]: This is the content of the footnote.

