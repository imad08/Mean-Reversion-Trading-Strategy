# Mean-Reversion-Trading-Strategy
To learn about mean reversion as a concept and how it holds importance when one is
forming a profitable trading strategy, along with other basic essentials of corporate finance
and how to apply this knowledge in python to filter out the most promising stocks out there
on the market. We first filter out stocks on the basis of their stationarity by making the use of
the hurst exponent. This is followed by an in-depth analysis of these filtered stocks over
three different time intervals to finally select the Top 25 stocks. Upon this selection, we use
Machine Learning techniques, namely ARIMA models for the prediction of these 25 stocks
and gauge our accuracy..

## Data
We were provided with minute-wise data containing stockVWAP (stock volume-weighted
average price), bid Price, ask Price of 111 stocks spanning Energy, IT, Financials,
HealthCare, Telecommunications and other sectors of the Indian market for the entire year
of 2017. Stock traded for 375 minutes each day from 9:15-3:30 and for 160 days throughout
the year. So, we have 90,000 data points to backtest our model and predict future stock
price.


## Hurst Exponent Calculation for checking stationarity of a time series:
Time Series: In simple language, time series is a sequence of observations in a certain
period of time. Recording changes in various things such as temperature in a specific city, or
as we make use of it, stock prices in regular intervals over a large period of time is a time
series. We use a time series as initial data for our analysis and to experiment on to predict
whether our models and strategies are profitable or not.
A time series of stock prices tell us a lot about how the stock has performed in different time
intervals in the past and how it may perform in the future. Through the years, extensive
analysis of time series by using sophisticated statistical tools have told traders a lot about a
stock’s traits and behaviours. Through time, the trend of the graph has given rise to the
concept of Stationarity.
Stationarity: A time series is defined to be stationary if its joint probability distribution is
mostly invariant under translations in time or space. In particular, and of key importance for
traders, the mean and variance of the process do not change over time or space and they
each do not follow a trend.If a time series is stationary in nature, we observe that the probability distribution is invariant
and hence a lot of factors somewhat constant remain in control and such a series is easier to
work upon for statistical purposes. Hence, calculating the stationarity of the series becomes
important.To calculate the stationarity of a time series, we have made use of the concept of Hurst
Exponent.
Hurst Exponent: Hurst Exponent aims to classify a time series into one of the following;
mean reverting, random walking or trending.
The idea behind it is to look at the variance of log prices to assess the rate of diffusive
behavior. For a time lag τ, the variance is given by:
Var(τ) = 〈|log(t+τ)-log(t)
2〉

In case of random walking, or general brownian motion, we can conclude that the equation
stated above directly depends on the time lag τ:
Var(τ) = 〈|log(t+τ)-log(t)
2〉~ τ

Here, if autocorrelations exist (any sequential price movements possess non-zero
correlation) this relation stated above does not stand. So to overcome this, we modify the τ
variable to τ
2H
. So we introduce an exponent factor of ‘2H’, where H is the Hurst Exponent.

Var(τ) = 〈|log(t+τ)-log(t)
2〉~ τ
2H
According to the Hurst Exponent we obtain, we conclude as following:
● H < 0.5 - Time series is mean reverting
● H = 0.5 - Time series is random walking o r in General Brownian Motion
● H > 0.5 - Time series is trending

## ARIMA MODELS
ARIMA, short for ‘Auto Regressive Integrated Moving Average’ is actually a class of models
that ‘explains’ a given time series based on its own past values, that is, its own lags and the
lagged forecast errors, so that equation can be used to forecast future values.
A pure Auto Regressive (AR only) model is one where Yt depends only on its own lags. That
is, Yt is a function of the ‘lags of Yt’. Likewise a pure Moving Average (MA only) model is one
where Yt depends only on the lagged forecast errors. An ARIMA model is one where the
time series is differenced at least once to make it stationary and you combine the AR and
the MA terms.

ARIMA model in words:
Predicted Yt = Constant + Linear combination Lags of Y (upto p lags) + Linear Combination
of Lagged forecast errors (upto q lags)

An ARIMA model is characterized by 3 parameters : p, d, q where,
p is the order of the AR term.
q is the order of the MA term.
d is the number of differencing required to make the time series stationary.


