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
- The *datetime* module supplies classes for manipulating dates and times in the fields like time parsing, formatting or even arithmetic. You can read its document [here](https://docs.python.org/3/library/datetime.html).
### Create datetime object
- First we create a datetime object:
```python
from datetime import datetime
dt = datetime(year=1993, month=10, day=4,
              hour=9, minute=8, second=7)
dt
```
Output: 
```
datetime.datetime(1993, 10, 4, 9, 8, 7)
```
The result is a `datetime` object. A [datetime object](https://docs.python.org/3/library/datetime.html#datetime-objects) is a single object containing all the information from a time point.

### Convert from string to datetime
- In many cases, we may need to standardise the format of date/time we scraped from the Internet into datetime objects for further application. See this case:
```python
from dateutil.parser import parse
time_list = ['19/May/2017 04:10:06',
    		 '2018.2.3',
    		 'June 12, 2018']
[parse(i) for i in time_list]
```
Output: 
```
[datetime.datetime(2017, 5, 19, 4, 10, 6),
 datetime.datetime(2018, 2, 3, 0, 0),
 datetime.datetime(2018, 6, 12, 0, 0)]
```
- All the time strings in different formats have been transferred into datetime objects. The level of details depends on how explicit the information the raw data provided is.
- The *dateutil* module provides powerful extensions to the standard *datetime* module. You can check its further applications [here](https://pypi.org/project/python-dateutil/).

### Convert from datetime to utctimstamp and vice versa
- The [timestamp](https://docs.python.org/3/library/datetime.html#datetime.datetime.timestamp) is the time in seconds since an *epoch* as a floating point number. The *epoch* is the point where the time starts, and is platform dependent. On Windows and most Unix systems, the epoch is January 1, 1970, 00:00:00 (UTC). 
```python
from datetime import datetime, timezone
dt = datetime(
    1993, 10, 4, 9, 8, 7,
    microsecond=12345,
    tzinfo=timezone.utc)  #
ts = dt.timestamp()
ts
```
Output: `749696888.012345`
- Also, we can get a datetime from a timstamp:
```python
from datetime import datetime
datetime.utcfromtimestamp(ts)
```
Output: 
```
datetime.datetime(1993, 10, 4, 9, 8, 8, 12345)
```
- [UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) (abbreviated from *Coordinated Universal Time) is the primary  time standard  by which the world regulates clocks and time.

### Format a datetime object to string
#### First, let’s get the present time:
```python
from datetime import datetime
dt = datetime.now().isoformat(timespec='seconds', sep=' ')
dt
```
Output: 
```
‘2018-11-18 00:41:49’
```
- Question:
    - What is the type of  `dt`? You can try to change its parameters in `.isoformat()` or remove it to see what will happen.
    - You can also use `str(dt)` to transfer a datetime object into string.
#### formating with different style
In some cases, we may need to convert a datetime into a specific format. Now we can use `strftime()`. Here is an example:
```python
from datetime import datetime
dt = datetime(2018, 11, 20, 14, 0, 0)
print(dt.strftime('%I:%M%p %m/%d(%a),%Y'))
print(dt.strftime('%H:%M:%S %Y/%m/%d'))
```
Output: 
```
02:00PM 11/20(Tue),2018
14:00:00 2018/11/20
```
- In this case,`%H` and `%I` represent hour in 24-hour clock and12-hour clock respectively. For 12-hour clock, we use `%p` to get AM/PM from the datetime object. You can click [here](https://docs.python.org/3/library/datetime.html#strftime-strptime-behavior) to see what each parameter represents in `strftime()`.

### Arithmetics on datetime
#### Know timedelta object
- A [timedelta](https://docs.python.org/3/library/datetime.html#timedelta-objects) object represents a duration, the difference between two dates or times. We can build a timedelta object like this:
```python
from datetime import timedelta
td = timedelta(days = 1)
td
```
Output: 
```datetime.timedelta(days=1)```
- The parameter `days` can be replaced with `seconds`, `microseconds`, `milliseconds`, `minutes`, `hours` and `weeks`. We can also combine them like `timedelta(weeks = 1, days = 2, hours = 12)`
#### Get difference between two datetime objects
- To get the duration between two datetime objects, we can calculate like this:
```python
from datetime import datetime
datetime(2018, 6, 12, 0, 0) - datetime(2018, 2, 3, 0, 0)
```
Output: `datetime.timedelta(days=129)`
#### Add timedelta to a datetime object, e.g. what is the date 4 weeks later?
- We can also do calculation between a datetime object and a timedelta object:
```python
import datetime
date_today = datetime.datetime(2018, 11, 19)
#date_today = datetime.date.today()
#date_today = datetime.datetime.now()
date = date_today + datetime.timedelta(weeks = 4)
str(date)
```
Output:
```'2018-12-17 00:00:00'```
- In this case, you can use `datetime.date.today()` instead to get the real-time date.
#### In some [cases](https://www.indeed.com/q-Data-Journalism-Internship-jobs.html), we may need to deal with a group of different types of time durations:
```python
from datetime import datetime, timedelta
time_list = ['30 Minutes ago','12 Hours ago',
             '4 Days ago','3 Weeks ago',
             '2 Month ago','1 Year ago']
now = parse(datetime.now().strftime('%Y-%m-%d %H:%M:%S'))
print('The current time is {}'.format(now))
mylist=[]
for i in time_list:
    if i.lower().find('minute') != -1:
        post_time = now - timedelta(minutes = int(i.split()[0]))
    elif i.lower().find('hour') != -1:
        post_time = now - timedelta(hours = int(i.split()[0]))
    elif i.lower().find('day') != -1:
        post_time = now - timedelta(days = int(i.split()[0]))
    elif i.lower().find('week') != -1:
        post_time = now - timedelta(weeks = int(i.split()[0]))
    elif i.lower().find('month') != -1:
        post_time = now - timedelta(days = int(i.split()[0]) * 30)
    elif i.lower().find('year') != -1:
        post_time = now - timedelta(days = int(i.split()[0]) * 365)
    mylist.append(post_time)
    output = 'The time {} is {}.'.format(i, post_time)
    print(output)
```
Now we need the timedelta object to get their precise time point.
Output:
```
The current time is 2018-11-19 10:57:50.
The time 30 Minutes ago is 2018-11-19 10:27:50.
The time 12 Hours ago is 2018-11-18 22:57:50.
The time 4 Days ago is 2018-11-15 10:57:50.
The time 3 Weeks ago is 2018-10-29 10:57:50.
The time 2 Month ago is 2018-09-20 10:57:50.
The time 1 Year ago is 2017-11-19 10:57:50.
```


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
