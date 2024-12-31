---
layout: post
title: "The Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: cutting.jpg
---

The idea of the bootstrap is quite simple. However, as its name suggests, the bootstrap does at first glance seem to produce something from nothing, like a statistical _perpetuum mobile_, which can be perplexing to one who has only been exposed to the final product and not the reasoning through which it is derived. To dissolve that perplexity, I will build up the bootstrap from its component parts, beginning with the empirical distribution of the sample.

## Empirical Distribution

We will begin with a simple case.

Given a sample, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is

$$
P[X = x_i] = \frac{1}{N} 
$$

In other words, it is a discrete uniform distribution over the sample values (rather than over the natural numbers).

Why should we care about this object? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].

Apart from its status as an MLE and for the specific purpose of the bootstrap, we care about the empirical distribution because it is a distribution that we can sample from by computational means


 To see why this is so, consider the likelihood function of the distribution function

## Empirical Distribution as Maximum Likelihood Distribution
We can think of the empirical distribution as the maximum likelihood estimate of the data-generating distribution when we relax our.




Let's say we have the following  sample of 5 numerical values, [1, 5, 3.5, 0, 0.1], and we want to know how confident we can be that the mean is representative of the population mean. Usually, we would depend upon distributional assumptions or the central limit theorem to produce an estimate of this kind, but if we want our estimate to be robust, we must loosen our assumptions as far as possible. One way to do this is to first estimate the true distribution from which the sample has been drawn. 
If we only maintain the assumptions of independent and identically distributed samples, then the maximum likelihood estimate of the.

[^1]: This is the content of the footnote.

