# Week 7 - Text analysis

<div id="toc">

<!-- TOC -->

- [Week 7 - Text analysis](#week-7---text-analysis)
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
        - [Exercise Tweeter Troll Data](#exercise-tweeter-troll-data)
        - [Download the file](#download-the-file)
    - [Dataframe](#dataframe)
        - [Apply a function onto every element of the dataframe.](#apply-a-function-onto-every-element-of-the-dataframe)
        - [Convert text by str(),lower()](#convert-text-by-strlower)
        - [Use the previous step as a filter](#use-the-previous-step-as-a-filter)
        - [Find the most one retweeted - by function.](#find-the-most-one-retweeted---by-function)
        - [Apply the function into all the names](#apply-the-function-into-all-the-names)
            - [Try1 Fail](#try1-fail)
            - [Try2 change the name as the value of the Series](#try2-change-the-name-as-the-value-of-the-series)
            - [Try3 succeed](#try3-succeed)
        - [Save time](#save-time)
        - [Calculate the frequent terms](#calculate-the-frequent-terms)
            - [Get text](#get-text)
            - [Word count](#word-count)
            - [Stop word](#stop-word)
            - [Word cloud](#word-cloud)
            - [Jieba](#jieba)
            - [Pandas plotting](#pandas-plotting)

<!-- /TOC -->

</div>

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

### Exercise Tweeter Troll Data

* Pili's Github  
  [https://github.com/hupili/python-for-data-and-media-communication](https://github.com/hupili/python-for-data-and-media-communication)

* Exercise Data:  
  [https://github.com/hupili/python-for-data-and-media-communication/blob/master/w7-text/Twitter Troll data from NBC \(nltk\).ipynb](https://github.com/hupili/python-for-data-and-media-communication/blob/master/w7-text/Twitter Troll data from NBC %28nltk%29.ipynb)

* Research get those deleted data from archive.

### Download the file

* `Control + right click` the 'save the file\(link\) as ...'.  
  ![](assets/to-do-uncategorized-screenshots/no46.png)

* Drag that into our working folder or just download into the folder.  
  ![](assets/to-do-uncategorized-screenshots/no47.png)

## Dataframe

  ```
  import pandas as pd
  df= pd.read_csv('XXXXXXXXXXXXXX.csv')
  ```

  ![](assets/to-do-uncategorized-screenshots/no48.png)

* It can also be opened by '[https://XXXX](https://XXXX) links'.

  ```
  import pandas as pd
  df= pd.read_csv('https://XXXXXXXXXXXXXXXXX')
  ```

  ```
  df.sample(10)
  ```

  ![](assets/to-do-uncategorized-screenshots/no49.png)  
  It means it randomly print 10 samples. It is useful when your dataset is very large, which will be slow to run the code.

  ```
  df['user_key'].value_counts()
  ```

  ![](assets/to-do-uncategorized-screenshots/no50.png)  
  Count the popular users. They post largest number of messages.

  ```
  'a' in 'am'
  ```

  ![](assets/to-do-uncategorized-screenshots/no51.png)  
  `in` is to check if it is contained in the text.

```
  'abc'.find('b')
```

  ![](assets/to-do-uncategorized-screenshots/no52.png)  
  It shows the index, which starts from 0. You can see from \[46\], space is also contained. And '-1' means the last one.

### Apply a function onto every element of the dataframe.

  ```
  df.apply()
  ```

  ![](assets/to-do-uncategorized-screenshots/no53.png)  
  ![](assets/to-do-uncategorized-screenshots/no54.png)

* `def` is to define a function called check\_name, which checks if 'amXXX' in x. If it is true, it will return 'amXXX'.

* x is just a variable.

* `apply` to make the function work for all the 'text' in the dataframe. In other words, x='text' in the example.

* There is an error in the second line. There are some dirty data in 'text'.

### Convert text by str(),lower()

  ```
  str(x)
  ```

  ![](assets/to-do-uncategorized-screenshots/no55.png)

  ```
  .value_counts()
  ```

  ![](assets/to-do-uncategorized-screenshots/no56.png)  
  It is to check how many times it appears. And they are the same, which means there are some errors.

 ```
  lower()
  upper()
  ```

  ![](assets/to-do-uncategorized-screenshots/no57.png)  
  ![](assets/to-do-uncategorized-screenshots/no58.png)

### Use the previous step as a filter
 
```
df[df['XXX'] ]
```

  ![](assets/to-do-uncategorized-screenshots/no59.png)  
  ![](assets/to-do-uncategorized-screenshots/no60.png)

* \[61\] is a filter. Now it works. We successfully find out how many times they are retweeted.

```
df['text'].apply[check_names].value_counts()[True]
```
![](assets/to-do-uncategorized-screenshots/no61.png)

* We extract the True.

### Find the most one retweeted - by function.

  ```
  def check_name(x):
    retutn 'ten_gop' in str(x).lower()
  df['text'].apply[check_names].value_counts()[True]
  ```

  It is the previous step.

  ```
  def count_retweeted_number(name):
    def check_name(x):
        retutn 'name' in str(x).lower()
    return df['text'].apply(check_name).value_counts()[True]
  ```

  ![](assets/to-do-uncategorized-screenshots/no62.png)

* Now we write the previous one into a function. In the inside function, we change 'x' into 'name'.

  ```
  count_retweeted_number('XXX')
  ```

  ![](assets/to-do-uncategorized-screenshots/no63.png)

### Apply the function into all the names

#### Try1 Fail

* `df['user_key']`  
  ![](assets/to-do-uncategorized-screenshots/no64.png)

  ![](assets/to-do-uncategorized-screenshots/no65.png)  
  It is a Series.

 ```
  s_user=df['user_key']
  ```

  ![](assets/to-do-uncategorized-screenshots/no66.png)  
  ![](assets/to-do-uncategorized-screenshots/no67.png)  
  The `value_counts` is just to show you how many times they appear. 's\_user' is just like a dictionary.

 ```
  s_user.apply(count_retweeted_number)
  ```

  ![](assets/to-do-uncategorized-screenshots/no68.png)  
  `apply` is a function which only works for the values.  
  Apply the function into all the 'user\_key'. But there is an error. Because we are applying on the values of the 's\_\_user',  which is obviously integers in \[75\].  So we have to change the name as the value of the Series. Then we can apply to the names.

#### Try2 change the name as the value of the Series

  ```
  s_user.index
  s_user.values
  ```

  ![](assets/to-do-uncategorized-screenshots/no69.png)  
  It is to check the index and values. They are correspond to each other.

  ```
  s_user.to_frame.reset_index()
  ```

  ![](assets/to-do-uncategorized-screenshots/no70.png)  
  `to_frame` is to change Series into Dataframe.  
  `reset_index` is to add an index. Then the formal index will be change into a value, whose column name is 'index'.

  ```
  df_user['index'].apply()
  ```

  ![](assets/to-do-uncategorized-screenshots/no71.png)  
  
  ![](assets/to-do-uncategorized-screenshots/no72.png)

* The error is in the picture below:  
  ![](assets/to-do-uncategorized-screenshots/no73.png)  
  In this step, if the answer is false, there will be an error.

#### Try3 succeed

* As we write before:

  ```
  s_user=df['user_key']
  ```


  ```
  .get()
  ```

  ![](assets/to-do-uncategorized-screenshots/no74.png)  
  ![](assets/to-do-uncategorized-screenshots/no75.png)  
  ![](assets/to-do-uncategorized-screenshots/no76.png)  
  ![](assets/to-do-uncategorized-screenshots/no77.png)  
  ![](assets/to-do-uncategorized-screenshots/no78.png)

  \[87\] is something appear in the content.  
  \[88\] is the same.  
  \[89\] does not exist in the content.  
  \[90\] and \[91\] means we change the return of the 'false'. In default, it is empty. We can change it in the 2nd parameter. It is better to set it as 0 in this example.

  ```
  .get(True,0)
  ```

  ![](assets/to-do-uncategorized-screenshots/no79.png)

  ```
  sort_values(by='user_key',ascending=False)
  ```

  ![](assets/to-do-uncategorized-screenshots/no80.png)  
  We can find out who tweeted the largest number of tweets.

  ```
  sort_values(by='count',ascending=False)
  ```

  ![](assets/to-do-uncategorized-screenshots/no81png)  
  We can find out who is retweeted most.  
  ![](assets/to-do-uncategorized-screenshots/no82.png)  
  So it will execute 454 times. It really takes a long time to finish the whole code.

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


------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)

