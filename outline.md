# Course Outline

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

Python language introduction:

* Variables and assignment
* Basic data types: int, float, str
* Arithmetic:
  * `+`, `-`, `*`, `/`, `//`, `%`, `**`
  * `math` , `numpy` \(may need `pip`\)
* Use functions and modules: `import`; `.` notation; `()` notation.
* Common modules
  * `sys`
  * `numpy`, `scipy`
  * `str.*` functions
  * `random`

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

> * Master the composite data type \[\] and {} in Python
> * Master the control logics in Python
> * Understand Python engineering

Python language:

* `help`
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

* Chapter 4, 5, 6 of [official Python 2 tutorial](https://docs.python.org/2/tutorial/)

## Week 4 - Web Scraping

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


## Week 5 - JSON and API

**Objective**:

> * Reinforce the knowledge of scraper. Able to analyse and scrape normal web pages
> * Understand API/ JSON and can retrieve data from online databases \(twitter, GitHub, weibo, douban, ...\)

Modules:

* Handle HTTP request/ response: `requests`
* Serialiser: `json`

Challenges:

* Taiwan had an earthquake in early Feb. Let's discuss this issue:
   * Search for the earthquake instances around Taiwan in recent 100 years and analyse the occurrences of earthquakes. You can refer to the same database used [here](https://dnnsociety.org/2017/09/02/map-of-sichuan-earthquake-in-d3/)
   * Search on Twitter and collect user's discussions about this topic. See if there is any findings. You can approach from the human interface [here](https://twitter.com/search?q=%23%E5%8F%B0%E6%B9%BE%E5%9C%B0%E9%9C%87) (hard mode) or use [python-twitter](https://github.com/bear/python-twitter) module (need to register developer and obtain API key).
* Retrieve and analyse the recent movie. Douban's API will be helpful here.
   * [API sample for Recent movies](https://api.douban.com/v2/movie/in_theaters)
   * [API sample for movie details](https://api.douban.com/v2/movie/subject/26942674)


-------

Following are TBC topics 

-------


## Week 6 - 1-D and 2-D analysis

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
* central tendency and spread of data

References:

* First two chapters (i.e. before "3D") of the article [The Art of Effective Visualization of Multi-dimensional Data](https://towardsdatascience.com/the-art-of-effective-visualization-of-multi-dimensional-data-6c7202990c57) by Dipanjan Sarkar 

## Week 7 - Text analysis

Related cases:

* [Quartz's analysis](https://qz.com/962718/we-analyzed-every-modern-love-column-from-the-past-10-years-heres-what-we-learned-about-love/) of New York Times's column of "Modern Love"
* Prof. Qian Gang's famous [analysis of texts in political communication](https://www.bloomberg.com/news/articles/2017-07-18/party-of-one-newspaper-mentions-show-xi-s-dominance-of-china).

## Week 8 - Time series

## Week 9 - 2-Dimensional analysis

**Objective**:

> * Understand correlation and causality
> * Can conduct visual \(explorative\) analysis of correlation
> * Can interpret common statistic quantities

Modules:

* `seaborn`
* `scipy.statsmodel`

## Week 9 - High-dimensional analysis

**Objective**:

> * Dimensionality reduction

Challenge:

1. Explore the HK Legco voting records

## Week 10 - Machine learning: clustering, classification and regression

**Objective**:

> * \(TODO\)

## Week 11 - Graph theory and social network analysis

**Objective**:

> * \(TODO\)

## Week 12 - Project presentation

**Objective**:

> Be able to efficiently **sell** your work after so many heavy duty hard works!

## Open topics

Those topics may be discussed if there is plenty Q/A time left in certain week. Or, you are welcome to explore those topics via group project.

* Cloud \(AWS\)
* Deep learning



