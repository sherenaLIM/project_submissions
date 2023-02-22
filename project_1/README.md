# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Exploring climate data of Singapore and its effects on market sentiment

### Overview

For my first project, I am going to analyze climate trends in Singapore. Climate refers to the general weather conditions prevailing over an area for a long period. There are several aspects to studying climate that includes rainfall, temperature, relative humidity, wet bulb temperature, sunshine duration etc. 

The project allows you to utilise and demonstrate the following skills:
- Basic statistics and probability
- Many Python programming concepts
- Programmatically interacting with files and directories
- Visualizations
- EDA
- Working with Jupyter notebooks for development and reporting

### Problem Statement

As a Research Analyst, you provide insights to help fund managers and stockbrokers make data-driven decisions about investments. 

Traditional economic theory purports that individuals are rational. However, machine learning models that are built on this premise fall short in their attempts to predict stock value. This project sets out to analyse the monthly weather patterns over the year and the yearly weather patterns over the years. Based on the hypothesis that meteorological conditions are associated with expressed sentiments on social media platforms such as twitter, insights gleaned from the data would enable portfolio managers to make better buy/sell decisions when they also account for weather-induced public sentiment. 

**The following hypotheses are to be further validated:** 

> 1. Higher rainfall is associated with worsened expressions of sentiment.
> 2. Cloud cover is associated with worsened expressions of sentiment.
> 3. Higher humidity is associated with worsened expressions of sentiment. 
> 4. Cold temperatures, hot temperatures, and narrower daily temperature ranges are associated with worsened expressions of sentiment.

**Citations:**
- Baylis P, Obradovich N, Kryvasheyeu Y, Chen H, Coviello L, et al. (2018) Weather impacts expressed sentiment. PLOS ONE 13(4): e0195750. https://doi.org/10.1371/journal.pone.0195750.
- Hirshleifer, D., & Shumway, T. (2003). Good Day Sunshine: Stock Returns and the Weather. The Journal of Finance, 58(3), 1009–1032. http://www.jstor.org/stable/3094570
- Mittal, A., & Goel, A. (2012). Stock prediction using twitter sentiment analysis. Standford University, CS229 (2011 http://cs229.stanford.edu/proj2011/GoelMittal-StockMarketPredictionUsingTwitterSentimentAnalysis.pdf), 15, 2352.

---

### Datasets

#### Provided Data

There are 8 weather datasets included in the [`data`](./data/) folder for this project. These correponds to rainfall, sunshine, humidity, and temperature information. 

* [`rainfall-monthly-highest-daily-total.csv`](./data/rainfall-monthly-highest-daily-total.csv): Monthly highest total daily rainfall from 1982 to 2022, measured in milimeters(mm).
* [`rainfall-monthly-number-of-rain-days.csv`](./data/rainfall-monthly-number-of-rain-days.csv): Monthly number of rain days from 1982 to 2022. A day is considered to have “rained” if the total rainfall for that day is 0.2mm or more.
* [`rainfall-monthly-total.csv`](./data/rainfall-monthly-total.csv): Monthly total rain recorded in mm(millimeters) from 1982 to 2022.
* [`sunshine-duration-monthly-mean-daily-duration`](./data/sunshine-duration-monthly-mean-daily-duration.csv): Mean sunshine hours per month from 1982 to 2022, measured in hours (hrs).
* [`relative-humidity-monthly-mean`](./data/relative-humidity-monthly-mean.csv): Mean relative humidity per month from 1982 to 2022, measured in percentage(%).
* [`surface-air-temperature-annual-mean-daily-minimum`](./data/surface-air-temperature-annual-mean-daily-minimum.csv): Mean daily minimum surface air temperature per year from 1982 to 2022, measure in degrees Celsius(°C).
* [`surface-air-temperature-monthly-mean-daily-minimum`](./data/surface-air-temperature-monthly-mean-daily-minimum.csv): Mean daily minimum surface air temperature per month from 1982 to 2022, measure in degrees Celsius(°C).
* [`wet-bulb-temperature-hourly.csv`](./data/wet-bulb-temperature-hourly.csv): Hourly wet bulb temperature in degrees Celcius(°C) at 100% relative humidity.

#### Additional Data

Other relevant stock historical datasets from [finance.yahoo.com](finance.yahoo.com) that you can download and use are as follows:

* [SPDR S&P 500 ETF Trust (SPY) Historical Data](https://finance.yahoo.com/quote/SPY/history/): Monthly SPY historical data from 1993 to 2022.

---

### Data Dictionary

| Feature | Type | Dataset | Description |
|---|---|---|---|
| **rainy_days** | *int64* | *no_of_rainy_days* | *monthly number of rain days from 1982 to 2022. A day is considered to have “rained” if the total rainfall for that day is 0.2mm or more* |
| **total_rainfall** | *float64* | *rainfall-monthly-total* | *monthly total rain recorded in millimeters(mm) from 1982 to 2022* | 
| **daily_highest** | *float64* | *maximum_rainfall_in_a_day* | *monthly highest total daily rainfall from 1982 to 2022, measured in milimeters(mm)* |
| **sunshine** | *float64* | *mean_sunshine_hrs* | *mean sunshine hours per month from 1982 to 2022, measured in hours (hrs)*|
| **humidity** | *float64* | *mean_rh* | *mean relative humidity per month from 1982 to 2022, measured in percentage(%)* |
| **monthly_daily_min_temp** | *float64* | *temp_mean_daily_min* | *mean daily minimum surface air temperature per month from 1982 to 2022, measure in degrees Celsius(°C)* |
| **hourly_temp** | *float64* | *wet_bulb_temperature* | *at 100% relative humidity, the hourly wet bulb temperature in degrees Celcius(°C)* |

---

### Brief Summary of Analysis

#### Assumption
**Weather can affect stock market players like any other people in their decisions through psychological channels of mood and perception, in the following ways.**
> 1. Higher rainfall is associated with worsened expressions of sentiment
> 2. Cloud cover is associated with worsened expressions of sentiment
> 3. Higher humidity is associated with worsened expressions of sentiment
> 4. Cold temperatures, hot temperatures, and narrower daily temperature ranges are all associated with worsened expressions of sentiment.

#### Key Takeaways

Fair weather conditions include months with low rainfall, higher sunshine, low humidity and moderate temperatures- we would expect stocks to rally as traders are more optimistic. On the other hand, bad weather conditions include months with lower sunshine, high rainfall, high humidity and high temperatures (typically during the monsoon seasons) - we would expect stock performance to take a dip as traders are less optimistic.

**1. Holding sunshine duration, precipitation, and temperature constant, stock market players are prone to sell their stocks away when there is higher rainfall.** 
> * Based on the `Time Series Monthly Calendar Heatmaps` for 'total_rainfall', 'maximum_rainfall_in_a_day' and 'no_of_rainy_days', we can see that the months of November to February (Singapore's Northeast Monsoon Season) saw the highest rainfall - during this period, we expect trading volume to increase and stock price to fall.
> * Based on the `Time Series Line Plots` for 'total_rainfall', 'maximum_rainfall_in_a_day' and 'no_of_rainy_days', we can infer that the gradual increase in the number of rain days over the years might lead to a gradual increase in the volume of transactions, but there could be a decline in stock price.

**2. Holding rainfall, humidity, and temperature constant, stock market players are more willing to buy stocks during sunny weather.**
> * Based on the `Time Series Monthly Calendar Heatmaps` for 'mean_sunshine_hrs', we can see that the months of January to August saw higher sunshine durations - we expect trading volume to increase and stock price to rise during these months.
> * Based on the `Time Series Line Plots` for 'mean_sunshine_hrs', we can infer that the apparent increase in sunshine duration would lead to a rise in the volume of transactions, and a rally in stock price over the years.

**3. Holding rainfall, sunshine, and temperature constant, stock market players are predisposed to sell their stocks if humidity is high.**
> * Based on the `Time Series Monthly Calendar Heatmaps` for 'mean_rh', we can see that the months of November to January reported higher levels of humidity, during Singapore's Northeast Monsoon Season - during this period, we expect trading volume to increase and stock price to fall.
> * Based on the `Time Series Line Plots` for 'mean_rh', we can infer that the decline in humidity over the years is expected to lead to a rise in the volume of transactions, or an increase in stock price.

**4. Holding rainfall, sunshine, and humidity constant, stock market players are more willing to purchase stocks when the daily diurnal temperature range (DTR) is wider, and when temperature does not deviate too much from the average.**
> * Based on the `Time Series Monthly Calendar Heatmaps` for 'temp_mean_daily_min' and 'wet_bulb_temperature', we can see that the months of April to July saw the highest temperatures, while the months of December and January saw the lowest temperatures - during these periods, we expect an increase in trading volume and underperforming stock prices.
> * Based on the `Time Series Box and Whiskers Plots by Month` for 'wet_bulb_temperature', we can see that the IQR, that represents the daily diurnal temperature range (DTR), is wider in December and January - during these months market sentiments should be fairly positive. 
> * Based on the `Time Series Line Plots` for 'temp_mean_daily_min', and 'wet_bulb_temperature', we can infer that the increase in temperature would lead to a fall in the volume of transactions.

---

#### Conclusions/Recommendations
**For predictive model to incorporate climate features, such that portfolio managers are able to predict SPY's closing values one day in advance and make more accurate data-driven sell/buy decisions.** 
- Ceteris Paribus, if the predicted stock value for the next day is n standard deviations less than the mean, we buy the stock &rarr; `buy decision`, else we `wait`
- Ceteris Paribus, if the predicted stock value is m standard deviations more than the actual adjusted value at buy time, we sell the stock &rarr; `sell decision`, else we `hold`

**Limitations of the Project**
- ^STI (Singapore Straits Times Index) is a far more superior proxy for market sentiment of traders whose economic behaviors are affected by the Singapore weather as opposed to SPY (SPDR S&P 500 ETF). However, I was unable to obtain the complete 40-year ^STI historical dataset from any credible online resource. SPY is the next best substitute as it is the largest ETF in the world and represents the movement of the overall stock market more accurately than individual stocks. However, movements in volume and return of SPY are less likely to be driven by the small number of investors residing in Singapore, relative to the larger pools of investors from other geographical regions.
