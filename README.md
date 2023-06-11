# Time-Series-Automation

## Context and Data
Each time series measures the number of searches for a specific keywork for a given time period. For
example, the time series of searches in Google for the keyword “Business Analytics” in the last 5 years,
measured every week (sum of searches on that week). Google trends report the search volume in a
relative scale, so each time series is normalized to a range 0 to 100, with 100 being the maximum
number of searchers for a particular time point (this means total volumes cannot be compared across
series with this dataset). In this dataset, we have time series measured at different frequencies: every
hour, every day, every week.

This dataset features some general ‘topics of interest’ and some ‘pop culture’/‘influencers’. A potential
use would be to identify if a particular keyword is ‘on the rise’ or ‘declining’, how ‘stable’ it is, etc. For
example to decide if we should invest in a long advertisement campaign with an influencer, or invest in
real state in a city, district,etc. Realistically, however, google trends is not a very precise indicator of
such, so this is purely for academic purposes.

The dataset comes in a csv format, with columns:
  - date: Date in datetime format.
  - hits: search volume, normalized to 0 –100.
  - keyword: The search term that the time series is measuring.

From this data, create several time series, one for each keyword, and then forecast them.

## The forecast problem
The ‘forecasts’ that have to be computed and reported:
  - Point forecasts: You will forecast the number of hits for the last 10% observations of the series
(rounding up). This means that the last 10% of each series will be considered the ‘test set’ that
cannot be used for modelling.
  - Probabilistic forecasts: For each time series, forecast the 75% quantile and 25% quantile across
the test set for each series
  - Expected Performance: Estimate of the mean absolute error of the predictions for each time
series. This is the estimation of what is going to be the prediction error on the test set, based on
the training, before looking at the test set.
  - Actual performance: The prediction error calculated on the actual on the test set.

The objective is to create a complete automatic methodology, that given a time
series compares several models (seasonal naïve, exponential smoothing family, ARIMA family, etc),
chooses the best one according to a metric and computes the forecasts. The methodology is then
applied to each time series.
