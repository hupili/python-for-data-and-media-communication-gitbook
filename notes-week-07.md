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
`pyvenv venv` means create a virtual environment(venv) folder called 'venv'. You can change the folder's name as you like, like `pyvenv BIGDATA`. 
    Be careful where you create the folder.

* Step2 
`source venv/bin/activate` means activate the virtual environment. Then you will see the '(venv)',which means you are in a virtual environment.
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

##### Range()
* Function 'Range' has 3 parameters. From XX to XX with the step size XX.  
The 3rd parameter is the step size. If you don't input the 3rd one, it will take 1 in default.
![](/assets/Screen Shot 2018-03-14 at 9.10.05 pm.png)
The parameters can be negative.
>![](/assets/Screen Shot 2018-03-14 at 9.11.39 pm.png)
>![](/assets/Screen Shot 2018-03-14 at 9.12.03 pm.png)

* 'i' is defined in the whole coding,from the beginning of 'import' to the end of the coding, not only inside for loop.

* If you define sth inside the `def`, the definition will only work inside the def.

##### Append VS Extend

>![](/assets/Screen Shot 2018-03-14 at 9.20.07 pm.png)

* In the for loop, i will be 10, 8 then 6 and 4 at last. Only the last value is left.

>![](/assets/Screen Shot 2018-03-14 at 9.24.45 pm.png)

* `append` means add. Every time you have an 'i', you add it into the 'pages' list.

>![](/assets/Screen Shot 2018-03-14 at 9.29.07 pm.png)

* `append` means that the whole list is appended as an element, or one item.

* `extend` means extract the items and add those items into the new list.

### Verify every step -splinter python

##### Fail to save content.

>![](/assets/Screen Shot 2018-03-14 at 9.34.32 pm.png)
```
r=requests.get('XXXXthe website')
```

* The above step is OK.


>```
r.text
open('mypage','w').write(r.text) 
```
Then you can find a file.
![](/assets/Screen Shot 2018-03-14 at 9.38.22 pm.png)
If you open it, you will find that![](/assets/Screen Shot 2018-03-14 at 9.38.37 pm.png) 
It is blank, which means the file you save is blank.
SO try to verify everything step by step.

##### Resolution: splinter

* Splinter is a browser to emulate a real person. So the website won't know whether you are a man or a robot.
![](/assets/Screen Shot 2018-03-14 at 9.45.48 pm.png)

* You can google to learn that. 


### Exercise: Tweeter Troll Data 

* Puli's Github 
https://github.com/hupili/python-for-data-and-media-communication

* Exercise Data:
https://github.com/hupili/python-for-data-and-media-communication/blob/master/w7-text/Twitter%20Troll%20data%20from%20NBC%20(nltk).ipynb

* Research get those deleted data from archive.

##### Download the file.

* `Control + right click` the 'save the file(link) as ...'.
![](/assets/Screen Shot 2018-03-14 at 9.52.25 pm.png)

* Drag that into our working folder or just download into the folder.
![](/assets/Screen Shot 2018-03-15 at 6.22.23 pm.png)

##### Dataframe
* 
```
import pandas as pd
df= pd.read_csv('XXXXXXXXXXXXXX.csv')
```
![](/assets/Screen Shot 2018-03-15 at 6.24.03 pm.png)

* It can also be opened by 'https://XXXX links'.
```
import pandas as pd
df= pd.read_csv('https://XXXXXXXXXXXXXXXXX')
```

*  
```
df.sample(10)
```
![](/assets/Screen Shot 2018-03-15 at 9.35.47 pm.png)
It means it randomly print 10 samples. It is useful when your dataset is very large, which will be slow to run the code.

* 
```
df['user_key'].value_acount()
```
![](/assets/Screen Shot 2018-03-15 at 9.38.53 pm.png)
Count the popular users. They post largest number of messages.

* 
```
'a' in 'am'
```
![](/assets/Screen Shot 2018-03-15 at 9.49.07 pm.png)
`in` is to check if it is contained in the text.

* 
```
'abc'.find('b')
```
![](/assets/Screen Shot 2018-03-15 at 9.55.47 pm.png)
It shows the index, which starts from 0. You can see from [46], space is also contained. And '-1' means the last one.

##### Apply a function onto every element of the dataframe.
* 
```
df.apply()
```
![](/assets/Screen Shot 2018-03-15 at 10.04.07 pm.png)
![](/assets/Screen Shot 2018-03-15 at 10.10.38 pm.png)
* `def` is to define a function called check_name, which checks if 'amXXX' in x. If it is true, it will return 'amXXX'.  
* x is just a variable. 
* `apply` to make the function work for all the 'text' in the dataframe. In other words, x='text' in the example.
*  There is an error in the second line. There are some dirty data in 'text'.

##### Convert text by str(),lower().

* 
```
str(x)
```
![](/assets/Screen Shot 2018-03-15 at 10.13.31 pm.png)


* 
```
.value_count()
```
![](/assets/Screen Shot 2018-03-15 at 10.19.54 pm.png)
It is to check how many times it appears. And they are the same, which means there are some errors.

* 
```
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
* [61] is a filter. Now it works. We successfully find out how many times they are retweeted.

*
```
df['text'].apply[check_names].value_account()[True]
```
![](/assets/Screen Shot 2018-03-16 at 3.03.09 pm.png)
* We extract the True.

##### Find the most one retweeted - by function.

* 
```
def check_name(x):
    retutn 'ten_gop' in str(x).lower()
df['text'].apply[check_names].value_account()[True]       
```
It is the previous step.

* 
```
def count_retweeted_number(name):
    def check_name(x):
        retutn 'name' in str(x).lower()
    return df['text'].apply(check_name).value_count()[True]
```
![](/assets/Screen Shot 2018-03-16 at 3.17.36 pm.png)
* Now we write the previous one into a function. In the inside function, we change 'x' into 'name'.













* 
```
import pandas as pd
df= pd.read_csv('XXXXXXXXXXXXXX.csv')
```
* It can also be open by the https://XXXX links.


* 
```
import pandas as pd
df= pd.read_csv('XXXXXXXXXXXXXX.csv')
```




### Pandas plotting

* Please learn to learn from others by google.

* Pandas can be more powerful than excel.First of all,let's start from the excel function.












    


*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
*
* 





