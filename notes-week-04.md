# Week 04 Web Scraping


#1. Jupyter notebook
* 1.As we have downloaded python2 and python3, there are some conflicts to run some programs when we import modules.
* 2.We can debug step by step.It is convenient when we are writing a complicated coding.

So it is suggested to enter virtual environment before using Jupyter notebook.

### Instruction: 
https://hupili.gitbooks.io/python-for-data-and-media-communication/content/module-jupyter.html

* Then you will see a page http://localhost:8888/tree. (As long as you are in the virtual environment, you can go to this link to write code.)
* A directory named 'venv' is on your desktop now. The files you put here can be run in the virtual environment by jupyter.

### Tips of usage:
##### Q1: How to quit the last steps's situation?
![](/assets/Screen Shot 2018-02-13 at 1.03.46 pm.png)

A:
The answer is in the picture: control+C. ( Pay attention to the text. )Then you will get the following picture.Please input `y` in 5 seconds.
![](/assets/Screen Shot 2018-02-13 at 1.06.35 pm.png)

##### Q2:How to quit from virtual environment?
![](/assets/Screen Shot 2018-02-13 at 1.09.51 pm.png)

A: input `deactivate`


# 2.Scrape
### The process of search engines(like Baidu)'s work
1. Crawl web pages
2. Store those web pages
3. Build reverse index,which means making a relationship between the keyword and web page.
4. Extract page-level features

### html JS css
**![](/assets/Screen Shot 2018-02-13 at 1.12.33 pm.png)**
* HTML is a machine language of web page. Writing something in HTML means to create a web page.It is a structure of diverse tags. Those tags are in pairs,with open tag and closing tag. 
* css and JS are other languages, which is used to describe the style of the web page,such as the characters' style and colour.

### Chrome Develop Console
* It is suggested to use 'Chrome' as our browser.
* In Chrome, `option+command+i` to open the Chrome develop console.
* Click the upper left corner of the console,![](/assets/Screen Shot 2018-02-13 at 1.15.32 pm.png)and you will find that by moving the mouse in the web, you can see the part in console.
* eg:**![](/assets/Screen Shot 2018-02-13 at 1.16.25 pm.png)**

### Write the scrape
#### 1.install modules in terminal
```
pip3 install --user requests
pip3 install --user bs4
pip3 install --user lxml
```
#### 2.start venv
#### 3.open a new file
**![](/assets/Screen Shot 2018-02-13 at 1.17.50 pm.png)**
* `shift+return` to run the code.



# Class Review
##Tips: tab & type & help & print
There are some useful tips for you.

* tab
If we input the `mypage.t`, then `tab`, we will find there are other commands(functions),including tag_name, text and so on.

2.  `type` to check the object. It is very useful when we write complicated codings.

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

*  `help(str.strip)` to know the details.

* `print` step by step to check where is the error.
(In Jupyter, you can just input the variables without the function of print.)


#### import modules
```
import requests
import bs4
import csv
```
* `requests` is a module containing diverse functions relating to the web page.
* `bs4` is the abbreviation of BeautifulSoup4.It is used to analyse web page.


#### requests + .text
```
r = requests.get('http://initiumlab.com/blog/20170329-trump-and-ivanka/'
r.text
```
It can be wrote in one line.
> ```
r = requests.get('http://initiumlab.com/blog/20170329-trump-and-ivanka/').text
```

* Store the web as `r`, `get` means try to get response of that web page.
`text` means to show the text of the web page.

#### BeautifulSoup
```
from bs4 import BeautifulSoup
```
* `BeautifulSoup` is to extract the web's content.
* It relies on certain engine to analyse `lxml` is one of the engine. By default, it will choose the best engine.

* Warning is not an error. So no need to worry at this stage.

#### find + strip() to get title
* Open the console, and you can find that title is between the tag"h1".

```
myh1 = mypage.find('h1')
mytitle = myh1.text
mytitle.strip()
```
* By moving the mouse, we can see in html that title is between the tag of `h1`.Then we use `find` to find what we want.Use `text` to extract the text.
* There are some meaningless word we don't need.`strip()`means delete the meaningless coding.
* You can `help(str.strip)` to see the usage of strip.

#### get date
```
mydate = mypage.find('time').text.strip()
```

#### get author (Important) 
**Comprehensive first, then exclusive. **

#####Try 1:fail
* If you input:` myauthor = mypage.find('span') `You will find:
>![](/assets/Screen Shot 2018-02-13 at 2.17.14 pm.png)

* It is not what we want,as there are too many 'span'.
So check how many span there, and find the difference between those tags.
* `command+f` to open the search bar in console,and input `span`.You can see, there are more than 2 'span'.

* if you input:`myspans = mypage.find_all('span')`, you can find more details.
>![](/assets/Screen Shot 2018-02-13 at 2.17.24 pm.png)

* In the above command, 'myspans' is a list, which contains many different span tags. We use [] to extract the members in the list. 
`myspans[0]` means the first one in the list.
`myspans[1]` means the second one in the list. And so on.

#####Try 2:succeed
* In the HTML, we can find that authors upper tag is `td`. But there are too many td. And it is difficult to be specific.
![](/assets/Screen Shot 2018-02-13 at 2.41.09 pm.png)
* Then try to locate the upper file ' tr class="post__authors" ':
   
   `len(mypage.find_all('tr'))`
    >![](/assets/Screen Shot 2018-02-13 at 3.06.54 pm.png)
   
* `find_all` means output all the items it finds.
* `find` means only output the first one. 

* There are 5 tr. So we want to narrow the area to search the 'span'.`find(a,b)` attrs= attributs. You can add more detailed information about tr, which helps to locate the tr.
   ```
   mytr = mypage.find('tr', attrs={'class': 'post__authors'})
   mytr
   ```
   > ![](/assets/Screen Shot 2018-02-13 at 2.46.30 pm.png) 

* `mytr.find_all('span')`to check what we have got.
>![](/assets/Screen Shot 2018-02-13 at 3.01.51 pm.png)

##### Requests
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 

##### Requests




### da f




