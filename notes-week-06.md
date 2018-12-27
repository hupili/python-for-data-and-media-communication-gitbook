# Week 06 - API

<div id="toc">

<!-- TOC -->

- [Week 06 - API](#week-06---api)
    - [Requests](#requests)
        - [Make a Request](#make-a-request)
        - [Response Content](#response-content)
    - [API](#api)
        - [Why use api](#why-use-api)
        - [Use API via HTTP request/ response](#use-api-via-http-request-response)
            - [Test API without using Python](#test-api-without-using-python)
        - [Use API via function calls to other modules/ packages](#use-api-via-function-calls-to-other-modules-packages)
    - [Bonus: Your first automatic writing robot on Twitter](#bonus-your-first-automatic-writing-robot-on-twitter)
    - [Exercises and Challenges](#exercises-and-challenges)
        - [Newyork Times API](#newyork-times-api)
        - [Douban API](#douban-api)
        - [Yahoo Finance API](#yahoo-finance-api)
        - [GitHub API](#github-api)
        - [Twitter API](#twitter-api)
        - [Wechat API](#wechat-api)
        - [Google Map API](#google-map-api)
        - [Bonus: Real Estate property in Hong Kong (via government open data portal API)](#bonus-real-estate-property-in-hong-kong-via-government-open-data-portal-api)
        - [Bonus: Blockchain - chain data and exchange data](#bonus-blockchain---chain-data-and-exchange-data)
        - [Bonus: Automatic earthquake writer](#bonus-automatic-earthquake-writer)
        - [Bonus: MailGun API](#bonus-mailgun-api)

<!-- /TOC -->

</div>


## Requests

Requests are the primary module we use to crawl website and get the content.

### Make a Request

Making a request is easy. First of all, please use `pip` to install requests before import. Then import the `requests` module. Usually, we use `requests.get` to make a request for data.

```python
import requests
r = requests.get('http://www.imdb.com/list/ls058982125/') #2017 Movie List
```

Now, we have a Response object called r. We can get all the information we need from this object, information about the 2017 movie list.

### Response Content

After we get the response object r, we need to read the content of the server’s response. There are three ways  to read contents.

```python
import requests
r = requests.get('http://www.imdb.com/list/ls058982125/') #pass url in ()
r.text
r.json
r.content
```

If you want to return text data, use `r.text`.(Use mostly)

If you want to return JSON, use `r.json`

If you want to return pictures and files, use `r.content`, it will return the binary data.

## API

Application Program Interfaces, or APIs, are commonly used to retrieve data from remote websites. Sites like Twitter, Douban and even government websites all offer certain data through their APIs. To use an API, you make a request to a remote web server, and retrieve the data you need.

### Why use api

Compared with other ways like download directly, APIs are useful in the following cases:

* The data is changing quickly. It doesn't need you to re-download it every minute - this will take a lot of bandwidth, and be pretty slow, the data we get through api is always up to date (unless you specify).
* Usually, the data sets return from APIs are usually can be directly convert to CSV or JSON, which is more structural and clean, you don't need to spend a lot of time to clean and find the data compared with request from `.html`.
* You can filter the data you want instead of download a large of data set.

Generally, different websites have different APIs methods to request the data. For example, the APIs of [USGS](https://earthquake.usgs.gov/fdsnws/event/1/) and [Douban](https://developers.douban.com/wiki/?title=api_v2) is a url, and you can change some parameters in the url to get the different data. While, the twitter api is a set of tokens and keys, you can call different functions to get different data.

### Use API via HTTP request/ response

So, in the following example, we'll be querying a simple API to retrieve data about the last 100 years' earthquakes that happen in Taiwan.

Step 1: Find it's API, and read it's documentation

API link : https://earthquake.usgs.gov/fdsnws/event/1/

Different organizations and websites have their own rules of using API. For this earthquake API, you cannot just request all data from this original API link, you need to specify which region, what period of time you want. It's like declare what content/data you want to request. Then you can just pass those parameters following the original API link to request those data, you can click the above API link see their examples to learn more.

Step 2: Set arguments and functions we want use

Functions:

* `query?`
* `count?`

Arguments:

* Start time: 1918-08-24
* End time: 2018-08-24
* Min latitude: 21.890
* Min longitude: 119.300
* Max latitude: 25.320
* Max longitude: 122.030

You can get 4 location parameters from [worldatlas](https://www.worldatlas.com/as/tw/where-is-taiwan.html)

Step 3: Create the API We want

```python
import requests
import csv

api_url = 'https://earthquake.usgs.gov/fdsnws/event/1/'
api_method = 'query?'
api_method_2 = 'count?'
api_format = 'format=geojson'
api_starttime = '1918-02-21'
api_endtime = '2018-02-21' #if you want to return data up to now, just to omit the endtime
api_minlatitude = '21.890'
api_minlongitude = '119.300'
api_maxlatitude = '25.320'
api_maxlongitude = '122.030'

query_url ='{0}{1}{2}&starttime={3}&minlatitude={4}&maxlatitude={5}&minlongitude={6}&maxlongitude={7}'.format(api_url,api_method,api_format,api_starttime,api_minlatitude,api_maxlatitude,api_minlongitude,api_maxlongitude)
#prepare for calling query function

count_url ='{0}{1}{2}&starttime={3}&minlatitude={4}&maxlatitude={5}&minlongitude={6}&maxlongitude={7}'.format(api_url,api_method_2,api_format,api_starttime,api_minlatitude,api_maxlatitude,api_minlongitude,api_maxlongitude)
#prepare for calling count function
```

Step 4: Requests content

If you just want to know how many earthquakes happen in the past 100 years, just use `count_url`, it will return how many data we get.

```python
response = requests.get(count_url)
data = response.json()
data # equals to print(data)
```

Note: **#in Jupyter Notebook you can omit 'print()' by directly using its name to print something**

Output:

```
{'count': 3939, 'maxAllowed': 20000}
```

If you just want to get all data and extract key information, just use `query_url`.

```python
response = requests.get(query_url)
data = response.json() #response JSON
data # print all data
```

Step 5:  Select the key values we want: mag, place and time, and write it in the csv file

You can check out the returned JSON, The outermost layer is a dict, and you will find all key information we want is in the key `features`, meanwhile, there are so many features. So firstly, we should extract all features by using `data['features']`, it will return a list of all features. And in the list, the information of every earthquake is in an dict. So we can further use keys to access its values.

```python
with open('TTT.csv','w') as f:
    writer = csv.writer(f)
    header = ['place','mag','time']
    writer.writerow(header)

    for i in range(0,len(data['features'])):
        writer.writerow([data['features'][i]['properties']['place'],data['features'][i]['properties']['mag'],data['features'][i]['properties']['time']])

    f.close()

    # data['features'][i]['properties']['mag'] means to find all magnitude of the earthquake
    # data['features'][i]['properties']['place'] # find all location
    # data['features'][i]['properties']['time'] # find all time
```

Output:

![Taiwan Earthquake Data](assets/taiwan-earthquake-data.png)
Quiz: You can see that the time is not what we want. Can you convert them to UTC time(Universal Time Coordinated).

#### Test API without using Python

Note that `requests.get(url)` basically sends an `GET` HTTP request to the server. You can achieve this without using Python. Your web browser, like Google Chrome, sends a lot of `GET` requests every day to the websites you visit. You can use `print(url)` to get the assembled final URL and copy-and-paste this URL into your browser address bar, to test the response from the server. Since most API returns JSON data structure, you can use the [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) extension in Google Chrome to get a better view and easier explore the response.

![Jsonview Sample](assets/jsonview-sample.png)

### Use API via function calls to other modules/ packages

Another API method that is worthy to introduce is using the keys and token they give to you, through which you can use the function they build to get the data. But a shortcoming about this method is there is very limit the amount of data you can get. The organizations with a large database are very strict about this. In this example, we will also use Taiwan example, to scrape users tweets under the keyword of 'Taiwan earthquake'.

Step 1: Check out `python-twitter` and install it

[Python twitter](https://python-twitter.readthedocs.io/en/latest/) is a library which provides a pure Python interface for the Twitter API. It works with Python 2.7+ and Python 3.

As usual, we use Jupyter Notebook to do exercise and pip way to install

```python
!pip install python-twitter
```

Step 2: Getting your application tokens

In order to use the python-twitter API client, you first need to acquire a set of application tokens. These will be your `consumer_key` and `consumer_secret`, which get passed to  `twitter.Api()` when starting your application. Please refer to the [documentation](https://python-twitter.readthedocs.io/en/latest/getting_started.html) and apply your own key.

```python
import twitter
import csv
api = twitter.Api(consumer_key) #please pass your own api key
```

Step 3: Find the correct function to call

There are many functions to accomplish different demands. If you want to get status from one given twitter ID, `api.GetUserTimeline` is the right one. As for our example, we should use `api.GetSearch` to get the comments. Then change the parameters we want. For more functions, please see [here](https://python-twitter.readthedocs.io/en/latest/twitter.html#module-twitter.api).

```python
results = api.GetSearch(term='taiwan earthquake',
        raw_query=None, 
        geocode=None, 
        since_id=None, 
        max_id=None, 
        until='2018-08-28', 
        since='2018-01-01', 
        count=100, #maximum you can get
        lang='en', 
        locale=None, 
        result_type='mixed', 
        include_entities=None, 
        return_json=False)
len(results) #check how many statues you get
type(results) # check the data type
```

Step 4: Take out the value we want and write it to CSV file

```python
with open('earthquake_comments.csv','w') as f:
    writer = csv.writer(f)
    header = ['Names','IDs','Time','Comments']
    writer.writerow(header)
    for i in range(0,len(results)):
        writer.writerow([results[i].user.screen_name,
        results[i].id,
        results[i].created_at,
        results[i].text])
```

Output:
![Earthquake comments](assets/chapter4-earthquake-comments.png)

## Bonus: Your first automatic writing robot on Twitter

Although our focus in this chapter is to get data from different sources via API, some of the APIs are more than that. For example, you can use the `python-twitter` module to post a status to Twitter. Now that you already know how to template string (`%` and `str.format`) and how to post a Twitter status, you can combine them as your first _automatic writing robot_!

Here are some examples of such robots:

- A robot that summarises Initium Media articles and post status upon new release. You can find [source code](https://github.com/hupili/summary-bot/blob/master/bot.py), or see it [in action](https://twitter.com/summary_bot).
- [EQBOT](http://eqbot.com/) gets earthquake updates in an interested region and post to Twitter when there is a new earthquake. The bot is reproduced by our TA as [@Chico.xyc](https://twitter.com/chicoxyc), whose source codes are in this [notebook](https://github.com/hupili/python-for-data-and-media-communication/blob/master/api-examples/Taiwan%20earthquake%20robot.ipynb).


## Exercises and Challenges

### Newyork Times API

https://developer.nytimes.com/

### Douban API

Retrieve and analyse the recent movie. Douban's API will be helpful here:

- [API sample for Recent movies](https://api.douban.com/v2/movie/in_theaters)
- [API sample for movie details](https://api.douban.com/v2/movie/subject/26942674)

Try to store the recent movie data into a CSV for future analysis. One example header could be:

```csv
title,director,year,cast,description,region
```

Reference use cases:

- [Hu Zizhe, COMM7780, S2018](https://github.com/hupili/python-for-data-and-media-communication/blob/b69f4a4d12dab58920a871e3e2aadf1a7f04d5ac/api-examples/week5_douban_huzizhe.py)

### Yahoo Finance API

Yahoo Finance provides rich set of stocks API. You can get company information and quote information from the API. The API is originally designed for their internal use. People have done a lot of analysis on it and reverse engineered the parameters so you can easily play around it. Find some example use from [this notebook](https://github.com/hupili/python-for-data-and-media-communication/blob/master/api-examples/Yahoo%20Finance%20API.ipynb).

### GitHub API

GitHub provides very convenient/ developer friendly access to its pubic database via [its API](https://developer.github.com/v3/). For example, one can enumerate the people who have starred one repo by calling (HTTP request) the following API endpoint:

```text
https://api.github.com/repos/{username}/{reponame}/stargazers
```

For example, click [here](https://api.github.com/repos/hupili/python-for-data-and-media-communication-gitbook/stargazers) to see the API response that includes all users who have starred our open book repo.

### Twitter API

Twitter provides official API to access its data and allows one to programmably post status updates on the platform. We have introduced the API and a Python package in previous sections. You can search for a certain keywords and get related tweets using this API.

Reference use cases:

- [XU Yucan, COMM7780, S2018](https://github.com/hupili/python-for-data-and-media-communication/blob/master/api-examples/week5_taiwancomments_xuyucan.py)

### Wechat API

Wechat does not provide public API but its own web App has an internal HTTP API. People have done good analysis on it and built very convenient packages to retrieve data and post messages. [wechat-egonet](https://github.com/hupili/wechat-egonet) is a script based on the library called `itchat`. You can use it to get your friend list and chatrooms information.

Reference use cases:

- **pwords**, 2018, _个人微信群组关系网络图 (ego-network)_ [Link](https://mp.weixin.qq.com/s/DgAXmcR2kn3q2xjsEiwpJg)

### Google Map API

Retrieve a JSON response from Google Map API. Here is an example: [Get the location of HKBU](https://maps.googleapis.com/maps/api/geocode/json?address=hong%20kong%20baptist%20university).

Once you know how to use `requests` and `json` to get the interested coordinates data, you can revisit the [city distance challenge](notes-week-03.md#distances-among-cities) from last chapter. Then you have a fully automated solution.

**NOTE**: The above HTTP API does not work starting from Aug 2018. Instead, you can use the Google geo coder from `geopy` library. You need to apply for an API key first. Following sample code can help you.

```python
from geopy.geocoders import GoogleV3
geolocator = GoogleV3(api_key='Put your Google Map API Key here')
location = geolocator.geocode("慈雲山毓華里18號慈華商場地下2-3號")
location.point
```

### Bonus: Real Estate property in Hong Kong (via government open data portal API)

Lookup real estate properties on HK gov open data portal, e.g. the [dataset page](https://data.gov.hk/en-data/dataset/centaline-centanetod-ccipropertyinfo/resource/4d3d7289-9d84-4f31-bf7e-a515d00d5328). Retrieve the data that `scp_mktc` contains '九龍' from year 2000 up to now. API result is like [this](assets/data-gov-hk-API-results).

### Bonus: Blockchain - chain data and exchange data

[blockchain.info](blockchain.info) provides a set of [API](https://www.blockchain.com/api) for one to retrieve information related with bitcoin transactions. Pick one wallet address, check its UTXO sets and sum up the values to get the total balance in this wallet.

[A free crypocurrency API](https://min-api.cryptocompare.com/) for you to retrieve and study historical exchange rates. We are interested in bitcoin price. Try to get the exchange rate day-by-day of `BTC/USDT` pair in recent years and store them in a file.

### Bonus: Automatic earthquake writer

* Implement a basic version of first automated writer - QuakeBot from LA Times.
  * Get real-time data of earthquakes in `America` from USGS API
  * Print a story to the screen include place, time, magnitude, using template string / string interpolation
  * See [here](https://gizmodo.com/quakebot-an-algorithm-that-writes-the-news-about-earth-1547182732) for an introduction of the bot. See [here](https://www.theregister.co.uk/2017/06/22/la_times_bot_spreads_fake_news/) for an incident and think how to avoid it?

Reference use cases:

- [XU Yucan, COMM7780/JOUR7280, F2018](https://github.com/ChicoXYC/python-for-data-and-media-communication/blob/master/api-examples/Taiwan%20earthquake%20robot.ipynb)

### Bonus: MailGun API

Try to send automatic emails using [MailGun](https://www.mailgun.com/). Imagine you want to maintain the relationship with thousands of customers. You have the name list with email addresses. You want to write an intimate email so that every mail looks like manually tailored for the recipient. However, it is very time consuming to do this manually. You come up with an idea based on string templating and MailGun API. MailGun is a commonly used service for receiving email and sending email. You can use string templating to format the customised message and then use MailGun to send them to the recipients.

An example of using MailGun can be found in [this repo](https://github.com/hupili/mgcli).
