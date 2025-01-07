---
layout: post
title: "Global Patterns of Grain Yield vs. Fertilizer Use"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: #wheatstock.jpg
hide_related_posts: true
---

On the scale of a single plant, it is well known that the application of mineral fertilizers improves plant growth but that it is subject to diminishing returns, and beyond a saturation point, a marginal increase in fertilizer will no longer have any effect upon plant growth.

Thus, in an experiment where the amount of fertilizer is made to vary across subjects, we expect the curve of plant growth as a function of fertilizer to be increasing but also to exhibit an asymptote. An example of what such experimental results look like for phosphorus fertilizer can be seen below (adapted from Alley and Vanlauwe, 2009).

![Figure 1]({{ site.baseurl }}/assets/img/Phosphorus.png)

In this paper, we investigate whether the same effect is visible on a global scale, where each country's grain yield for a given year is represented as a single data point, or whether on the contrary, other determinants of differences in yield between countries overshadow the effect of fertilizer at scale. 

Furthermore, we look at the trajectories of certain countries along the fertilizer saturation curve over time. The focus, however, is not upon time series analysis.

To simplify the analysis, we will restrict our attention to grain crops because (1) most countries produce significant quantities of at least one grain crop, (2) yields across different grain crops are highly correlated with one another, and (3) grain crops account for more than half of all calories consumed in the world and are therefore of extreme practical importance.

## Data

The grain yield data comes from [Our World in Data](https://ourworldindata.org/crop-yields), and the fertilizer usage data comes from [The World Bank](https://data.worldbank.org/indicator/AG.CON.FERT.PT.ZS).

We begin by considering the data for a single year single year, 2020, because that is the most recent year for which complete data is available. Later, we extend our analysis backwards in time.

## Exploratory Visualization

Below is the scatterplot of grain yield in metric tons produced per hectare against fertilizer in kilograms applied per hectare. Two aspects of the plot attracted our notice:

1. At low levels of fertilizer use, the two variables have a strong positive correlation; at high levels, they have no correlation.

2. The variance in yield grows with fertilizer usage.

The first of these patterns is consistent with the observations we made in the introduction concerning the fertilizer curve of a single organism and suggests that at low levels of fertilizer use, differences in fertilizer use have high explanatory power.

The second pattern may be due to the fact that reaching the highest attainable yield is impossible without the use of large quantities of fertilizer, whereas it is possible to use much fertilizer while still failing to achieve high yields, so that among countries who have neared the fertilizer saturation point, differences in factors like climate, soil quality, crop varieties, agricultural expenditure, and agricultural technology have come to dominate differences in fertilizer use and therefore have greater power to explain differences in yield.

![Figure 3]({{ site.baseurl }}/assets/img/FertilizerYieldScatter.png)

Rather than explicitly modeling the relationship between the variables as a non-linear curve with an asymptote, we opted to transform the explanatory variable, fertilizer, in order to linearize the relationship. Of all such transformations, a logistic transformation (sometimes called a sigmoid transformation) seemed most appropriate in light of the patterns observed in the scatterplot. 

## Logistic Transformation of Fertilizer Variable

## Grid Search for Logistic Parameter

## Clustering Analysis

## Reverse Causality

## Sources

## Footnotes


