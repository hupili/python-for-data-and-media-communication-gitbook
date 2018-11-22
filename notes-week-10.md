# Week 10: Text data

<div id="toc">

<!-- TOC -->

- [Week 10: Text data](#week-10-text-data)
    - [Text processing](#text-processing)
        - [String functions recap](#string-functions-recap)
            - [Case 1: Get full URL from HTML A tag's href attribute](#case-1-get-full-url-from-html-a-tags-href-attribute)
            - [Case 2: Substring matching and substitution](#case-2-substring-matching-and-substitution)
            - [Case 3: Most frequent names in tweets](#case-3-most-frequent-names-in-tweets)
        - [encode and decode](#encode-and-decode)
        - [String matching and Regular Expression (RegEx)](#string-matching-and-regular-expression-regex)
            - [RegEx case 1: match Twitter username from tweets](#regex-case-1-match-twitter-username-from-tweets)
            - [RegEx case 2: match telephone numbers in a piece of text](#regex-case-2-match-telephone-numbers-in-a-piece-of-text)
            - [Bonus: Text substitution](#bonus-text-substitution)
            - [RegEx in shell](#regex-in-shell)
    - [Stopwords](#stopwords)
        - [Set stopwords](#set-stopwords)
        - [Remove stopwords](#remove-stopwords)
    - [Word frequency](#word-frequency)
        - [Use dict to count the words frequency](#use-dict-to-count-the-words-frequency)
        - [Use pandas.series.value_counts()](#use-pandasseriesvalue_counts)
        - [Visualize word frequency](#visualize-word-frequency)
            - [with bar chart](#with-bar-chart)
            - [with tag cloud](#with-tag-cloud)
    - [Word segmentation](#word-segmentation)
        - [jieba for Chinese](#jieba-for-chinese)
        - [How to add new terms to the wordseg dictionary](#how-to-add-new-terms-to-the-wordseg-dictionary)
        - [How to adjust term weight in the wordseg dictionary](#how-to-adjust-term-weight-in-the-wordseg-dictionary)
    - [Bonus: TF.IDF](#bonus-tfidf)
    - [Bonus: Topic model](#bonus-topic-model)
    - [Bonus: Sentiment analysis](#bonus-sentiment-analysis)
    - [Bonus: word2vec](#bonus-word2vec)
    - [Further readings](#further-readings)

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

#### Case 1: Get full URL from HTML A tag's href attribute

Scraping Initiumlab articles' urls, which we used as an example in [chapter 5](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-05.md#scrape-all-articles-of-one-page)

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

#### Case 2: Substring matching and substitution

Check out certain words in a string, replace certain words and separate the words with some notations.

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

#### Case 3: Most frequent names in tweets

Apply a function onto every element of the dataframe - Check out the most frequent names in the tweets text

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

`UTF-8` is the most widely used implementation of Unicode on the Internet, while `GBK` is mainly used for coding Chinese character.

For example, scraping Chinese websites like `电影天堂`.

```python
url = 'https://www.dytt8.net/'
r = requests.get(url)
html_str = r.text
```

![Wrong encoding](assets/wrong-encoding.png)

You will find the results is messy because the website is using `gb2312` method to encode the html, which is kind of `GBK` methods.

![GBK encoding](assets/gbk-encoding.png)

Therefore, we need to firstly decode the content.

```python
html = r.content.decode('gbk')
html
```

After decoding, the Chinese characters can display appropriately. And when saving the data, you can use a more widely used method `utf-8` to encode it.

```python
with open('dy.csv','a',newline='',encoding='utf-8') as csvfile
```

![Decodes gbk](assets/decode-gbk.png)

### String matching and Regular Expression (RegEx)

The `.find()` and `in` operator on `str` has limited matching capability. They can only perform precise matching. What if we want to do fuzzy matching? Common siutations:

1. Find all the user names from the Twitter message. i.e. those look like `@xxxx `, i.e. start with `@` and end with ` ` (blank).
2. Find all the phone numbers from a paragraph of texts.

RegEx can solve those problems in a very concise way. We show you the power of RegEx in following subsections. Once you decide to move further, the [official doc on re](https://docs.python.org/3/library/re.html) is a good source for you to further study RegEx.

#### RegEx case 1: match Twitter username from tweets

Here's the solution for question 1.

```python
>>> tweet = '@tom @jacky and @will, please come to my office at 10am.'
>>> import re
>>> pattern = re.compile(r'@[a-zA-Z0-9]+')  # pattern of the Twitter username
>>> pattern.findall(tweet)
['@tom', '@jacky', '@will']
```

The key of learning RegEx is to learn the pattern string, i.e. `@[a-zA-Z0-9]+` in the above example. Let's decode this pattern as follows:

- `@` - matches a single `@` character.
- `[]` - is a collection notation, matching the current position to any valid character in this collection.
  - In our example, the collection is composed of
    - All characters from `a` to `z`, and from `A` to `Z`, and from `0` to `9`.
    - The hyphen `-` here is a notation to specify a range of characters.
- `+` - is a repetition number, meaning matching one or more characters using the preceding pattern character
  - The preceding pattern character is a collection, i.e. `[a-zA-Z0-9]`.

To sum it up, the above RegEx pattern can match all any substring that starts with a `@` character and then followed by one or more alphanumeric characters.

#### RegEx case 2: match telephone numbers in a piece of text

Learning RegEx is like learning a new language. It is very easy to match the pattern you want. However, it may be difficult to exclude things that you don't want to match. Let's give a demo using question 2. The first trial would be:

```python
>>> introduction = 'Student usually can enrol up to 16 courses in 1 semester. If you want to enrol in more courses, please contact Ms A at 34119999 or Mr B 34119998'
>>> pattern = re.compile(r'\d+')
>>> pattern.findall(introduction)
['16', '1', '34119999', '34119998']
```

In this pattern, `\d` means the collection of numbers, i.e. `[0-9]`. The `+` specifies a repetition count of one or multiple. You can see that all the numeric substrings are extracted. However, not all of them are telephone numbers. Gievn a bit domain knowledge, we know that the phone numbers in Hong Kong have 8 digits. So we can adjust our pattern to use a repetition number of `{8}`:

```python
>>> pattern = re.compile(r'\d{8}')
>>> pattern.findall(introduction)
['34119999', '34119998']
```

The pattern works at present, but does not work when the text includes other 8-digit non telephone number substrings:

```python
>>> introduction = 'Student usually can enrol up to 16 courses in 1 semester. If you want to enrol in more courses, please contact Ms A at 34119999 or Mr B 34119998. Students who enrol in extra courses will be charged 12345678 dollar per course.'
>>> pattern = re.compile(r'\d{8}')
>>> pattern.findall(introduction)
['34119999', '34119998', '12345678']
```

The tuition fee is also match because our pattern is not precise enough. In order to fix this problem, we need to further apply our domain knowledge. We know that HKBU's telephone numbers start with `3411`. So we can revise our pattern and get following result:

```python
>>> pattern = re.compile(r'3411\d{4}')
>>> pattern.findall(introduction)
['34119999', '34119998']
```

The pattern is to match any 8 character string that starts with "3411" and ends with any four digits. The curious readers may ask: what if the tuition fee is "34113411 dollar"? As you guess, the above pattern fails. How to refine? The short answer is that there is no ultimate way. As long as "34113411" itself is a valid telephone number, we can hardly exclude it from our matching by just looking at itself. 

This issue is quite common text processing, or further more **Natural Language Processing (NL)**. The token itself is not enough for us to understand its meaning. One similar example is: "Apple is good". We are not sure if "the Apple" that produces iPhone is good; or apple, as a fruit, is good. We human being needs context in order to understand this sentence. So is computer. This discussion is beyond our curriculum. Interested readers can search for "NLP".

Back to our focus on basic pattern matching, we can conclude that it is easy to match the things one want using RegEx, but rather difficult to fully exclude other unwanted stuffs. When building your RegEx solution, you usually starts with a collection of **cases**. You keep on adding new cases to the collection and test them with your RegEx pattern. You may need to refine multiple times in order to find the one that works well on your dataset.

#### Bonus: Text substitution

RegEx can let you substitute some matching parts. This is very similar to the `str.replace` function but does more than that. It even allows one to interpolate variables using values from matching part.

Suppose the university decides "3411" is a bad prefix and "8888" sounds good. How do we change all the numbers? Checkout following solution:

```python
>>> pattern = re.compile(r'3411(\d{4})')
>>> re.sub(pattern, r'+852 8888-\1', introduction)
'Student usually can enrol up to 16 courses in 1 semester. If you want to enrol in more courses, please contact Ms A at +852 8888-9999 or Mr B +852 8888-9998. Students who enrol in extra courseswill be charged 12345678 dollar per course.'
```

Besides changing the telephone prefix, we also added the country code and a hyphen between university prefix and the phone number. Note how this happens:

- `()` is called a "group" in RegEx. The brackets do not match any character. However, patterns inside a pair of brackets are of the same group. The match substring will be put in the same group for further reference.
- `\1` means the first group. There could be multiple groups matched by one pattern. You can use `\n` notation to refer to the `n`-th group. `\0` means the entire string.

#### RegEx in shell

Following commands can be used to perform RegEx operation. Those commands sometimes can make your work more efficient.

- `grep`
- `egrep`
- `fgrep`

## Stopwords

### Set stopwords

1. You can download the `stopwords.txt` from the internet and load when you used, [example](https://github.com/stanfordnlp/CoreNLP/blob/master/data/edu/stanford/nlp/patterns/surface/stopwords.txt).

```python
filepath = './stopwords.txt'
stopwords = [line.strip() for line in open(filepath, 'r', encoding='utf-8').readlines()]
```

2. import stopwords from `nltk` library

```python
import nltk
from nltk.corpus import stopwords
nltk.download('stopwords')
stopwords = stopwords.words('english')
```

<!-- this method is under testing with error cannot download -->

3. import stopwords from `pypi`

For installation and documentation, you can refer [here](https://pypi.org/project/stop-words/
), they provide a diverse languages of stopwords.

4. Customize your own stopwords

You can add new stopwords by the case need.

```python
stopwords = list #the original stopwords list
newStopWords = ['stopWord1','stopWord2']
stopwords.extend(newStopWords)
```

### Remove stopwords

```python
processed_word_list = []
#assume you've already get a list of words  
for word in words:
    word = word.lower() # in case they are not all lower cased
    if word not in stopwords:
        processed_word_list.append(word)
```

## Word frequency

### Use dict to count the words frequency

```python
list = meaningful_words #the list of words you have
dict_words_frequency={}
for n in list:
    dict_words_frequency[n]=list.count(n)
#dict_words_frequency
```

### Use pandas.series.value_counts()

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
        word = word.lower() # in case they are not all lower cased
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

### jieba for Chinese

For english words, its easy to segment words, just by the blank space between the words. But for Chinese words, its more complicated, because there is no blank space in Chinese sentence and the combination of the characters in one sentences may diverse too. In order to handle this situation, `jieba` is the most useful libraries we can get out here, which is a Chinese specialized word segmentation module.

Install and import:

```python
!pip3 install jieba
import jieba
```

Basic usage:

```python
s = '我在浸会大学学python'
jieba.cut(s)
#output: <generator object Tokenizer.cut at 0x10f3a3048>
list(jieba.cut(s)) #turn it into list
#['我', '在', '浸会', '大学', '学', 'python']
```

Case1: Cut an article, you can download the article [here](assets/trade-wars-zh.txt).

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
s1 = '狮子山的山泉水如果汁一般好喝'
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

<!-- TODO: -->

## Further readings

1. [Unicode, ASCII,UTF-8 and GBK](https://jdhao.github.io/2018/01/28/unicodede-utf8-gbk/)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)
