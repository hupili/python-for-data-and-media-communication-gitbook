# Week 11: Datetime and Time Series

<div id="toc">

<!-- TOC -->

- [Week 11: Datetime and Time Series](#week-11-datetime-and-time-series)
    - [Objective](#objective)
    - [Datasets](#datasets)
    - [Datetime](#datetime)
        - [Create datetime object](#create-datetime-object)
        - [Convert from string to datetime](#convert-from-string-to-datetime)
        - [Convert from datetime to utctimstamp and vice versa](#convert-from-datetime-to-utctimstamp-and-vice-versa)
        - [Format a datetime object to string](#format-a-datetime-object-to-string)
        - [Arithmetics on datetime](#arithmetics-on-datetime)
    - [Time Series](#time-series)
        - [Resample, aggregate and plot](#resample-aggregate-and-plot)
        - [Smoothing technique: Moving average](#smoothing-technique-moving-average)
        - [Bonus: Time Series forecasting models](#bonus-time-series-forecasting-models)
    - [References](#references)

<!-- /TOC -->

</div>

## Objective

* Understand the principle of timestamp and datetime format
* Master basic computation on datetime values, including handling timezone conversion
* Understand periodical analysis \(daily, weekly, monthly, seasonal, etc\)

Modules:

* `datetime`
* `dtparser`
* `pandas`
  * basic visualisation using polyline `.plot()`
  * zoom in/ out:  `.resample`, `.aggregate`
* `seaborn`

## Datasets

* [NBC Russian Troll on Twitter dataset](https://www.nbcnews.com/tech/social-media/now-available-more-200-000-deleted-russian-troll-tweets-n844731)
* [Twitter Data](https://github.com/kestrel614/HKODD17-Trump/tree/master/data) of the [Donald & Ivanka Trump analysis](https://initiumlab.com/blog/20170329-trump-and-ivanka/) -- reproduce the charts.
* Financial data usually comes in form of time series, e.g. [Yahoo Finance API](https://github.com/hupili/python-for-data-and-media-communication/blob/master/api-examples/Yahoo%20Finance%20API.ipynb).
* Bitcoin transactions are available via [blockchain.com API](https://www.blockchain.com/api). [A free crypocurrency API](https://min-api.cryptocompare.com/) is available to query the exchange ratio between two symbols.

## Datetime

### Create datetime object

### Convert from string to datetime

### Convert from datetime to utctimstamp and vice versa

<!-- TODO: Introduce the "timestamp" concept. -->

### Format a datetime object to string

<!-- TODO: using different style, e.g. 24-hour scheme. AM/PM scheme -->

### Arithmetics on datetime

- Know timedelta object
- Get difference between two datetime objects
  - Get total_seconds(); convert to other units like days/ weeks
- Add timedelta to a datetime object, e.g. what is the date 4 weeks later?

## Time Series

Basic requirement is to plot time series at different granularity, e.g. by hour, by day, by week, ... Articulate the findings on the polyline plot.

### Resample, aggregate and plot

### Smoothing technique: Moving average

### Bonus: Time Series forecasting models

Predictictive analysis is not a requirement from this introductory course. Our main focus is on the descriptive part. Interested readers can checkout the following models from other literatures.

- AR
- MA
- ARMA
- ARIMA

## References

* timestamp usually come in unit of milliseconds \(1/1000\) of a second. [An example](https://github.com/dmep2017/dmep2017.github.io/blob/master/d3-map-sichuan-earthquate/Data Process.ipynb) to parse this timestamp format into `datetime` format.
* Past notes of [datetime](https://github.com/hupili/python-for-data-and-media-communication/tree/master/datetime) from spring 2018.
* Brockwell, Peter J., and Richard A. Davis. Introduction to Time Series and Forecasting. 2nd ed. Springer Texts in Statistics. New York: Springer, 2002.