# Course Outline

## Week 0 - GitHub

**Objective**

> * Can use GitHub for resource hosting, project management and discussion forum.
> * Can use GitHub Desktop to sync local repos with remote repos.
> * Can use `gh-pages` to host static web pages as one's portfolio.

## Week 1 - Hands-on the Terminal

**Objective:**

> * Able to navigate file system in Terminal, using shell
> * Create the first python script and execute it

MAC:

* `Cmd+space` to open Spotlight; search “Terminal” to open terminal

Shell commands:

* `cd` to switch working folder
  * Path separated by `/`
  * Special paths: `.`,`..`,`-`,`~`
* `ls`to list files/ folders in current folder
* `pwd` to check current working folder
* `ls`/`pwd` is your friend; type often to make sure where you are
* `touch` to create empty new file; mkdir to create new directory
* `python` to execute python scripts \(usually in `.py` but not necessary\)
* Format of shell commands: 
  * `<command-name> <arg1> <arg2>..` \(space separated arguments\)

Challenge:

1. Write a Python script to output "Good evening" in the Terminal.

References:

* [Terminal and shell commands \(Chinese\)](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)
* [Appendix A of "Learn Python the hard way"](https://learnpythonthehardway.org/python3/appendixa.html)

## Week 2 - Use Python as a daily tool

**Objective**:

> * Can use Python as a daily tool -- at least a powerful calculator
> * Become comfortable with Python interpreter -- the REPL pattern (Read-Evaluate-Print Loop)
> * Can use `help` to get inline documentation on new modules and functions

Python language introduction:

* Variables and assignment
* Basic data types: `int`, `float`, `str`, `bool`
* Arithmetic:
  * `+`, `-`, `*`, `/`, `//`, `%`, `**`
  * `math`, `numpy` \(may need `pip`\)
* Use functions and modules:
  * `import` (and `import ... from ...`)
  * `.` notation to reference to member variable/ method
  * `()` notation to call function
* Common modules
  * `str.*` functions
    * String templating 1: `str.format`
    * String templating 2: `format_str % (var1, var2, ...)`
  * `random`
  * `numpy`, `scipy`

Challenge:

1. Build a mortgage calculator - given principal `P`, interest rate `r` and load period `n`, calculated the amortised monthly payment `A`
2. Calculate the `area` of a circle given its radius `r`
3. Given the length of hypotenuse of a right triangle, calculate the length of its legs. You may want to get values like $$\sin(\frac{\pi}{6})$$ via `numpy.pi` and `numpy.sin` 
4. Generate 10 random numbers. \(it is OK to run your script 10 times\)

References:

* Chapter 1, 2, 3 of [official Python 2 tutorial](https://docs.python.org/2/tutorial/)
* Python format string: [https://pyformat.info/](https://pyformat.info/)

## Week 3 - Python for anything

**Objective**:

> * Master the composite data type `[]` and `{}` in Python
> * Master the control logics in Python, especially `if` and `for`
> * Further understand the different roles of text editor and interpreter. Be comfortable writing batch codes in `.py` file and execute in Shell environment.
> * [O] Understand Python engineering

Python language:

* `help`
* `bool` and comparisions
  * `str` comparison and `int` comparison
* Composite data types: `list` `[]`, `dict` `{}`
* Control flow:
  * `for`, `while`
  * `if`
  * `try..except`
* Function, class, module:
  * `def`
  * `class`
  * `*.py`; `from`, `import`

Workflow:

* Python interpreter
* pip: `pip3` for `python3`
  * `--user` option in shared computer

Challenge:

1. Distances among cities:
   1. Calculate the "straight line" distance on earth surface from several source cities to Hong Kong. The source cities: New York, Vancouver, Stockholm, Buenos Aires, Perth. For each source city, print one line containing the name of the city and distance. "Great-circle distance" is the academic name you use to search for the formula.
   2. Use `list` and `for` loop to handle multiple cities
   3. Use function to increase the reusability
2. Divide HW1 groups randomly: \(case contribution\)
   1. Get the list of student IDs from the lecturer
   2. Generate the grouping randomly
3. Solve the "media business model" calculator.

References:

* Chapter 4, 5, 6 of [official Python 3 tutorial](https://docs.python.org/3/tutorial/)

## Week 4 - JSON and API

**Objective**:

> * Learn to use Jupyter notebook. All demos following this week will be conducted in Jupyter notebook.
> * Understand API/ JSON and can retrieve data from online databases \(twitter, GitHub, weibo, douban, ...\)
> * Understand basic file format like `json` and `csv`. 
>    * Be able to comfortably navigate through compound structures like `{}` and `[]`. 
>    * Be able to comfortably use (multiple layer of) for-loop to re-format data.
>    * Be able to use serialisers to handle input/ output to files.

The brief of Application Programming Interface (API):

* Operate in client-and-server mode.
* Client does not have to download the full volume of data from server. Only use the data on demand.
* Server can handle intensive computations that not available by client.
* Server can send updated data upon request.

Modules:

* Handle HTTP request/ response: `requests`
* Serialiser: `json` and `csv`

Challenges:

* Taiwan had an earthquake in early Feb. Let's discuss this issue:
  * Search for the earthquake instances around Taiwan in recent 100 years and analyse the occurrences of earthquakes. You can refer to the same database used [here](https://dnnsociety.org/2017/09/02/map-of-sichuan-earthquake-in-d3/). Checkout the [API description](https://earthquake.usgs.gov/fdsnws/event/1/). The `count` and `query` API are useful.
  * Search on Twitter and collect user's discussions about this topic. See if there is any findings. You can approach from the human interface [here](https://twitter.com/search?q=%23台湾地震) \(hard mode\) or use [python-twitter](https://github.com/bear/python-twitter) module \(need to register developer and obtain API key\).
* Retrieve and analyse the recent movie. Douban's API will be helpful here.
  * [API sample for Recent movies](https://api.douban.com/v2/movie/in_theaters)
  * [API sample for movie details](https://api.douban.com/v2/movie/subject/26942674)
* Use Google Map API to retrieve geo-locaitons and canonical names: e.g. [Get the location of HKBU](https://maps.googleapis.com/maps/api/geocode/json?address=hong%20kong%20baptist%20university)
* Lookup real estate properties on HK gov open data portal. e.g. the [dataset page](https://data.gov.hk/en-data/dataset/centaline-centanetod-ccipropertyinfo/resource/4d3d7289-9d84-4f31-bf7e-a515d00d5328), the [API result](https://api.data.gov.hk/v1/filter?q=%7B%22resource%22%3A%22http%3A%2F%2Fhk.centanet.com%2Fopendata%2FCCI%2520Estate%2520for%2520Opendata.csv%22%2C%22section%22%3A1%2C%22format%22%3A%22json%22%2C%22sorts%22%3A%5B%5B9%2C%22desc%22%5D%5D%7D)
* blockchain.info provides a set of [API](https://www.blockchain.com/api) for one to retrieve information related with bitcoin transactions. Pick one wallet address, check its UTXO sets and sum up the values to get the total balance in this wallet.

Exercise:

* Request cerntain API to acquire information
* Convert a JSON to CSV in Python
* Convert a CSV to JSON in Python

Further readings:

* Use `beautifulsoup` to [scrape Twitter timeline content](http://www.lyonwj.com/2017/11/12/scraping-russian-twitter-trolls-python-neo4j/) from [Wayback machine](http://archive.org/web/). A good example of investigative journalism, by William Lyon from [neo4j](https://neo4j.com/).


## Week 5 - Web Scraping

**Objective**:

> * Understand the basics of HTML language, HTTP protocol, web server and Internet architecture
> * Able scrape static web pages and turn them into CSV files

Tools: \( [Step-by-step reference](module-jupyter.md) \)

* Virtualenv -- Create isolated environment to avoid projects clutter each other
* Jupyter notebook -- Web-based REPL; ready to distribute; all-in-one presentation

Modules:

* Handle HTTP request/ response: `requests`
* Parse web page: `lxml`, Beautiful Soup, `HTMLPaser`, `help(str)`
  * Useful string functions: `strip()`, `split()`, `find()`, `replace()`, `str[begin:end]`
* Serialiser: `csv`, `json`

Challenges: \(save to `*.csv`

* Use `lxml` / `bs4` `requests`
  * Collect a table for the [NSFC/RGC join research fund](http://www.ugc.edu.hk/eng/rgc/funded_research/funding_results/list_award_e2009.html). A full table can be found [here](http://www.ugc.edu.hk/eng/rgc/funded_research/funding_results/other.html). You are also welcome to collect data of [other funding schemes](http://www.ugc.edu.hk/eng/rgc/funded_research/funding_results.html).
  * Collect all the faculty's information and make a contact book. [site](http://www.comm.hkbu.edu.hk/comd-www/english/people/m_facutly_dept.htm).
  * Collect the movie list and their rating from [IMDB](http://www.imdb.com/list/ls058982125/).
* Bonus:
  * Collect the tweets from a celebrity like [this post](http://initiumlab.com/blog/20170329-trump-and-ivanka/). You can search "python twitter" for many useful modules online.

References:

* Allison Parrish's [tutorial of scraper](https://github.com/aparrish/dmep-python-intro/blob/master/scraping-html.ipynb) in summer 2017.

Further reading:

* Study `urllib` as an alternative to `requests`
* Study Regular Expression and `re` library in Python
* See how [reproducibility is improved](https://www.nature.com/articles/d41586-018-01322-9) with Jupyter notebook and other tools \(not only Python\).


## Week 6 - Table manipulation and 1-D analysis

**Objective**:

> * Master the schema of "data-driven story telling": the crowd \(pattern\) and the outlier \(anomaly\)
> * Can efficiently manipulate structured table formatted datasets
> * Use `pandas` for basic calculation and plotting

Modules:

* `pandas`
* `seaborn`
* `matplotlib` 

Statistics:

* mean, media, percentile
* min, max
* variance
* histogram
* sort
* central tendency and spread of data
* Scatter plot and correlation

Datasets to work on:

* [openrice.csv](https://github.com/hupili/python-for-data-and-media-communication/tree/master/w6-pandas) contributed by group 1

References:

* First two chapters \(i.e. before "3D"\) of the article [The Art of Effective Visualization of Multi-dimensional Data](https://towardsdatascience.com/the-art-of-effective-visualization-of-multi-dimensional-data-6c7202990c57) by Dipanjan Sarkar
* [Exercise numpy](https://www.shiyanlou.com/courses/1090) on ShiYanLou
* [Exercise pandas](https://www.shiyanlou.com/courses/1091) on ShiYanLou

Additional notes:

* You need to finish [Dataprep](dataprep.md) before analysis. That is, we start with structured data. Preparing the structured and cleaned data has no common schema. We have pointers in [Dataprep](dataprep.md) for your own reading.

## Week 7 - Text analysis

**Objective**:

> * Further strengthen the proficiency of pandas: DataFrame and Series
> * Learn to plot and adjust charts with `matplotlib`
> * Master basic string operations
> * Understand some major text mining models and be able to apply algorithm from 3rd party libraries.

Modules & topics:

* `str` - basic string processing
  * `.split()`, `in`, `.find()`
  * `%s` format string
  * `''.format()` function
* `collections.Counter` for word frequency calculation
* `jieba` - the most widely used Chinese word segmentation package.
* \(optional\) `re`- Regular Expression \(regex\) is the swiss knife for text pattern matching.
* \(optional\) `nltk` - contains common routines for text analysis
* \(optional\) `gensim` - topic mining package. It also contains the `Word2Vec` routine.
* \(optional\) Sentiment analysis - construct classifier using `sklearn` or use an API like [text-processing](http://text-processing.com/docs/sentiment.html). `TextBlob` is also useful and applied in [group 2's work](https://dnnsociety.org/2018/03/02/using-big-data-to-figure-out-how-fair-china-daily-news-is/).

Related cases:

* [Quartz's analysis](https://qz.com/962718/we-analyzed-every-modern-love-column-from-the-past-10-years-heres-what-we-learned-about-love/) of New York Times's column of "Modern Love"
* Prof. Qian Gang's famous [analysis of texts in political communication](https://www.bloomberg.com/news/articles/2017-07-18/party-of-one-newspaper-mentions-show-xi-s-dominance-of-china).

References:

* Construct Naive Bayes based classifier for sentiment analysis. [Read here](https://www.kaggle.com/ngyptr/python-nltk-sentiment-analysis)

Datasets to work on:

* [NBC Russian Troll on Twitter dataset](https://www.nbcnews.com/tech/social-media/now-available-more-200-000-deleted-russian-troll-tweets-n844731) -- The 200,000 deleted Twitter messages posted by Russian's troll accounts. Around 50M, in CSV format.
* [Hillary Clinton email archive from WikiLeaks](https://www.wikileaks.org/clinton-emails/emailid/20000) There are the plain text and parsed data but you may need to run a scraper to get the data first.

## Week 8 - Time series

> * Understand the principle of timestamp and datetime format
> * Master basic computation on datetime values
> * Understand periodical analysis \(daily, weekly, monthly, seasonal, etc\)
> * Can handle timezone conversion

Modules:

* `datetime`
* `dtparser`
* `pandas`
  * basic visualisation `.plot`
  * zoom in/ out:  `.resample`, `.aggregate`
* `seaborn`

References:

* timestamp usually come in unit of milliseconds \(1/1000\) of a second. [An example](https://github.com/dmep2017/dmep2017.github.io/blob/master/d3-map-sichuan-earthquate/Data Process.ipynb) to parse this timestamp format into `datetime` format.

Datasets:

* [NBC Russian Troll on Twitter dataset](https://www.nbcnews.com/tech/social-media/now-available-more-200-000-deleted-russian-troll-tweets-n844731) \(used last week\)
* [Twitter Data](https://github.com/kestrel614/HKODD17-Trump/tree/master/data) of the [Donald & Ivanka Trump analysis](https://initiumlab.com/blog/20170329-trump-and-ivanka/) -- reproduce the charts.

## Week 9 - Graph theory and social network analysis

**Objective**:

> * Understand the basics of graph theory
> * Understand most common applications in social network analysis
> * Can conduct graph analysis and visualisation in `networkx`

Graph metrics and algorithms:

* Shortest path
* Graph profiling: diameter, degree distribution, clustering coefficient
* Centrality: degree, PageRank, betweenness, closeness, ...
* Community detection

Challenges:

* Generate the Zachary's Karate Club data: https://en.wikipedia.org/wiki/Zachary's_karate_club .
* [SNAP dataset](http://snap.stanford.edu/)
* [Cosponsorship Network Data](http://jhfowler.ucsd.edu/cosponsorship.htm)
* Analyse the [Les Miserables' graph data](https://bl.ocks.org/mbostock/4062045).

References:

* [數據新聞﹕政商網絡系列（下）（文：陳電鋸）](https://news.mingpao.com/ins/%E3%80%90%E6%95%B8%E6%93%9A%E6%96%B0%E8%81%9E%E3%80%91%E6%94%BF%E5%95%86%E7%B6%B2%E7%B5%A1%E7%B3%BB%E5%88%97%EF%BC%88%E4%B8%8B%EF%BC%89%E3%80%80%EF%BC%88%E6%96%87%EF%BC%9A%E9%99%B3%E9%9B%BB%E9%8B%B8%EF%BC%89/web_tc/article/20150831/s00022/1441006491105) -- articulation via centrality
* [Clustering Game of Thrones](https://datascienceplus.com/network-analysis-of-game-of-thrones/) -- application of community detection
* 大家都叫我老杨, [推特上有多少「新五毛」？](http://blog.yesmryang.net/wumao-twitter/). The analysis is done in R but the dataset and topic is interesting to look at.


## Week 10 - 2D analysis and more on visualisations

## Week 11 - High-dimensional analysis

**Objective**:

> * Understand correlation and causality. Can conduct visual \(explorative\) analysis of correlation
> * Can interpret common statistic quantities
> * Dimensionality reduction

Challenge:

1. Explore the HK Legco voting records

Modules:

* `sklearn`
  * `decomposition.PCA`
* `seaborn`
* \(optional\) `scipy.statsmodel`

References:

* [HK Legco 2012 - 2016 dataset](https://github.com/hupili/hhba2016-hk-legco-dataset-2012-2016) from Initium Media, 2016
* [HK Legco voting analysis](https://github.com/hupili/legcohk/blob/master/LegCoHK.ipynb) with PCA, an early version, 2014.

---

Following are TBC topics

---

## Week 10 - Machine learning: clustering, classification and regression

**Objective**:

> * \(TODO\）

## Week 12 - Project presentation

**Objective**:

> Be able to efficiently **sell** your work after so many heavy duty hard works!

## Open topics

Those topics may be discussed if there is plenty Q/A time left in certain week. Or, you are welcome to explore those topics via group project.

* Cloud \(AWS\)
* Deep learning



