# Week 7 - Text analysis

### Check the information in terminal

* `which pip3`is to learn where is pip3 in your computer. You can also input `which pip`to know the location of pip.

* `ls -l` means to list the files in the mode of listing with details.  
  ![](/assets/Screen Shot 2018-03-14 at 8.39.55 pm.png)  
  From the above screenshot, you can find that Python equals to python3.6 and the same as python3. Pip does not equal to pip3.

* `cat` to check the content to verify if they are the same.  
  ![](/assets/Screen Shot 2018-03-14 at 8.46.05 pm.png)  
  Obviously, they are the same.

* You can also drag the pip file and pip3 file into the Visual Studio Code,after you use `which` to know their location.

### Simple steps to start Jupyter notebook in terminal.

##### 4 Steps

* Step1  
  `pyvenv venv` means create a virtual environment\(venv\) folder called 'venv'. You can change the folder's name as you like, like `pyvenv BIGDATA`.  
    Be careful where you create the folder.

* Step2  
  `source venv/bin/activate` means activate the virtual environment. Then you will see the '\(venv\)',which means you are in a virtual environment.  
  ![](/assets/Screen Shot 2018-03-14 at 8.34.33 pm.png)  
  You can `deactivate` the virtual environment.

* Step3

  ```
  pip install jupyter
  pip install requests
  ```

* Step4  
  `Jupyter notebook` to open notebook.

##### New

* If you are in the same computer, or on your own laptop, you don't need to totally follow the 4 steps.

* Pili's virtual environment folder is 'environment'. So if he restart his computer, he can just

  ```
  source enviroment/bin/activate
  Jupyter notebook
  ```

  ![](/assets/Screen Shot 2018-03-14 at 8.59.18 pm.png)

### Install modules in jupyter

* You can just pip install packages in jupyter notebook.
  ![](/assets/Screen Shot 2018-03-15 at 6.16.50 pm.png)

### For loop

##### Range\(\)

* Function 'Range' has 3 parameters. From XX to XX with the step size XX.  
  The 3rd parameter is the step size. If you don't input the 3rd one, it will take 1 in default.  
  >![](/assets/Screen Shot 2018-03-14 at 9.10.05 pm.png)  
*  The parameters can be negative.

  > ![](/assets/Screen Shot 2018-03-14 at 9.11.39 pm.png)  
  > ![](/assets/Screen Shot 2018-03-14 at 9.12.03 pm.png)

* 'i' is defined in the whole coding,from the beginning of 'import' to the end of the coding, not only inside for loop.

* If you define sth inside the `def`, the definition will only work inside the def.

##### Append VS Extend

> ![](/assets/Screen Shot 2018-03-14 at 9.20.07 pm.png)

* In the for loop, i will be 10, 8 then 6 and 4 at last. Only the last value is left.

> ![](/assets/Screen Shot 2018-03-14 at 9.24.45 pm.png)

* `append` means add. Every time you have an 'i', you add it into the 'pages' list.

> ![](/assets/Screen Shot 2018-03-14 at 9.29.07 pm.png)

* `append` means that the whole list is appended as an element, or one item.

* `extend` means extract the items and add those items into the new list.

### Verify every step -splinter python

##### Fail to save content.

> ![](/assets/Screen Shot 2018-03-14 at 9.34.32 pm.png)
>
> ```
> r=requests.get('XXXXthe website')
> ```

* The above step is OK.

> ```
 r.text
 open('mypage','w').write(r.text)
 ```

*  Then you can find a file.  

> ![](/assets/Screen Shot 2018-03-14 at 9.38.22 pm.png)  
> If you open it, you will find that![](/assets/Screen Shot 2018-03-14 at 9.38.37 pm.png)  
> It is blank, which means the file you save is blank.  
> SO try to verify everything step by step.

##### Resolution: splinter

* Splinter is a browser to emulate a real person. So the website won't know whether you are a man or a robot.  
  ![](/assets/Screen Shot 2018-03-14 at 9.45.48 pm.png)

* You can google to learn that.

### Exercise: Tweeter Troll Data

* Puli's Github  
  [https://github.com/hupili/python-for-data-and-media-communication](https://github.com/hupili/python-for-data-and-media-communication)

* Exercise Data:  
  [https://github.com/hupili/python-for-data-and-media-communication/blob/master/w7-text/Twitter Troll data from NBC \(nltk\).ipynb](https://github.com/hupili/python-for-data-and-media-communication/blob/master/w7-text/Twitter Troll data from NBC %28nltk%29.ipynb)

* Research get those deleted data from archive.

##### Download the file.

* `Control + right click` the 'save the file\(link\) as ...'.  
  ![](/assets/Screen Shot 2018-03-14 at 9.52.25 pm.png)

* Drag that into our working folder or just download into the folder.  
  ![](/assets/Screen Shot 2018-03-15 at 6.22.23 pm.png)

##### Dataframe

* ```
  import pandas as pd
  df= pd.read_csv('XXXXXXXXXXXXXX.csv')
  ```

  ![](/assets/Screen Shot 2018-03-15 at 6.24.03 pm.png)

* It can also be opened by '[https://XXXX](https://XXXX) links'.

  ```
  import pandas as pd
  df= pd.read_csv('https://XXXXXXXXXXXXXXXXX')
  ```

* ```
  df.sample(10)
  ```

  ![](/assets/Screen Shot 2018-03-15 at 9.35.47 pm.png)  
  It means it randomly print 10 samples. It is useful when your dataset is very large, which will be slow to run the code.

* ```
  df['user_key'].value_counts()
  ```

  ![](/assets/Screen Shot 2018-03-15 at 9.38.53 pm.png)  
  Count the popular users. They post largest number of messages.

* ```
  'a' in 'am'
  ```

  ![](/assets/Screen Shot 2018-03-15 at 9.49.07 pm.png)  
  `in` is to check if it is contained in the text.

* ```
  'abc'.find('b')
  ```

  ![](/assets/Screen Shot 2018-03-15 at 9.55.47 pm.png)  
  It shows the index, which starts from 0. You can see from \[46\], space is also contained. And '-1' means the last one.

##### Apply a function onto every element of the dataframe.

* ```
  df.apply()
  ```

  ![](/assets/Screen Shot 2018-03-15 at 10.04.07 pm.png)  
  ![](/assets/Screen Shot 2018-03-15 at 10.10.38 pm.png)

* `def` is to define a function called check\_name, which checks if 'amXXX' in x. If it is true, it will return 'amXXX'.

* x is just a variable.

* `apply` to make the function work for all the 'text' in the dataframe. In other words, x='text' in the example.

* There is an error in the second line. There are some dirty data in 'text'.

##### Convert text by str\(\),lower\(\).

* ```
  str(x)
  ```

  ![](/assets/Screen Shot 2018-03-15 at 10.13.31 pm.png)

* ```
  .value_counts()
  ```

  ![](/assets/Screen Shot 2018-03-15 at 10.19.54 pm.png)  
  It is to check how many times it appears. And they are the same, which means there are some errors.

* ```
  lower()
  upper()
  ```

  ![](/assets/Screen Shot 2018-03-15 at 9.55.21 pm.png)  
  ![](/assets/Screen Shot 2018-03-15 at 10.21.29 pm.png)

##### Use the previous step as a filter

*  
```
df[df['XXX'] ]
```

  ![](/assets/Screen Shot 2018-03-15 at 10.23.33 pm.png)  
  ![](/assets/Screen Shot 2018-03-15 at 10.24.01 pm.png)

* \[61\] is a filter. Now it works. We successfully find out how many times they are retweeted.

* 
```
df['text'].apply[check_names].value_counts()[True]
```
![](/assets/Screen Shot 2018-03-16 at 3.03.09 pm.png)

* We extract the True.

##### Find the most one retweeted - by function.

* ```
  def check_name(x):
    retutn 'ten_gop' in str(x).lower()
  df['text'].apply[check_names].value_counts()[True]
  ```

  It is the previous step.

* ```
  def count_retweeted_number(name):
    def check_name(x):
        retutn 'name' in str(x).lower()
    return df['text'].apply(check_name).value_counts()[True]
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.17.36 pm.png)

* Now we write the previous one into a function. In the inside function, we change 'x' into 'name'.

* ```
  count_retweeted_number('XXX')
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.25.56 pm.png)

##### Apply the function into all the names.

##### Try1: Fail

* `df['user_key']`  
  ![](/assets/Screen Shot 2018-03-16 at 4.06.19 pm.png)

  ![](/assets/Screen Shot 2018-03-16 at 3.27.10 pm.png)  
  It is a Series.

* ```
  s_user=df['user_key']
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.35.18 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 3.32.53 pm.png)  
  The `value_counts` is just to show you how many times they appear. 's\_user' is just like a dictionary.

* ```
  s_user.apply(count_retweeted_number)
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.41.17 pm.png)  
  `apply` is a function which only works for the values.  
  Apply the function into all the 'user\_key'. But there is an error. Because we are applying on the values of the 's\_\_user',  which is obviously integers in \[75\].  So we have to change the name as the value of the Series. Then we can apply to the names.

##### Try2: change the name as the value of the Series

* ```
  s_user.index
  s_user.values
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.51.38 pm.png)  
  It is to check the index and values. They are correspond to each other.

* ```
  s_user.to_frame.reset_index()
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.59.49 pm.png)  
  `to_frame` is to change Series into Dataframe.  
  `reset_index` is to add an index. Then the formal index will be change into a value, whose column name is 'index'.

* ```
  df_user['index'].apply()
  ```

  ![](/assets/Screen Shot 2018-03-16 at 4.10.23 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.06.19 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.07.55 pm.png)

* The error is in the picture below:  
  ![](/assets/Screen Shot 2018-03-16 at 4.08.44 pm.png)  
  In this step, if the answer is false, there will be an error.

##### Try3: succeed

* As we write before:

  ```
  s_user=df['user_key']
  ```

  ![](/assets/Screen Shot 2018-03-16 at 3.35.18 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 3.32.53 pm.png)

* ```
  .get()
  ```

  ![](/assets/Screen Shot 2018-03-16 at 4.16.07 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.19.32 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.19.49 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.19.58 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.20.02 pm.png)

  > \[87\] is something appear in the content.  
  > \[88\] is the same.  
  > \[89\] does not exist in the content.  
  > \[90\] and \[91\] means we change the return of the 'false'. In default, it is empty. We can change it in the 2nd parameter. It is better to set it as 0 in this example.

* ```
  .get(True,0)
  ```

  ![](/assets/Screen Shot 2018-03-16 at 4.28.30 pm.png)

* ```
  sort_values(by='user_key',ascending=False)
  ```

  ![](/assets/Screen Shot 2018-03-16 at 4.30.18 pm.png)  
  We can find out who tweeted the largest number of tweets.

* ```
  sort_values(by='count',ascending=False)
  ```

  ![](/assets/Screen Shot 2018-03-16 at 4.33.28 pm.png)  
  We can find out who is retweeted most.  
  ![](/assets/Screen Shot 2018-03-16 at 4.37.55 pm.png)  
  So it will execute 454 times. It really takes a long time to finish the whole code.

##### Save time

* You can interrupt it.  
  ![](/assets/Screen Shot 2018-03-16 at 4.35.26 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.36.54 pm.png)

* You can run the top20.  
  ![](/assets/Screen Shot 2018-03-16 at 4.38.47 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 4.39.12 pm.png)

### Calculate the frequent terms

##### Get text

* > ![](/assets/Screen Shot 2018-03-16 at 5.06.43 pm.png)  
  > ![](/assets/Screen Shot 2018-03-16 at 5.06.53 pm.png)  
  > ![](/assets/Screen Shot 2018-03-16 at 5.07.07 pm.png)  
  > Get the text.
* ```
  .split()
  ```
  
  >![](/assets/Screen Shot 2018-03-16 at 5.07.21 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 5.07.46 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 5.07.59 pm.png)  
  Split by space or comma.

* ```
  [:10]
  ```

  >![](/assets/Screen Shot 2018-03-16 at 5.13.49 pm.png)  
  Get the formal 10 items' text.

* ```
  extend()
  ```

  >![](/assets/Screen Shot 2018-03-16 at 5.15.14 pm.png)  
  Split the formal 5 items' text and split them by space. Then extract the items and add the items into list 'all\_text'.

*  If we run for whole text, cancelling '\[:5\]'. There is an error.  
  > ![](/assets/Screen Shot 2018-03-16 at 5.20.33 pm.png)  
  > We have to change the text into str.![](/assets/Screen Shot 2018-03-16 at 5.21.36 pm.png)

##### Word count

* >![](/assets/Screen Shot 2018-03-16 at 5.23.56 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 5.25.09 pm.png)

* ```
  pd.Series()
  ```

  ![](/assets/Screen Shot 2018-03-16 at 5.26.54 pm.png)  
  ![](/assets/Screen Shot 2018-03-16 at 5.27.33 pm.png)  
  Convert 'word count' into a Series, and reset index.

* ```
  .to_frame().reset_index()
  ```

  ![](/assets/Screen Shot 2018-03-16 at 5.28.05 pm.png)  
  Convert into a dataframe.

* ```
  sort_values(ascending=False)
  ```

  ![](/assets/Screen Shot 2018-03-16 at 5.30.33 pm.png)  
  They are not informative, as there are so many 'stop-words'. We can delete those words manually.

* ```
  set(['RT', 'the', 'of'])
  ```

  ![](/assets/Screen Shot 2018-03-16 at 6.03.44 pm.png)  
  `set` is more efficient for the integers to check in or not in.

* You can search google you can find 'stop word' resources.

* NLTK:   
  ![](/assets/Screen Shot 2018-03-16 at 6.19.21 pm.png)

##### Stop\_word

> ![](/assets/Screen Shot 2018-03-16 at 6.07.07 pm.png)  
> ![](/assets/Screen Shot 2018-03-16 at 6.09.15 pm.png)

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

  ![](/assets/Screen Shot 2018-03-16 at 6.16.07 pm.png)

##### Word cloud

![](/assets/Screen Shot 2018-03-16 at 6.29.19 pm.png)
*  ![](/assets/Screen Shot 2018-03-16 at 6.27.26 pm.png)
   ![](/assets/Screen Shot 2018-03-16 at 6.32.55 pm.png)

##### Jieba

![](/assets/Screen Shot 2018-03-16 at 7.33.26 pm.png)

* ```
  jieba.cut()
  ```

  >![](/assets/Screen Shot 2018-03-16 at 7.35.45 pm.png)  

*  It means we have to change it into a list.  
  >![](/assets/Screen Shot 2018-03-16 at 7.37.21 pm.png)

### Pandas plotting

* Please learn to learn from others by google.

* Pandas can be more powerful than excel.First of all,let's start from the excel function.



