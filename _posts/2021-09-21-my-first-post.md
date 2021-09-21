---
layout: post
title:  "Missing Data and my Masters Project"
date:   2021-09-11 15:47:34 -0500
categories: jekyll update
---

So, I want to talk about my masters project. It's been almost 18 months since I successfully completed the research project that enabled me to graduate with my MS in statistics. I'm mostly recovered. It involved imputing missing data about individuals screened for rheumatic heart disease. Thousands of children had been screened, but only a small percentage had received a second, more thorough examination. I wanted to answer questions about the whole population that involved information measured in the second examination. 

There are many ways to handle missing data, from "this is technically a solution" to "this is almost perfect, but no one has the time." Here are some examples:

* __Complete cases:__ You can eliminate all the observations with missing data and perform the analysis with complete cases. 
* __Mean imputation:__ Or you can replace the missing data with the mean value for that variable in the observed data. 
* __Regression imputation:__ You can use the observed data to construct a regression model to predict what would have been observed, then fill in the blanks. 
* __EM algorithm:__ An iterative approach that alternates between estimating the missing values and estimating unknown paramters, improving each set of estimates in each step.
* __Multiple imputation:__ Missing values are drawn from the observed data distribution many times, creating many complete data sets. Then all the data sets are analyzed and the results are combined to produce final results which account for the added uncertainty of having missing data.

There are different ways for data to be missing, and the type of missingness determines what method should be used. All the solutions mentioned above require that the missingness is either completely random (MCAR) or explained by other observed variables (MAR). However, they produce biased estimates when the data are missing not at random (MNAR). This means data are not observed based on the unobserved values themselves. In my project, the variable of interest was the rheumatic heart disease diagnosis, and some related measurements. The first stage of screening identified individuals who were likely to have the disease, so the missing data affected the probability that an observation was missing. I needed a method to use the incomplete data to make estimates about the population, while accounting for nonrandom missingness.

This brings us to Bayesian missing data models. In a Bayesian framework, we can model missing data the same way we model unknown parameters. However, it also allows us to handle nonrandom missingness by modeling the distribution of missingness explicitly. We can factor the distribution of the data (observed and unobserved) and an indicator for missingness into the marginal distribution of the complete data and a missingness model which is conditional on the data. This incorporates the relationship between the missingness and the unobserved data. This type of structure is best when we know about the causes and pattern of missing data. Pattern-mixture models factor the likelihood differently and do not require us to specify a model for the missingness.

* Latex math to show factored likelihood w/ missingness model and full data marginal

Using a Bayesian approach for missing data is a clear, intuitive way to accurately handle nonrandom missingness. The mechanism behind the missingness can be modeled directly, incorporating any information we have about why data were not observed. Then the information provided by the nonrandom missingness can be used to improve estimation.