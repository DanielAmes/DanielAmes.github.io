---
layout: post
title: "Global Patterns of Grain Yield vs. Fertilizer Use"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: wheatstock.jpg
hide_related_posts: true
---
## Background
On the scale of a single plant, it is well known that the application of mineral fertilizers improves plant growth but that it is subject to diminishing returns and beyond a certain point of fertilizer saturation in the soil, a marginal increase in fertilizer will no longer produce a merginal increase in plant growth.
Thus, in an experiment where the amount of fertilizer is made to vary across subjects, we expect the curve of plant growth as a function of fertilizer to be increasing but also to exhibit an asymptote. An example of what such experimental results look like for phosphorus fertilizer can be seen below (adapted from Alley and Vanlauwe, 2009).

![Figure 1]({{ site.baseurl }}/assets/img/Phosphorus.png)

We want to know whether the same effect is visible on a global scale, where each country's grain yield for a given year is represented as a single data point, or whether on the contrary, other determinants of differences in yield between countries overshadow the effect of fertilizer at scale. 

To simplify the analysis, we will restrict our attention to grain crops because (1) most countries produce significant quantities of at least one grain crop, (2) yields across different grain crops are highly correlated with one another[^1], and (3) grain crops account for more than half of all calories consumed in the world and are therefore of extreme practical importance.

## Background

We begin by considering the data for a single year single year, 2020, because that is the most recent year for which complete data is available.
## Logistic Transformation

## Grid Search for Logistic Parameter

## Reverse Causality

## Footnotes
[^1]: The high mutual correlation between the yields of different grains can be seen in the first principal component of the yield figures for the year 2022:

\begin{verbatim}
Loadings:
              Comp.1 Comp.2 Comp.3 Comp.4 Comp.5 Comp.6 Comp.7 Comp.8
wheat_yield    0.350  0.303  0.639                       0.150  0.591
maize_yield    0.333 -0.610  0.163 -0.108 -0.618  0.294              
barley_yield   0.371  0.399        -0.109  0.105  0.349  0.515 -0.540
rice_yield     0.337 -0.469  0.126 -0.393  0.688 -0.128              
sorghum_yield  0.348        -0.735                0.138  0.149  0.541
rye_yield      0.368  0.158        -0.160 -0.314 -0.829        -0.148
millet_yield   0.340 -0.196         0.888  0.184 -0.105        -0.113
oats_yield     0.378
\end{verbatim}

