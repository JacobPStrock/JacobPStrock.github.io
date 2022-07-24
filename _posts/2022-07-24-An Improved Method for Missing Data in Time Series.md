---
usemathjax:
    true
header: 
    teaser: /assets/images/Model_comparison_icon.png
---

![Model Comparison](/assets/images/Model_comparison_icon.png)

Time series analysis is the topic that has gripped me since I started studying statistics. Who doesn't want to better understand the past and predict the future? Most of the data that is collected has a time component which is non-negligable. While some consider the non-independence of data a nuissance for statistical analysis, I consider it one of the greatest opportunities to understand the time pattern. 

Time series analysis and time series of data are powerful for building our understand on a topic, but there is almost invariably a big challenge: missing data. Measuring devices brake, data collection is interupted, and periodically the funding may dry up. The way that we handle this missing data can have large effects and potential biases for our inference. 

Bayesian State-Space models and the particular case of the dynamic linear model are popular time-series tools with an inherent ability to imput missing data through forward filtering with the Kalman filter followed by backward sampling. These model allow any parameter of our model to time vary, allow us to study temporally changing relationships. This includes covariance matrices through a method called discount factoring. This method works extremely well for dynamic covariance when data are mostly complete. The method, outlined in XXX, mathematically suggest that the covariance matrix XXX for the latent state specification of the model, should decay from one time step to the next.

Practically, this equation represents how the information is lost from one time step to the next.

The issue is that for data with extended periods of missingness, standard discounting methods would have the loss of information grow at an exponential rate in the forward filter:

This is as opposed to a linear rate in a static covariance specification: 

Inutition suggests that an exponential loss of information in missing data may be overly conservative, but what covariance specification gives us the most accurate results for periods of extensive missing data?

Further, what is the optimal selection criteria for selecting a discount factor?

<object data="/assets/supplementaryfiles/NESS_presentation_Final.pdf" width="1000" height="1000" type='application/pdf'></object>


__Objective__:

Using a fit to the real time series, I repeatedly simulate time series, using discount factoring with linear or exponential rates of information loss for the forward filter step. Because the data and missingness are simulated. 

Using data generated with different discount factor levels, I compare recovery of the true discount factor values with 6 different criterion:

__Data__:

In this investigation, I will use real time series data from the Narragansett Bay Long-term Time Series. I chose to use the log transformed Chlorophyll (algal pigment data), because it is the subject of another time series analysis I have been working on. The data is from 2003 to 2020, collected at weekly resolution. While the use of a multivariate analysis would be optimal for imputation, I use a univariate series to focus on the question of covariance specification.

Raw data can be found [here](https://web.uri.edu/gso/research/plankton/).

__Data Processing__:


__Analysis & Results__:




__Conclusions__:

- Consistently, RMSFE had the most statistical power to recover the parameterization of the data generation model.
- 
- 
