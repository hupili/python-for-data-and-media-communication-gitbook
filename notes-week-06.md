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
            - [Locating Elements](#locating-elements)
            - [Example: CNN articles scraping](#example-cnn-articles-scraping)
                - [Fundamental: One page](#fundamental-one-page)
                - [Advanced: All pages](#advanced-all-pages)
        - [Splinter](#splinter)
            - [Finding elements](#finding-elements)
                - [Fundamental version: one page](#fundamental-version-one-page)
                - [Advanced version: all pages](#advanced-version-all-pages)
    - [Analyse Network Traces](#analyse-network-traces)
    - [[O] Crawl mobile Apps](#o-crawl-mobile-apps)
    - [[O] Other quick scraping/ crawling tricks](#o-other-quick-scraping-crawling-tricks)
    - [Excercises and Challenges](#excercises-and-challenges)
        - [In-bound marketing and SEO auditing](#in-bound-marketing-and-seo-auditing)
        - [Crawl the legal case of China](#crawl-the-legal-case-of-china)
    - [Related Readings](#related-readings)

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
3. Some webpages have strictly rules for anti-scraping. However, in browser emulation, we simulate users' behaviors, which is more camouflaged and not easy to discover, meaning that the limits is smaller than static scraping like `request`.

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

#### Locating Elements

There are many ways to locate the elements. It's similar to the usage in `requests` method, just a simple `find...` sentence but more diverse.

Selenium provides the following methods to locate elements in a page:

* find_element_by_id
* find_element_by_name
* find_element_by_xpath
* find_element_by_link_text
* find_element_by_partial_link_text
* find_element_by_tag_name
* find_element_by_class_name
* find_element_by_css_selector

To find multiple elements (these methods will return a list):

* find_elements_by_name
* find_elements_by_xpath
* find_elements_by_link_text
* find_elements_by_partial_link_text
* find_elements_by_tag_name
* find_elements_by_class_name
* find_elements_by_css_selector

Except the `XPath` method, others are pretty much like we used before, just check out the html in Chrome Devtools, find the name, class, link, attributes etc. For instruction of the syntax, you can refer this [documentation](https://selenium-python.readthedocs.io/locating-elements.html).

For `XPath` method, XPath uses path expressions to select nodes or node-sets in an XML document. The following are basic expression rules and expression path examples. For a more detailed usage, you can check out this [tutorial](https://www.w3schools.com/xml/xpath_syntax.asp).

Basic expression rules:

| Expression | Description                                                                                           |
|------------|-------------------------------------------------------------------------------------------------------|
| /          | Selects from the root node                                                                            |
| //         | Selects nodes in the document from the current node that match the selection no matter where they are |
| .          | Selects the parent of the current node                                                                |
| @          | Selects attributes                                                                                    |

Path Expression examples:

| Path Expression     | Results                                                                          |
|---------------------|----------------------------------------------------------------------------------|
| /bookstore/book[1]  | Selects the first book element that is the child of the bookstore element.       |
| //book              | Selects all book elements no matter where they are in the document               |
| //@lang             | Selects all attributes that are named lang                                       |
| //title[@lang='en'] | Selects all the title elements that have a "lang" attribute with a value of "en" |

#### Example: CNN articles scraping

The following is the link of results returned by keyword searching of `trade war`. We can scrape those articles title, time and url for further studying. The reason why we need use `selenium` is because the page turning links are embedded javascript codes, which cannot be extracted and use directly in `requests` way. To solve that, we need to interact with the page, and do browser emulation.

https://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war

##### Fundamental: One page

```python
!pip3 install selenium # if you installed before, just ignore
from selenium import webdriver

browser = webdriver.Chrome('/users/xuyucan/chromedriver')
browser.get('http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war')

browser.find_elements_by_xpath("//div[@id='summaryList_mixed']//div[@class='summaryBlock']") #find all articles wrapped in the path of class='summaryBlock'
articles = []
for session in browser.find_elements_by_xpath("//div[@id='summaryList_mixed']//div[@class='summaryBlock']"):
    article = {}
    article['headline'] = session.find_element_by_class_name("cnnHeadline").text #find headline
    article['date'] = session.find_element_by_class_name("cnnDateStamp").text #find date
    url = session.find_element_by_xpath("./div[@class='cnnHeadline']/*[@href]")  #can not directly get the href attributes, it will return 'url' as a selenium object: <selenium.webdriver.remote.webelement.WebElement (session="936716c8251394a2fddad1fa80b64d23", element="0.9458243256600611-16")>
    article['url'] = url.get_attribute('href') #further get attributes from last step
    articles.append(article)
articles
```

Output:

![Articles Output1](assets/selenium-articles-output1.png)

##### Advanced: All pages

```python
from selenium import webdriver
import time #mainly use its time sleep function
browser = webdriver.Chrome('/users/xuyucan/chromedriver')

articles = []
browser.get('http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war')
time.sleep(2) #sleep 2 second for each call action, if it's too frequently with no sleep time, its has high opportunity to be banned from the website.

for i in range (0,10): #change range to enlarge of data scale
    browser.find_elements_by_xpath("//div[@id='summaryList_mixed']//div[@class='summaryBlock']")
    for session in browser.find_elements_by_xpath("//div[@id='summaryList_mixed']//div[@class='summaryBlock']"):
        article = {}
        article['headline'] = session.find_element_by_class_name("cnnHeadline").text #find headline
        article['date'] = session.find_element_by_class_name("cnnDateStamp").text #find date
        url = session.find_element_by_xpath("./div[@class='cnnHeadline']/*[@href]")
        article['url'] = url.get_attribute('href')
        articles.append(article)

#in the following, we need to emulate to click `next button` to turn pages.
#try 1: just click link by default ... 
#next_page = browser.find_element_by_link_text('Next').click()
#error: not clickable. After try several print() in the process,I found that, we need to scroll the window down till we can see the next button. Therefore you can see that selenium browser emulation method is really just like a human behavior.
#try 2: scroll whole body down to the bottom...
#browser.execute_script('window.scrollTo(0, document.body.scrollHeight);')
#error: In some page, the navigation bar has blocked the click button if you scroll down to the bottom
#try 3: (document.body.scrollHeight - int) ...  
#fail: can not be minus, but can be divided.
    browser.execute_script('window.scrollTo(0, document.body.scrollHeight/1.5);') #test several numbers to choose a suitable one
    next_page = browser.find_element_by_link_text('Next')
    next_page.click()
    i = i + 1
    #print(next_page.get_attribute('href')) to see whether its iterated

import pandas as pd #spoiler. pandas is the key module in the next chapter, you can check out chapter 7 for further information.
df = pd.DataFrame(articles) #convert articles into dataframe
df
```

Output:

![Selenium Articles Output2](assets/selenium-articles-output2.png)

### Splinter

Splinter achieves pretty much the same results as Selenium does, though there might be a little difference in syntax. In the following, we will also use `splinter` method to demo the cnn example, you can compare it with `selenium` method, and choose one you like to practice more.

```python
!pip3 install splinter  
from splinter import Browser
import time
url = 'http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war'
browser = Browser('chrome')
browser.visit(url)
time.sleep(2)
```

**Note:** If you get error `Message: 'chromedriver' executable needs to be in PATH.`. The PATH is the working path that your Jupyter Notebook is running. You can check out where it is by the following command, and place the chromedriver you download into this folder.

```python
!echo $PATH
!ls #add the first path returned from last step
!open #add the first path returned from first step
```

![Driver Path](assets/splinter-driver-path.png)

#### Finding elements

Splinter provides 6 methods for finding elements in the page, one for each selector type: `css`, `xpath`, `tag`, `name`, `id`, `value`, `text`. Each of these methods returns a list with the found elements. And you can use index to access each of them in the list. This method is different from `selenium` which provides with finding single element and list of elements. All in all, those two methods are very alike. You can check out [here](https://splinter.readthedocs.io/en/latest/api/driver-and-element-api.html#splinter.driver.DriverAPI.find_by_css) for Splinter doc about finding elements. In this case, we mainly use `find_by_css(css_selector)` method.

##### Fundamental version: one page

```python
!pip3 install splinter  
from splinter import Browser
import time
url = 'http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war'
browser = Browser('chrome')
browser.visit(url)
time.sleep(2)

articles = []
for block in browser.find_by_css('#summaryList_mixed .summaryBlock'):
    article = {}
    h = block.find_by_css('.cnnHeadline a')
    article['headline'] = h.text
    article['url'] = h['href']
    article['date'] = block.find_by_css('span.cnnDateStamp').text
    articles.append(article)

articles
```

Output:

![Splinter articles output1](assets/splinter-articles-output1.png)

How to find its css? When you open chrome devtools, you can find the css in the `style` console by corresponding to the elements in the webpage.

![Find by css](assets/find_by_css.png)

https://github.com/hupili/python-for-data-and-media-communication/tree/master/ww-splinter

##### Advanced version: all pages

```python
url = 'http://money.cnn.com/search/index.html?sortBy=date&primaryType=mixed&search=Search&query=trade%20war'

def get_articles_from_browser(b):
    articles = []
    for block in b.find_by_css('#summaryList_mixed .summaryBlock'):
        article = {}
        h = block.find_by_css('.cnnHeadline a')
        article['headline'] = h.text
        article['url'] = h['href']
        article['date'] = block.find_by_css('span.cnnDateStamp').text
        articles.append(article)
    return articles

# Launch the initial page#
browser = Browser('chrome')
browser.visit(url)
time.sleep(2)

all_page_articles  = []
for i in range(50): #scrape 50 pages
    time.sleep(0.5)
    try:
        new_articles = get_articles_from_browser(browser)
        all_page_articles.extend(new_articles)
        browser.execute_script('window.scrollTo(0, document.body.scrollHeight/1.5);') #scroll down
        next_buttons = browser.find_by_css('.pagingLinks li.ends.next')
        next_buttons[0].click() #splinter find_by return a list, therefore we need use index0 to access the next_button.
    except Exception as e:
        print(e)
        print('Error on page %s' % i)

import pandas as pd
df = pd.DataFrame(all_page_articles)
df
```

Output: There will be 500 rows.

![Splinter Articles Output2](assets/splinter-articles-output2.png)

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

## Related Readings

- Dynamic loading and crawling exmaple: [libguides example](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/scraper-examples/Libguides.ipynb)
- Social media crawling example: [Scrape a luxury brand with keyword in Weibo](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/ww-selenium/Weibo.ipynb)
- Dynamic page crawling, with a matter of parsing page content: [Timeout](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/ww-splinter/timeout.com.ipynb)
- Dynamic crawling a static page with a matter of pagination: [Amazon Books](https://github.com/hupili/python-for-data-and-media-communication/blob/a4922340f55c4565fff19979f77862605ac19f22/ww-splinter/Amazon%20books.ipynb)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)