---
layout: post
title: "The Bootstrap"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: cutting.jpg
---

The idea of the bootstrap is quite simple. It is the estimation of quantities of interest via Monte Carlo estimates from the empirical distribution.

## Empirical Distribution

We will begin with a simple case.

Given a sample of size _N_, $$x_{1},\cdots,x_{N} \in \mathbb{R}$$, the empirical distribution is

$$
P[X = x_i] = \frac{1}{N} \hspace{10pt}
$$

In other words, it is a discrete uniform distribution over the sample values (rather than over the natural numbers).

Why should we care about this entity? The most obvious reason is that in a strict sense it is our _best guess_ of the true distribution if we greatly limit our assumptions about that distribution. In particular, if our only assumptions about the sample is that it is I.I.D., then the empirical distribution is the maximum likelihood estimate (MLE) of the true distribution[^1].
 To see why this is so, consider the likelihood function of the distribution function

## Empirical Distribution as Maximum Likelihood Distribution
We can think of the empirical distribution as the maximum likelihood estimate of the data-generating distribution when we relax our.




Let's say we have the following  sample of 5 numerical values, [1, 5, 3.5, 0, 0.1], and we want to know how confident we can be that the mean is representative of the population mean. Usually, we would depend upon distributional assumptions or the central limit theorem to produce an estimate of this kind, but if we want our estimate to be robust, we must loosen our assumptions as far as possible. One way to do this is to first estimate the true distribution from which the sample has been drawn. 
If we only maintain the assumptions of independent and identically distributed samples, then the maximum likelihood estimate of the c

 Although the empirical distribution is with good reason defined in terms of a cumulative distribution function, the _idea_ of the empirical distribution is much clearer when presented in the guise of a probability distribution function.


 them *italicized*, using *astericks* or _underscores_, or making them **bold**, using **double astericks** or __double underscores__. Of course, you can combine those two formats, with both _**bold and italicized**_ text, using any combination of the above syntax. You can also add a strikethrough to text using a ~~double tilde~~.

## Monte Carlo Estimator


[^1]: This is the content of the footnote.

