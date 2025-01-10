---
layout: post
title: "Project: Global Patterns of Grain Yield vs. Fertilizer Use"
author: "Daniel Ames"
categories: journal
tags: [documentation,sample]
image: #wheatstock.jpg
---
On the scale of a single plant, it is well known that the application of mineral fertilizers improves plant growth but that it is a practice subject to diminishing returns, and beyond a saturation point, a marginal increase in fertilizer will no longer have any effect upon plant growth.

Thus, in an experiment where the amount of fertilizer is made to vary across subjects, we expect the curve of plant growth as a function of fertilizer to be increasing but also to exhibit an asymptote. An example of what such experimental results look like for phosphorus fertilizer can be seen below (adapted from Alley and Vanlauwe, 2009).

![Figure 1]({{ site.baseurl }}/assets/img/Phosphorus.png)

We investigated whether the same effect is visible on a global scale, where each country's grain yield for a given year is represented as a single data point, or whether on the contrary, other determinants of differences in yield between countries overshadow the effect of fertilizer at scale. 

Furthermore, we looked at the trajectories of certain countries along the fertilizer saturation curve over time.

To simplify the analysis, we restricted our attention to grain crops because (1) most countries produce significant quantities of at least one grain crop, (2) yields across different grain crops are highly correlated with one another, and (3) grain crops account for more than half of all calories consumed in the world and are therefore of extreme practical importance.

## Data

The grain yield data comes from [Our World in Data](https://ourworldindata.org/crop-yields), and the fertilizer usage data comes from [The World Bank](https://data.worldbank.org/indicator/AG.CON.FERT.ZS). 

The main weakness of the fertilizer data is that it is not specific to grain crops, nor are distinctions made between nitrogen, phosphorus, and potassium fertilizers. We reasoned that it would nevertheless serve as an approximation of the level of fertilizer applied to grains because in most countries grains account for around a third of total agricultural production.

We began by considering the data from 2019, because that is the most recent year for which complete data is available.

## Exploratory Visualization
To get an idea of how grain yields and fertilizer usage each vary across the globe, we created maps of the two variables with the R package _rworldmap_:

![Map A]({{ site.baseurl }}/assets/img/yieldmap2019bold.png)

![Map B]({{ site.baseurl }}/assets/img/fertilizermap2019bold.png)


It can immediately be seen that much of the variation in the plots is between geopolitical regions rather than between ecological or climatic regions. So, for example, most countries in Western Europe have high grain yields, and most of Africa (excepting Egypt) has low levels of fertilizer usage.

Below is the scatter plot of grain yield in metric tons produced per hectare against fertilizer in kilograms applied per hectare. 

![Figure 4]({{ site.baseurl }}/assets/img/scatter2019.png)

Two aspects of the plot attracted our notice:

1. At low levels of fertilizer use, the two variables have a strong positive correlation; at high levels, they have no correlation.

2. The variance in yield grows with fertilizer usage.

The first of these patterns is consistent with the observations we made in the introduction concerning the fertilizer curve of a single organism and suggests that at low levels of fertilizer use, differences in fertilizer use have high explanatory power.

The second pattern may be due to the fact that reaching the highest attainable yield is impossible without the use of large quantities of fertilizer, whereas it is possible to use a great deal of fertilizer while still failing to achieve high yields, so that among countries who have neared the fertilizer saturation point, differences in factors like climate, soil quality, crop varieties, agricultural expenditure, and agricultural technology have come to dominate differences in fertilizer use and therefore will have greater power to explain differences in yield. Another possible explanation is that the correlation is so strong at low levels of fertilizer usage because those countries are in general quite similar to one another, and in fact many of them are located in the same geographical region, Sub-Saharan Africa.

## Model Fitting

Rather than explicitly modeling the relationship between the variables as a non-linear curve with an asymptote, we opted to transform the fertilizer variable in order to linearize the relationship, after which we fit a linear model. Of all such transformations, a logistic transformation seemed the most appropriate in light of the patterns observed in the scatter plot and of the mathematical tractability of the transformation.

## Logistic Transformation of Fertilizer Variable

The class of transformations we considered were those of the form 

$$
f(x) = \frac{a}{1+\exp{(-bx + c})} + d
$$

The parameters $a$ and $d$, being linear transformations, have no effect upon the efficacy of linearization and were consequently set to $a = 200$ and $d = -100$, so that the transformed variable could be interpreted as percent fertilizer saturation. For the same reason, the parameter $c$ was set to $0$.

With linearity in mind, the criterion by which we selected the optimal setting of $b$ was the Pearson correlation coefficient of the yield variable and the transformed fertilizer variables, which in this case is equal to the square root of the $R^2$ of an OLS model fit to the two variables.

## Grid Search and Final Linear Model
Because we only had one variable to optimize, we exhaustively explored the parameter space with a grid search. From preliminary visualization, we judged that the likely order of magnitude of the optimal parameter value was between $10^{-3}$ and 1, and so we performed the grid search across $10^4$ equally spaced values from $10^{-3}$ to 1. The optimal parameter value that we obtained was $b = 0.0184$, resulting in a correlation coefficient of $r = 0.698$ (the code can be found in the appendix).

We can see that after the transformation, a linear model fits the data quite well:

![Figure 5]({{ site.baseurl }}/assets/img/scatteryield2019.png)

Under the fitted model, a one-percent increase in fertilizer saturation is associated with a 40 kg per hectare increase in yield and Adjusted $R^2 = 0.484$. This effect size is on the same order of magnitude of those observed in an experimental setting on the scale of single organisms.

## Gaussian Mixture Model

In the post-transformation scatter plot, one can observe clusters, that is, the data points do not uniformly populate all points along the model line. Not only that, but the clusters that stand out have quite different covariance structures from one another: the cluster to the extreme right seems to vary most vertically and the cluster to the extreme left varies most along the line of the linear model. Such observations naturally suggested a Gaussian Mixture Model (GMM), rather than, say, a $k$-means model, because the former works by identifying clusters with ellipsoidal variance.

We fit a GMM with the $mclust$ package in R, where the BIC acted as the model selection criterion. The best model according to BIC was an ellipsoidal, equal orientation model with 4 components. The results are plotted below.

![Figure 6]({{ site.baseurl }}/assets/img/clustgmm20194.png)

![Figure 7]({{ site.baseurl }}/assets/img/clustermap2019bold.png)



## Sources

* Alley, Marcus & Vanlauwe, Bernard. (2009). The Role of Fertilizers in Integrated Plant Nutrient Management. 

* Sheaffer, C. C., & Moncada, K. M. (2012). Introduction to Agronomy–Food, Crops and Environment.

## Code

Github Repo Link

