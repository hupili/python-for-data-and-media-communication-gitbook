# Week 10: Text data

<div id="toc">

<!-- TOC -->

- [Week 10: Text data](#week-10-text-data)
    - [Text processing](#text-processing)
        - [String functions recap](#string-functions-recap)
        - [encode and decode](#encode-and-decode)
        - [String matching and Regular Expression (RegEx)](#string-matching-and-regular-expression-regex)
            - [Bonus: Text substitution](#bonus-text-substitution)
            - [RegEx in shell](#regex-in-shell)
    - [Word frequency](#word-frequency)
        - [Visualize word frequency](#visualize-word-frequency)
            - [with bar chart](#with-bar-chart)
            - [with tag cloud](#with-tag-cloud)
    - [Word segmentation](#word-segmentation)
        - [How to add new terms to the wordseg dictionary](#how-to-add-new-terms-to-the-wordseg-dictionary)
        - [How to adjust term weight in the wordseg dictionary](#how-to-adjust-term-weight-in-the-wordseg-dictionary)
    - [Bonus: TF.IDF](#bonus-tfidf)
    - [Bonus: Topic model](#bonus-topic-model)
    - [Bonus: Sentiment analysis](#bonus-sentiment-analysis)
    - [Bonus: word2vec](#bonus-word2vec)
    - [Text](#text)
    - [Check the information in terminal](#check-the-information-in-terminal)
    - [Simple steps to start Jupyter notebook in terminal](#simple-steps-to-start-jupyter-notebook-in-terminal)
        - [4 Steps](#4-steps)
        - [New](#new)
        - [Install modules in jupyter](#install-modules-in-jupyter)
    - [For loop](#for-loop)
        - [Range\(\)](#range\\)
        - [Append VS Extend](#append-vs-extend)
    - [Verify every step -splinter python](#verify-every-step--splinter-python)
        - [Fail to save content](#fail-to-save-content)
        - [Resolution splinter](#resolution-splinter)
        - [Save time](#save-time)
        - [Calculate the frequent terms](#calculate-the-frequent-terms)
            - [Get text](#get-text)
            - [Word count](#word-count)
            - [Stop word](#stop-word)
            - [Word cloud](#word-cloud)
            - [Jieba](#jieba)
            - [Pandas plotting](#pandas-plotting)
    - [Time series](#time-series)
    - [Geographical data](#geographical-data)

<!-- /TOC -->

</div>

<!-- NOTE: new outline begin -->

## Text processing

### String functions recap

Outline:

- split
- replace
- join
- format
- find
- slicing (`:`)


Case 1: Scraping Initiumlab articles' urls, which we used as an example in [chapter 5](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-05.md#scrape-all-articles-of-one-page)

* Using `split + slice + format`

When scrape certain elements in webpage, the elements sometimes are folded or shorted, we need to split to different parts, use list slicing to get the part we want and re-format the strings we want.  For example:

![Initiumlab articles](assets/initiumlab-articles.png)

the article url we get is `"../../../blog/20160730-mediawiki-wiki-knowledge-management-system/"`, but what we expect is this`"http://initiumlab.com/blog/20160730-mediawiki-wiki-knowledge-management-system/"`. We can format the new string by the following method.

```python
string = "../../../blog/20160730-mediawiki-wiki-knowledge-management-system/"
s = string.split('/blog')
#s
s1 = s[-1]
#s1
s2='{0}{1}'.format('http://initiumlab.com',s1)
#s2
```

Case 2: Check out certain words in a string, replace certain words and separate the words with some notations.

* Using `find + replace + join`

In certain occasion, we need to check out whether there is one word in the string, and need to replace the word.

```python
str = "this is string example....this is the string we will test, is it"
str.find('string')
#output: 8, the position of the first characters
str.find('python')
#output: -1, it will return -1 if there is no this word in the string
str.replace("is", "was") #replace all
#output: 'thwas was string example....thwas was the string we will test, was it'
str.replace("is", "was", 3) #replace first 3
#output: 'thwas was string example....thwas is the string we will test, is it'
s3 = str.split(' ')
'|'.join(s3) #you can add different things in the string
#output: 'this|is|string|example....this|is|the|string|we|will|test,|is|it'
```

Case 3: Apply a function onto every element of the dataframe - Check out the most frequent names in the tweets text

* Using `str.lower()` + `in` operator + `pandas.apply()`

Exercise with the Tweeter Troll Data, you can download [here](https://raw.githubusercontent.com/hupili/python-for-data-and-media-communication/master/text-analysis/regular_reader_tweets.csv).

1. Check out times that certain name appears in the dataset.

```python
#import and check out the dataset
import pandas as pd
df = pd.read_csv('regular_reader_tweets.csv')
#len(df)
#df.sample(10)

#check certain user name in the text
def check_name(x):
    return 'ten_gop' in str(x).lower()
df['text'].apply(check_name).value_counts()
#return results true only
#df['text'].apply[check_names].value_counts()[True]
```

Output:

```text
False    202991
True        491
Name: text, dtype: int64
```

2. Check out the most common names in the tweet text.

```python
# filter out all the user and reset to dataframe
s_user = df['user_key'].value_counts()
df_users = s_user.reset_index()
#df_users

# count_retweeted_number of all the users with apply function
def count_retweeted_number(name):
    def check_name(x):
        return name in str(x).lower()
    return df['text'].apply(check_name).value_counts().get(True, 0)

df_users['count'] = df_users['index'].apply(count_retweeted_number)
df_users.sort_values(by='count', ascending=False)
```

Output:

![Checkout most common names](assets/checkout-most-common-names.png)

### encode and decode

- UTF-8
- GBK

<!-- TODO -->

### String matching and Regular Expression (RegEx)

The `.find()` and `in` operator on `str` has limited matching capability. They can only perform precise matching. What if we want to do fuzzy matching? Common siutations:

1. Find all the user names from the Twitter message. i.e. those look like `@xxxx `, i.e. start with `@` and end with ` ` (blank).
2. Find all the phone numbers from a paragraph of texts.

RegEx can solve those problems in a very concise way.

<!-- TODO: solve above two problems using RegEx -->

#### Bonus: Text substitution

RegEx can let you substitute some matching parts. It even allows to interpolate variables using values from matching part.

#### RegEx in shell

Following commands can be used to perform RegEx operation. Those commands sometimes can make your work more efficient.

- `grep`
- `egrep`
- `fgrep`

## Word frequency

Use the [assignment 1](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assignments.md#assignment-0----bridging-assignment-for-language-efficiency) as an example:

```python
import os
import pandas as pd
  
def read_txt(path): #read files and get content
    all_text = []
    for file in os.listdir(path):
        f=open(file,"r+",encoding="utf8")
        contents= f.read()
        all_text.append(contents)
    all_words = "".join(all_text)
    for ch in '\s+\.\!\/_,$%^*(+\"\')]+|[+——()?:【】“”‘’！，。’':
        words = all_words.replace(ch," ")
    return words

def stopwordslist(filepath):   #set stopwords
    stopwords = [line.strip() for line in open(filepath, 'r', encoding='utf-8').readlines()]  
    return stopwords

def remove_stopwords(words): #remove stopwords
    processed_word_list = [] 
    for word in words:
        word = word.lower() # in case they arenet all lower cased
        if word not in stopwords:
            processed_word_list.append(word)
    return processed_word_list

words = read_txt("text/")
words = words.split()
stopwords = stopwordslist('./stopwords_eng.txt')
stopwords = set(stopwords)
processed_word_list = remove_stopwords(words)
word_count = pd.Series(processed_word_list).value_counts().sort_values(ascending=False)[0:15]
```

Output:

```text
china             69
trade             52
chinese           43
trump             32
war               25
beijing           20
u.s.              17
tariffs           16
america           15
american          14
president         14
global            14
economic          11
administration    11
foreign           10
```

### Visualize word frequency

#### with bar chart

```python
#you can use other visualization library
import seaborn as sns
import matplotlib.pyplot as plt 
def word_count(processed_word_list):
    word_count = pd.Series(processed_word_list).value_counts().sort_values(ascending=False)[0:15]  
    fig = plt.figure(figsize=(16,8))  
    x = word_count.index.tolist()  
    y = word_count.values.tolist()  
    sns.barplot(x, y, palette="BuPu_r")  
    plt.title('word frequency top 15')  
    plt.ylabel('count')  
    sns.despine(bottom=True)  
    #plt.savefig('./word_count_bar.png',dpi=400)  
    plt.show()

word_count(processed_word_list)
```

![Words frequency bar](assets/words-frequency-top15-bar.png)

#### with tag cloud

Tag cloud is commonly used, for aesthetics purpose. However, it is not a precise presentation of the data.

```python
from PIL import Image
import wordcloud
import numpy as np

def tag_cloud(text):
    mask = np.array(Image.open('newspaper.png')) #set mask, you can change to the picture you like, but it must have a high color contrast
    wc = wordcloud.WordCloud(mode='RGBA',background_color='white',max_words=2000,stopwords=stopwords,max_font_size=300,random_state=42,mask=mask)
    wc.generate_from_text(' '.join(text))
    plt.figure(figsize=(12,12))
    plt.imshow(wc, interpolation='bilinear')
    plt.axis("off")
    plt.title('word frequency top 15 tag cloud', loc='Center', fontsize=20)
    plt.show()
    return plt.show()

tag_cloud(words)
```

![Words frequency tag cloud](assets/words-frequency-tag-cloud.png)

## Word segmentation

- `jieba` for Chinese. You can download the article [here](assets/trade-wars-zh.txt)

```python
import jieba
text = open('trade-wars-zh.txt',"r").read()
#cut words
words = jieba.cut(text)
#set stopwords
filepath = 'stopwords.txt'
stopwords = [line.strip() for line in open(filepath, 'r', encoding='utf-8').readlines()]
#remove stopwords
processed_word_list = []
for word in words:
    if word not in stopwords and len(word)>1: #remove single word
        processed_word_list.append(word)

#processed_word_list
```

### How to add new terms to the wordseg dictionary

Example 1: Customize your own words dict

For basic needs, using `suggest_freq(segment, tune=True)` and `add_word(word)` are recommended.

```python
print('/'.join(jieba.cut('特朗普已经准备好对所有进口美国的中国商品征收关税')
#中国/已/表示/计划/对/美国/的/任何/贸易壁垒/进行/报复/。
jieba.suggest_freq(('贸易', '壁垒'), True)
print('/'.join(jieba.cut('中国已表示计划对美国的任何贸易壁垒进行报复。')))
#中国/已/表示/计划/对/美国/的/任何/贸易/壁垒/进行/报复/。
jieba.add_word('贸易壁垒')
print('/'.join(jieba.cut('中国已表示计划对美国的任何贸易壁垒进行报复。')))
#中国/已/表示/计划/对/美国/的/任何/贸易壁垒/进行/报复/。
```

Example 2: Ambiguous word segmentation

1. 如果 & 果汁

```python
s1 = '香港的自来水如果汁一般好喝'
'/'.join(jieba.cut(s1))
#'狮子山/的/山泉水/如果/汁/一般/好喝'
jieba.suggest_freq(('如', '果'), True)
'/'.join(jieba.cut(s1))
#'狮子山/的/山泉水/如/果汁/一般/好喝'
```

2. 乒乓球拍 卖完了& 乒乓球 拍卖完了

```python
s2 = '乒乓球拍卖完了'
'/'.join(jieba.cut(s2))
#'乒乓球/拍卖/完/了'
jieba.add_word('乒乓球拍')
jieba.suggest_freq(('拍', '卖'), True)
#'乒乓球拍/卖完/了'
```

For a complicated cases, you can refer [here](https://blog.csdn.net/qq_30262201/article/details/80128076) to customize your own words dict.

### How to adjust term weight in the wordseg dictionary

## Bonus: TF.IDF

- Term Frequency
- Inverse Document Frequency

## Bonus: Topic model

<!-- TODO: -->

## Bonus: Sentiment analysis

- Construct classifier using `sklearn`.
- Online API like [text-processing](http://text-processing.com/docs/sentiment.html).
- `TextBlob` is also useful and applied in [group 2's work](https://dnnsociety.org/2018/03/02/using-big-data-to-figure-out-how-fair-china-daily-news-is/).

## Bonus: word2vec

<!-- NOTE: new outline end -->

## Text

----

Following content is from week7 of S18 offering. Unorganised yet.

## Check the information in terminal

* `which pip3`is to learn where is pip3 in your computer. You can also input `which pip`to know the location of pip.

* `ls -l` means to list the files in the mode of listing with details.  
  ![](assets/to-do-uncategorized-screenshots/no31.png)  
  From the above screenshot, you can find that Python equals to python3.6 and the same as python3. Pip does not equal to pip3.

* `cat` to check the content to verify if they are the same.  
  ![](assets/to-do-uncategorized-screenshots/no32.png)  
  Obviously, they are the same.

* You can also drag the pip file and pip3 file into the Visual Studio Code,after you use `which` to know their location.

## Simple steps to start Jupyter notebook in terminal

### 4 Steps

* Step1  
  `pyvenv venv` means create a virtual environment\(venv\) folder called 'venv'. You can change the folder's name as you like, like `pyvenv BIGDATA`.  
    Be careful where you create the folder.

* Step2  
  `source venv/bin/activate` means activate the virtual environment. Then you will see the '\(venv\)',which means you are in a virtual environment.  
  ![](assets/to-do-uncategorized-screenshots/no33.png)  
  You can `deactivate` the virtual environment.

* Step3

  ```
  pip install jupyter
  pip install requests
  ```

* Step4  
  `Jupyter notebook` to open notebook.

### New

* If you are in the same computer, or on your own laptop, you don't need to totally follow the 4 steps.

* Pili's virtual environment folder is 'environment'. So if he restart his computer, he can just

  ```
  source enviroment/bin/activate
  Jupyter notebook
  ```

  ![](assets/to-do-uncategorized-screenshots/no34.png)

### Install modules in jupyter

* You can just pip install packages in jupyter notebook.
  ![](assets/to-do-uncategorized-screenshots/no35.png)

## For loop

### Range\(\)

* Function 'Range' has 3 parameters. From XX to XX with the step size XX.  
  The 3rd parameter is the step size. If you don't input the 3rd one, it will take 1 in default.
  ![](assets/to-do-uncategorized-screenshots/no36.png) 

*  The parameters can be negative.
  ![](assets/to-do-uncategorized-screenshots/no37.png)  
  ![](assets/to-do-uncategorized-screenshots/no38.png)

* 'i' is defined in the whole coding,from the beginning of 'import' to the end of the coding, not only inside for loop.

* If you define sth inside the `def`, the definition will only work inside the def.

### Append VS Extend

![](assets/to-do-uncategorized-screenshots/no39.png)

* In the for loop, i will be 10, 8 then 6 and 4 at last. Only the last value is left.

![](assets/to-do-uncategorized-screenshots/no40.png)

* `append` means add. Every time you have an 'i', you add it into the 'pages' list.

![](assets/to-do-uncategorized-screenshots/no41.png)

* `append` means that the whole list is appended as an element, or one item.

* `extend` means extract the items and add those items into the new list.

## Verify every step -splinter python

### Fail to save content

![](assets/to-do-uncategorized-screenshots/no42.png)

```
r=requests.get('XXXXthe website')
```
The above step is OK.

```
 r.text
 open('mypage','w').write(r.text)
```

* Then you can find a file.  

![](assets/to-do-uncategorized-screenshots/no43.png)  
If you open it, you will find that
![](assets/to-do-uncategorized-screenshots/no44.png)  
It is blank, which means the file you save is blank.  
SO try to verify everything step by step.

### Resolution splinter

Splinter is a browser to emulate a real person. So the website won't know whether you are a man or a robot.  
![](assets/to-do-uncategorized-screenshots/no45.png)

You can google to learn that.



### Save time

* You can interrupt it.  
  ![](assets/to-do-uncategorized-screenshots/no83.png)  
  ![](assets/to-do-uncategorized-screenshots/no84.png)

* You can run the top20.  
  ![](assets/to-do-uncategorized-screenshots/no85.png)  
  ![](assets/to-do-uncategorized-screenshots/no86.png)

### Calculate the frequent terms

#### Get text

  ![](assets/to-do-uncategorized-screenshots/no87.png) 
  ![](assets/to-do-uncategorized-screenshots/no88.png)  
  ![](assets/to-do-uncategorized-screenshots/no89.png)  
 Get the text.

  ```
  .split()
  ```
  
  ![](assets/to-do-uncategorized-screenshots/no90.png)  
  ![](assets/to-do-uncategorized-screenshots/no91.png)  
  ![](assets/to-do-uncategorized-screenshots/no92.png)  
  Split by space or comma.

  ```
  [:10]
  ```

  ![](assets/to-do-uncategorized-screenshots/no93.png)  
  Get the formal 10 items' text.

  ```
  extend()
  ```

  ![](assets/to-do-uncategorized-screenshots/no94.png)  
  Split the formal 5 items' text and split them by space. Then extract the items and add the items into list 'all\_text'.

*  If we run for whole text, cancelling '\[:5\]'. There is an error.  
  ![](assets/to-do-uncategorized-screenshots/no95.png)  
   We have to change the text into str.![](assets/to-do-uncategorized-screenshots/no96.png)

#### Word count

  ![](assets/to-do-uncategorized-screenshots/no97.png)  
  ![](assets/to-do-uncategorized-screenshots/no98.png)

  ```
  pd.Series()
  ```

  ![](assets/to-do-uncategorized-screenshots/no99.png)  
  ![](assets/to-do-uncategorized-screenshots/no100.png)  
  Convert 'word count' into a Series, and reset index.

  ```
  .to_frame().reset_index()
  ```

  ![](assets/to-do-uncategorized-screenshots/no101.png)  
  Convert into a dataframe.

  ```
  sort_values(ascending=False)
  ```

  ![](assets/to-do-uncategorized-screenshots/no102.png)  
  They are not informative, as there are so many 'stop-words'. We can delete those words manually.

  ```
  set(['RT', 'the', 'of'])
  ```

  ![](assets/to-do-uncategorized-screenshots/no103.png)  
  `set` is more efficient for the integers to check in or not in.

* You can search google you can find 'stop word' resources.

* NLTK:   
  ![](assets/to-do-uncategorized-screenshots/no104.png)

#### Stop word

![](assets/to-do-uncategorized-screenshots/no105.png)  
![](assets/to-do-uncategorized-screenshots/no106.png)

* Step1

  ```
  def is_stop_word(x):
  return x in stop_words
  ```

* Step2

  ```
  df_wrod_count[df_word_count['index'].apply(is_stop_word)]
  ```

* Step3

  ```
  .sort_values(by=0,ascending=False)
  ```

* Step4

  ```
  is not stop
  ```

![](assets/to-do-uncategorized-screenshots/no107.png)  

#### Word cloud

![](assets/to-do-uncategorized-screenshots/no108.png)
![](assets/to-do-uncategorized-screenshots/no109.png)
*  ![](assets/to-do-uncategorized-screenshots/no110.png)
   

#### Jieba


![](assets/to-do-uncategorized-screenshots/no111.png)
  ```
  jieba.cut()
  ```

![](assets/to-do-uncategorized-screenshots/no113.png)  

*  It means we have to change it into a list.  
![](assets/to-do-uncategorized-screenshots/no114.png)

#### Pandas plotting

* Please learn to learn from others by google.

* Pandas can be more powerful than excel.First of all,let's start from the excel function.

## Time series

**TODO**: Organise concept notes here.

At present, you can refer to those
[notebooks from S18 class](https://github.com/hupili/python-for-data-and-media-communication/tree/a4922340f55c4565fff19979f77862605ac19f22/w8-datetime).

## Geographical data

**TODO**

Following are the major steps and considerations when dealing with geographical data:

1. Geocode: turn geographical names into longitude and latitude coordinates. For example, you can not plot `Hong Kong` on a map, but you can plot `(114.141, 22.362)` on the map. (you can use [geojson.io](http://geojson.io/#map=11/22.3672/114.0580) to quickly get the data).
2. Projection: even if you get the geo coordinates somehow, it still can not be plotted on the screen directly. We need a translation from the geo coordinates to screen coordinates. For example, if we want to put HK in the center of the a `640px by 480px` 2D map, we need to establish a mapping like `(114.141, 22.362) --> (320px, 240px)`. This process is called projection. The actual project is more complex than that. Here's a demo of [different methods of projection](https://www.jasondavies.com/maps/transition/).
   - Scatter plot/ bubble plot -- simply project the point coordinates
   - Choropleth -- one needs to project a geometry
3. Base layer: maps are usually organised into layers. Besides puting the data points we are interested in onto the map, we also show some geographical information, like consitutuency boundaries, streets and ontours. This is the benefit of map -- put new data points onto a plate that people are already familiar with. This kind of information usually comes with the "base layer", whereas the above plotted elements are in "data layers". Choices for base layer are like Google Maps, Open Street Map, Mapbox, etc.

References for geographical data:

- Draw geo scatter plot via matplotlib: [England and Ireland seen from pub locations](http://ramiro.org/notebook/mapping-pubs/)
- Bubble chart on map using `folium` (leaflet.js based) for visualisation and `overpy` for geocoding: [Visualising HK property prices](https://medium.com/coinmonks/visualizing-property-prices-in-hong-kong-with-pandas-overpy-and-folium-595240ffca90)
- Plot choropleth using `folium`: [United States unemployment rate choropleth map](https://python-graph-gallery.com/292-choropleth-map-with-folium/) . One needs to prepare a data table and a geojson file which includes the interested geometries.

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)

----
