# Analysis of time series data and forecast trends using Prophet model

Analysis of time series data is to understand the trends in google search traffic, stock prices and revenue for MercadoLibre and forecast the future trends using Prophet model for planning. The CSV data used consists of:
1. google_hourly_search_trends.csv
2. mercado_daily_revenue.csv
3. mercado_stock_prices.csv

 Following steps were followed:
 
* 1: Find unusual patterns in hourly Google search traffic.

- Read and use google search data and focus on just the month of May 2020 by slicing. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?

`Observation:` The total search traffic for the month of May 2020 is 38181 whereas median monthly search traffic for the year was 35172.5. Thus, the Google search traffic increased by approx. 8% in May 2020 when MercadoLibre released its financial results.

* 2: Mine the search traffic data for seasonality
(so that marketing efforts can be focussed around the times with most traffic)

- Using above data, plot the average traffic by the day of the week and by the week of the year.
try to track and predict interest in the company and its platform for any time of day,so that the .
- using hvPlot, visualize this traffic as a heatmap, referencing the index.hour as the x-axis and the index.dayofweek as the y-axis.

`Observation:` Visualization shows that traffic is maximum at midnight most of the days in the week except day 5. In general we can say traffic tends to be more in 3 to 4 hours around midnight.
Also, The traffic tends to increase during winter holiday period i.e. starts increasing from week 40 through week 52. However it is maximum in first 8 weeks or first 2 months of the year.


* 3: Relate the search traffic to stock price patterns.

- Read in and plot the stock price data. 
- Concatenate the stock price data to the search data in a single DataFrame.Slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot and visualize the data to understand if they have a common trend.
- Create new columns in the DataFrame named `“Lagged Search Trends”` that offsets, or shifts, the search traffic by one hour,`“Stock Volatility”`, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility and `“Hourly Stock Return”`, which holds the percent change of the company's stock price on an hourly basis. Calculate the time series correlation,to understand if a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price return.

`Observation:` Both time series i.e. stock prices and google trends show a common trend in the mid of March 2020 where there is decline in search trends as well as stock prices for MercadoLibre.
There is negligible inverse relationship between lagged search and stock volatility of -0.14 whereas the lagged search traffic and the stock price returns have almost no predictable relationship.

Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms.

* 4: Create a time series model with Prophet for forecast.

- Produce a time series model that analyzes and forecasts patterns in the hourly search data. 
- Set up the Google search data for a Prophet forecasting model. After estimating the model, plot the forecast to understand the near-term forecast for the popularity of MercadoLibre.
- Plot the individual time series components of the model to understand hourly, weekly, and yearly trend for the google traffic.

`Observation:` The near term forecast for MercadoLibre shows that its popularity would be constant for next 80 days.
At around midnight MercadoLibre exhibits the most popularity.
Tuesday seems to get the most search traffic in the week.
MercadoLibre has the lowest search traffic in October month of the year.

* 5: Forecast revenue by using time series models for next quarter

- Read in the daily historical sales (revenue) figures, and then apply a Prophet model to the data.
- Interpret the model output to identify any seasonal patterns in the company's revenue. 
- Produce a sales forecast with the most likely, best- and worst-case scenarios.


`Observation:` Based on the forecast drawn for the sales of MercadoLibre using Prophet model, the next quarter between 2020-07-01 to 2020-09-30 will most likely have expected sales of 1945.38 (millions US dollars), where there is a possiblity of sales of 2116.39(millions US dollars) as the best case and 1774.11(millions US dollars) as the worst case scenario.

## Technologies and Modules

This tool leverages python 3.7 with the following packages:

* [pandas] (https://pandas.pydata.org/docs/getting_started/index.html)- for data analysis
* [googlecolab] (https://colab.research.google.com/?utm_source=scs-index)
* [hvplot] (https://hvplot.holoviz.org/user_guide/Introduction.html)- to display an interactively explorable plot
* [scikit-learn] (https://scikit-learn.org/stable/)- open source machine learning library
* [pathlib] (https://docs.python.org/3/library/pathlib.html#module-pathlib)- to read file path
* [holoviews] (https://holoviews.org/)- to visualize trends
* [fbprophet] (https://pypi.org/project/fbprophet/)- to create model and forecast
* [datetime] (https://docs.python.org/3/library/datetime.html)

## Installation Guide

```
conda install pandas
pip install fbprophet
pip install hvplot
pip install holoviews
```

## Contributor

Shivangi Gupta

## License

MIT
