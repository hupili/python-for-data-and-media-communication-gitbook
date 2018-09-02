# Week 05 - Get semi-structured data: Web scraping

<div id="toc">

<!-- TOC -->

- [Week 05 - Get semi-structured data: Web scraping](#week-05---get-semi-structured-data-web-scraping)
    - [Jupyter notebook](#jupyter-notebook)
        - [Install modules in terminal](#install-modules-in-terminal)
        - [Start venv](#start-venv)
        - [Tips of usage](#tips-of-usage)
            - [Q1: How to quit the last steps's situation?](#q1-how-to-quit-the-last-stepss-situation)
            - [Q2:How to quit from virtual environment?](#q2how-to-quit-from-virtual-environment)
        - [Tab & type & help & print](#tab--type--help--print)
        - [Open a new file](#open-a-new-file)
    - [Knowledge about HTML](#knowledge-about-html)
        - [The process of search engines\(like Baidu\)'s work](#the-process-of-search-engines\like-baidu\s-work)
        - [Html JS css](#html-js-css)
        - [Chrome Develop Console](#chrome-develop-console)
    - [Scraper](#scraper)
        - [Import modules](#import-modules)
        - [Requests + .text](#requests--text)
        - [BeautifulSoup](#beautifulsoup)
        - [Find + strip\(\) to get title](#find--strip\\-to-get-title)
        - [Get date](#get-date)

<!-- /TOC -->

</div>

## Jupyter notebook

* 1.As we have downloaded python2 and python3, there are some conflicts to run some programs when we import modules.
* 2.We can debug step by step.It is convenient when we are writing a complicated coding.

So it is suggested to enter virtual environment before using Jupyter notebook.

### Install modules in terminal

```
pip3 install --user requests
pip3 install --user bs4
pip3 install --user lxml
```

### Start venv
[https://hupili.gitbooks.io/python-for-data-and-media-communication/content/module-jupyter.html](https://hupili.gitbooks.io/python-for-data-and-media-communication/content/module-jupyter.html)

* Then you will see a page [http://localhost:8888/tree](http://localhost:8888/tree). \(As long as you are in the virtual environment, you can go to this link to write code.\)
* A directory named 'venv' is on your desktop now. The files you put here can be run in the virtual environment by jupyter.

### Tips of usage

#### Q1: How to quit the last steps's situation?

![](assets/to-do-uncategorized-screenshots/no1.png)

A:
The answer is in the picture: control+C. \( Pay attention to the text. \)Then you will get the following picture.Please input `y` in 5 seconds.

![](assets/to-do-uncategorized-screenshots/no9.png)

#### Q2:How to quit from virtual environment?
![](assets/to-do-uncategorized-screenshots/no2.png)

A: input `deactivate`

### Tab & type & help & print
There are some useful tips for you.

* tab
If we input the `mypage.t`, then `tab`, we will find there are other commands\(functions\),including tag\_name, text and so on.

* `type` to check the object. It is very useful when we write complicated codings.
eg:
```
a=1
type(a)
b="hello"
type(b)
```
You will get:
```
int
str
```

* `help(str.strip)` to know the details.

* `print` step by step to check where is the error.
\(In Jupyter, you can just input the variables without the function of print.\)

### Open a new file
![](assets/to-do-uncategorized-screenshots/no3.png)
* `shift+return` to run the code.


## Knowledge about HTML

### The process of search engines\(like Baidu\)'s work

1. Crawl web pages
2. Store those web pages
3. Build reverse index,which means making a relationship between the keyword and web page.
4. Extract page-level features

### Html JS css
![](assets/to-do-uncategorized-screenshots/no4.png)

* HTML is a machine language of web page. Writing something in HTML means to create a web page.It is a structure of diverse tags. Those tags are in pairs,with open tag and closing tag.
* css and JS are other languages, which is used to describe the style of the web page,such as the characters' style and colour.

### Chrome Develop Console

* It is suggested to use 'Chrome' as our browser.
* In Chrome, `option+command+i` to open the Chrome develop console.
* Click the upper left corner of the console, and you will find that by moving the mouse in the web, you can see the part in console.
* eg:![](assets/to-do-uncategorized-screenshots/no5.png)


## Scraper

### Import modules
```
import requests
import bs4
import csv
```
* `requests` is a module containing diverse functions relating to the web page.

* `bs4` is the abbreviation of BeautifulSoup4.It is used to analyse web page.

### Requests + .text
```
r = requests.get('http://initiumlab.com/blog/20170329-trump-and-ivanka/'
r.text
```
It can be wrote in one line.

`r = requests.get('http://initiumlab.com/blog/20170329-trump-and-ivanka/').text`

* Store the web as `r`, `get` means try to get response of that web page.

* `text` means to show the text of the web page.

### BeautifulSoup
```
from bs4 import BeautifulSoup
mypage = BeautifulSoup(r.text)
```
* `BeautifulSoup` is to extract the web's content.
It relies on certain engine to analyse. `lxml` is one of the engine. By default, it will choose the best engine.

* Warning is not an error. So no need to worry at this stage.


### Find + strip\(\) to get title
>`h1 class="post__title" itemprop="name headline"> 特朗普父女推特解密</h1
`

* Open the console, by moving the mouse you can find title is in `<h1........</h1>`.(see the above 'html' part.)

```
myh1 = mypage.find('h1')
mytitle = myh1.text
mytitle.strip()
```

* `find` to find what we want, and output the first item.
* `find_all` means output all we find. 
* `strip()`means delete the meaningless coding.
* You can `help(str.strip)` to see the usage of strip.

### Get date
>```
<time itemprop="dateCreated" datetime="2017-03-29T....." content="2017-03-29">
                  2017-03-29
                </time>
```

```
mydate = mypage.find('time').text.strip()
```

### Get author \(Important\)
##### Try 1:fail
`myauthor = mypage.find('span')`
![](assets/to-do-uncategorized-screenshots/no6.png)

* It is not what we want, as there are too many 'span'.So check how many span there, and find the difference between those tags. `command+f` to open the search bar in console,and input 'span'.You can see, there are more than 2 'span'.

`myspans = mypage.find_all('span')`
![](assets/to-do-uncategorized-screenshots/no7.png)
* `find_all` means output all the items it finds.
* `find` means only output the first one.

* 'myspans' is a list. 
 `myspans[0]`means extract the first one in the list.
 `myspans[1]`means extract the second one in the list.

##### Try 2:succeed to find all the authors

![](assets/to-do-uncategorized-screenshots/no8.png)

* In the HTML, we can find that authors upper tag is 'td'. But there are too many td. And it is difficult to be specific.

* As 'tr' has class, which means more specific than 'td', so try to locate the more upper file: 'tr':

`len(mypage.find_all('tr')`
>`5`

* There are 5 tr. We have to narrow the area to search the 'span'.

`mytr = mypage.find('tr', attrs={'class': 'post__authors'})`

* `attrs`= attributes. You can add more detailed information about tr, which helps to locate the tr. 


`mytr` 
```
<tr class="post__authors">
<td>.......</td>
<td>
<span>Li Yiming</span>
<span>Li Yuqiong</span>
</td>
</tr>
```

`mytr.find_all('span')`
`[<span>Li Yiming</span>, <span>Li Yuqiong</span>]`


### Try to output those authors.
```
authors = []
for myspan in mytr.find_all('span'):
    authors.append(myspan.text)
```

* Create a new empty list called 'authors'. Then add the information in it.

* `list1.append()`means add the item into the list1.

```
article = {
    'title': mytitle,
    'authors': authors,
    'date': mydate
}
```
* `{}` is a dictionary.The left of the colon is the key, or name. The right of the colon is the value of the key.


### Def to scraper more articles                                                                       
```
def scrape_one_page(url):
    r = requests.get(url).text
    mypage = BeautifulSoup(r,'lxml')
    mytitle = mypage.find('h1').text.strip()
    mydate = mypage.find('time').text.strip()
    mytr = mypage.find('tr', attrs={'class': 'post__authors'})
    authors = []
    for myspan in mytr.find('span'):
        authors.append(myspan)
    article = {
        'title': mytitle,
        'authors': authors,
        'date': mydate
    }
    return article
```
* Create a function for future.

* Following is an example of the function`scrape_one_page` 's usage:
`print(scrape_one_page('http://initiumlab.com/blog/20170401-data-news/'))`


### "For" loop to scraper more articles
```
urls = [
    'http://initiumlab.com/blog/20170407-open-data-hk/',
    'http://initiumlab.com/blog/20170401-data-news/',
    'http://initiumlab.com/blog/20170329-trump-and-ivanka/'
]

articles= []
for url in urls:
    article= scrape_one_page(url)
    articles.append(article)
print(articles)
```
* Input a list of urls. Create an empty list called articles. For every urls' meaningful information, use the `scrape_one_page` function to extract.Then add those into the articles.


### Write .csv
```
with open('eggs.csv', 'w') as f:
    writer= csv.writer(f)
    for article in articles:
        writer.writerow([
            article['authors'],
            article['date'],
            article['title']
        ])
```
* We can save those infornation with in different ways. `csv` is one of the types which can be easily opened and read.

* `with open ('eggs.cdv','w') as f:` means create a file called 'eggs.csv'. 'w' is one of the way to open it, which is usually in default. 'as f' means that when we write f, it equals to open the file.

* `csv.writer` means edit a csv file.

* `writer.writerow([])` means add information in row. It can be wrote like this `s.writerow(['Spam', '1', '2', '3'])`


## [O] Crawler

A crawler is essentially a super module of scraper. When talking about "scraper", we mainly focus on retrieving and parsing a single document, be it an HTML, PDF, or image. Most of the time, we deal with HTML documents. "crawler" can follow the hyperlinks in a document, scrape documents pointed by those hyperlinks, and find new hyperlinks -- thus crawling.

Crawler is an essential building block for a search engine. Think of how Google and Baidu can reach the whole WWW-world without knowing where it is, or how large it is. It all starts by giving a set of "seed pages", and let the crawler expand the horizon by following the links on the pages.

### Crawler is not necessary in most of your cases

As a beginner of programmatic data collection, you often find crawler is non-necessary. The major reason is that in our use case, the "crawling zone" is bounded, namely there is a systematic way to specify where to crawl and how to crawl. In such scenario, you only need to focus on "scraper" part. Once you can handle one page, you can systematically generate other pages, or rules/ operation sequences to find other pages. Here are some examples of common generators:

- Find pages to scrape from a "hub page" -- e.g. find links to news articles from a list page, and then scrape each page from the list.
- Manipuate page id parameter in URL -- e.g. a forum/ a Wordpress blog site.
- Start from a seed page and continuously click "Next Page" -- e.g. search engine results. [notes-week-06.md](notes-week-06.md) will explain in details how to emulate browser in a programmatic way.

### scrapy

[scrapy](https://scrapy.org/) is the most commonly used crawler framework in Python. Given this framework, you only need to write a `parse` function, which basically does two jobs:

1. Emit "data item" found in the current page
2. Emit "page item" that `scrapy` framework needs to follow.

Note the keyword `yield` when you try this framework. This is called "Generator" -- a common construct in most modern programming languages. You have already used generator for many times throughout this class. We don't mention it to avoid possible confusion. Interested readers can find a simple tutorial [here](https://www.liaoxuefeng.com/wikipage/00138681965108490cb4c13182e472f8d87830f13be6e88000).

### scrapy-cluster

[scrapy-cluster](https://github.com/istresearch/scrapy-cluster) is a distributed crawling framework, that uses [Docker](https://www.docker.com/) container technology to easily and horizontally scale out with your task size. It is a super module of `scrapy`. The layering is a follows:

1. `parse()` function in `scrapy` -- This is essentially a "Scraper" -- single page, parsing
2. `scrapy` -- This is essentially **one** "Crawler" -- The emited data items and page items are within one crawling topic.
3. `scrapy-cluster` -- This is essentially a (distributed) cluster of **multiple** Crawlers. Those crawlers can have different topics, priorities, scheduling options, etc.

## Exercises and Challenges

Some scrapers and the output dataset from our past students:

* [HK Carpark price data](https://github.com/XIAO-Chao/hkbu-big-data-media/tree/master/homework2)
* [Qidian](https://github.com/DaisyZhongDai/hkbu-big-data-media/tree/master/homework2)
* [CTrip scenic point data](https://github.com/marla322/hkbu-big-data-media/tree/master/HW2)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)