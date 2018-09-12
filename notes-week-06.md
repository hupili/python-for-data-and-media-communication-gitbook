# Week 06 - Advanced scraping: browser emulation, anti-crawler and other nitty gritty

<div id="toc">

<!-- TOC -->

- [Week 06 - Advanced scraping: browser emulation, anti-crawler and other nitty gritty](#week-06---advanced-scraping-browser-emulation-anti-crawler-and-other-nitty-gritty)
    - [Anti-crawling](#anti-crawling)
        - [User agent](#user-agent)
        - [Rate throttling](#rate-throttling)
    - [Common issues](#common-issues)
        - [Encoding](#encoding)
    - [Browser emulation](#browser-emulation)
        - [Why use Browser Emulation](#why-use-browser-emulation)
        - [Limitation](#limitation)
        - [Selenium](#selenium)
            - [Downloading Python bindings for Selenium](#downloading-python-bindings-for-selenium)
            - [Drivers](#drivers)
            - [Navigating](#navigating)
        - [splinter](#splinter)
    - [Analyse Network Traces](#analyse-network-traces)
    - [[O] Crawl mobile Apps](#o-crawl-mobile-apps)
    - [[O] Other quick scraping/ crawling tricks](#o-other-quick-scraping-crawling-tricks)
    - [Excercises and Challenges](#excercises-and-challenges)
        - [In-bound marketing and SEO auditing](#in-bound-marketing-and-seo-auditing)
        - [Crawl the legal case of China](#crawl-the-legal-case-of-china)

<!-- /TOC -->

</div>

## Anti-crawling

### User agent

### Rate throttling

* Limit by IP
* Limit by cookie/ access token

## Common issues

### Encoding

[51job.com example](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/51job.com.ipynb)

## Browser emulation

Primarily, Browser emulation or browser automation is used for automating web applications for testing purpose. Like when you build your web application, you want to simulate how many users your server can handle, and how the users act when they look into your website, how they open page, click, navigate and read the the page content.

But browser emulation is certainly not limited to just that. For our course, we mainly use it to manipulate the
browser, to interactively communicate with the website, locate the information and get the data we want.

### Why use Browser Emulation

1. Some of complicated website can't be directly scraped by static method. For example, some elements, especially page turning buttons/links in the webpage have embedded javascript codes, which need users certain actions to further loading the content.
2. Browser Emulation way can handle some complicated scraping work like ones that need you login.
3. Some webpages have strictly rules for anti-scraping. However, in browser emulation, we simulate users' behaviors, which is more camouflaged and not easy to discover, meaning that the limits is smaller than static scraping like `request`.

In our course, we mainly introduce two libraries - `Selenium` and `Splinter` for browser emulation and dynamic scraping. Those packages are wildly used in this field. And their documentations are easy to read.

### Limitation

Each time, it need to load all the content of the webpage, the crawling speed is slow, therefore not suitable for scraping cases with a large load of data.

### Selenium

Selenium is a set of different software tools, each with a different approach to supporting browser automation. These tools are highly flexible, allowing many options for locating and manipulating elements within a browser, the key tool we will use is Selenium Python bindings.

> Selenium Python bindings provides a simple API to write functional/acceptance tests using Selenium WebDriver. Through Selenium Python API you can access all functionalities of Selenium WebDriver in an intuitive way.

You can visit [here](https://selenium-python.readthedocs.io/) to learn how to use those functions by yourself. In the following example, we will use CNN articles scraping case to elaborate the basic functions of it, and how to scrape a webpage that need our interaction.

#### Downloading Python bindings for Selenium

```python
!pip install selenium    #in Jupyter Notebook
```

```python
from selenium import webdriver #import
```

#### Drivers

Selenium requires a driver to interface with the chosen browser. Chrome, for example, requires Chromedriver, which needs to be installed before the below examples can be run.

you can download different drivers for supported browsers in the following links:

| Supported Browsers | Download Links                                                 |
|--------------------|----------------------------------------------------------------|
| Chrome             | https://sites.google.com/a/chromium.org/chromedriver/downloads |
| Firefox            | https://github.com/mozilla/geckodriver/releases                |
| Safari             | https://webkit.org/blog/6900/webdriver-support-in-safari-10/   |

For windows users: please refer to [here](https://selenium-python.readthedocs.io/installation.html#detailed-instructions-for-windows-users) for instruction of download.

**Note: Make sure it’s in your PATH, e. g. place it in /usr/bin or /usr/local/bin.** If it's not in the PATH, when you initiate the Chromedriver, it will raise error `Message: 'chromedriver' executable needs to be in PATH.`

You can also solve this problem by specify the path of the Chromedriver, for example, if you just download in `Users/username/...`. You can still initiate it in this way, for my example:

```python
browser = webdriver.Chrome() #default to initiate webdriver, you can assign it with driver or browser or other things you like. If raise error, you can specify the file path like the following.
browser = webdriver.Chrome('/users/xuyucan/chromedriver')
```

#### Navigating

You can doing a lot of interactive things with the webpage with help of the selenium, like navigating to a link, searching, scrolling, clicking etc. In the following example, we will demo the basic usage of navigating.

```python
from selenium import webdriver
browser = webdriver.Chrome('/users/xuyucan/chromedriver') #initiate webdriver
browser.get('http://google.com/') #visit to google page
element = browser.find_element_by_name("q") #Find the search box
element.send_keys("github python for data and media communication gitbook") #search our openbook
element.submit() #submit search action
# you will find the webpage will automaticlly return the results you search
link = browser.find_element_by_link_text('GitHub - hupili/python-for-data-and-media-communication-gitbook') #find our tutorial
link.click() #click the link, enter our tutorial
browser.execute_script("window.scrollTo(0,1200);") #scroll in the page, window.scrollTo(x,y), x means horizontal, y means vertical
notes_links = browser.find_element_by_link_text('notes-week-06.md') #find link of notes 6
notes_links.click() #click into notes 6
#browser.close()
```

https://github.com/hupili/python-for-data-and-media-communication/tree/a4922340f55c4565fff19979f77862605ac19f22/ww-selenium

[libguides example](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/Libguides.ipynb)

### splinter

https://github.com/hupili/python-for-data-and-media-communication/tree/master/ww-splinter

## Analyse Network Traces

Open "Google Chrome Developer Console" by `command+option+i`. Check out the "Network" tab and use "XHR" filter to find potential packages. We are usually interested in `json` files or `xml` files sent over the line. Most dynamic web pages have predictable / enumerable internal API -- use HTTP request to get certain `json`/ `xml` files.

Some websites render HTML at the backend and send them to the frontend in a dynamic way. You find the URL in address bar stays the same but the content is changed. You can also find the HTML files and their **real URL** via developer console. One such example is [xiachufang.com scraper](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/xiachufang.com.ipynb).

## [O] Crawl mobile Apps

**TODO**

"Charles proxy", "mitmproxy"

## [O] Other quick scraping/ crawling tricks

In our class, we show you the very basic steps of scraping so that you know how it things happen in a sequential way. However, you don't have write codes for everything from scratch in real practice. People already made numerous tools and libraries that can help you do certain tasks quickly. Here are some examples related with course (Shell/ Python) for those who are interested:

- Type `wget -r {url}`, where `{url}` is the URL of the website you want to crawl. After running this command, you can find all the web pages and their dependent resources are on your computer. You can fine tune the parameters to limit crawling scope, like number of hops or types of files. Use `man wget` to find out more.
- There are many shell commands which can be combined to perform efficient text processing. [This article](https://github.com/hupili/agile-ir/blob/master/cases/case2-crawl-by-url-filling/index.md) shows how one can combine a few Shell commands to quickly download the Shakespeare works.
- [This repo](https://github.com/hupili/agile-ir/blob/master/cases/case2-crawl-by-url-filling/index.md), originally a workshop given on PyConHK in 2015, shows you some handy tools and libraries in Python that allow one to scrape more with less codes. For example, you can use `readability` to extract the main body of an HTML page, without bothering with its page structure. For readers with frontend development background, `pyquery` is a handy library to allow you write jQuery like selectors to access HTML elements. `scraply` is a machine learning based library that can learn the labelled crawling target and generate corresponding rules; The user only needs to tell `scraply` what to crawl, instead of how to crawl.

## Excercises and Challenges

### In-bound marketing and SEO auditing

Search Engine Optimization (SEO) is one common technique a digital marketer needs to master. Suppose you have led a team to conduct the optimization. Now it is time to audit the optimization result. One of the key function is to build scraper which can:

* Input 1 is a search query, i.e. some keywords
* Input 2 is a set of URLs from your own website
* Output the ranks of each URL in the search result list

### Crawl the legal case of China

<http://wenshu.court.gov.cn> collects the legal cases in China. It supports advanced search options. One can emulate browser to download relevant documents on a certain area. Please try:

- Give a keyword as input.
- Download the documents of the first page, e.g. `.docx` files, onto local disk.
- Organise an index of those documents into a `CSV` which may include "title", "court", "date", "document-path", and other fields if you deem useful.