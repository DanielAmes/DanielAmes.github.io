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
P[X = x_i] = \frac{1}{N} 
$$

In other words, it is a discrete uniform distribution over the sample values (rather than over the natural numbers).

Why should we care about this object? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].

Apart from its status as an MLE, we care about the empirical distribution because, unlike the unknown true distribution, it is a distribution that we can sample from though computational means, opening up to us the world of Monte Carlo estimates.


## Monte Carlo Estimation

[^1]: This is the content of the footnote.

