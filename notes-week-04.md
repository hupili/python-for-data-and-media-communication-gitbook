# JSON and API

## Objective

* Learn to use Jupyter notebook. All demos following this week will be conducted in Jupyter notebook.
* Understand API/ JSON and can retrieve data from online databases (twitter, GitHub, weibo, douban, ...)
* Understand basic file format like json and csv.
    * Be able to comfortably navigate through compound structures like {} and [].
    * Be able to comfortably use (multiple layer of) for-loop to re-format data.
    * Be able to use serialisers to handle input/ output to files.

The brief of Application Programming Interface (API):

Operate in client-and-server mode.
Client does not have to download the full volume of data from server. Only use the data on demand.
Server can handle intensive computations that not available by client.
Server can send updated data upon request.

## Learn to use Jupyter Notebook

### Installing the Jupyter Notebook

Please see to our [tutorial](/module-jupyter.md) of how to install and enter jupyter notebook.
![jupyter notebook example](/assets/jupyter-notebook-example.png)

### Basic usage

1. click `new` to create a new python 3 notebook
2. write codes like you usually do in text editors, and press `shift`+`return` to run the code. It will return the results or errors under the cell.
3. use `! pip3 install module_name` to install modules in jupyter notebook.
4. in front of every cell, there is an `in [ ]` sign, the number in `[]` means the sequences of cells, and if there is `*` in `[]`, means that this cell is still running, you can either wait it finish or click `stop` under the `kernel` to exit from the running,pressing `I` twice will also do the trick.
5. cell. `run cell` run step by step. `run all above` to run and check the previous steps of coding.
6. kernel. `kernel` is a tool for interactive input and output all the things you did from the beginning. By clicking`restart`, you can give a variable another value.

## CSV

The CSV (Comma Separated Values) format is the most common import and export format for spreadsheets and databases,just like `xlsx` file, which is used for storing your data and make it easy to read and write. You don't need to pip install csv in terminal. Just import csv before using it.

The csv has two basic functions: `reader` and `writer` .objects read and write.

### csv.reader

Return a reader object which will iterate over lines in the given csv file. Each row read from the csv file is returned as a list of strings. No automatic data type conversion is performed.

Suppose we have a csv file, `name_list.csv`, the content is as follows:

| name  | id   | gender | location | phone|
|-------|------|--------|----------|------|
| Chico | 1742 |    M   |  KLN     |  3344|
| Ri    | 1743 |    F   |  LOS     |  5168|
| Ivy   | 1655 |    F   |   MK     |  7323|

How to read this csv?

```python
>>> import csv
... with open('name_list.csv', newline='') as f: # open csv
...     rows = csv.reader(f) # read CSV
...     for row in rows: #loop every row
...
>>>         print(row)
['name', 'id', 'gender', 'location', 'phone']
['Chico', '1742', 'M', 'KLN', '3344']
['Ri', '1743', 'F', 'LOS', '5168']
['Ivy', '1655', 'F', 'MK', '7323']
['', '', '', '', '']
```

**Note:**

* `with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening.

* `open()` means open the file. If there is no such file, it will create a new one. If there is a existing one, writer function will clear all the previous content and then write the new content.

* `newline=' '` is one of the certain structure, which is used to avoid blank line.

### csv.writer

Return a writer object responsible for converting the user’s data into delimited strings. Csvfile can be any object with a write() method. If csvfile is a file object, it should be opened with `newline=''`.

How to write a csv?

```python
with open('NAME.csv','w',newline='') as f:
... mywriter=csv.writer(f)  #writer is the function to write something
... mywriter.writerow(['Chico','Male'])  #you can just use writer.writerow()
... mywriter.writerow(['Ri','Female'])  
... mylist=[['KLN',1742,3344],['Los',1743,5168]]  
... mywriter.writerows(mylist)  
```  

The output will be a NAME.csv, whose content is like this:
![write a csv](/assets/csv-write-a-csv.png)

**Note:**

* `w` means write. By the way, if you want to read the file, you can input`r`,representing "read".

* `csv.writer()` means to write something in the NAME.csv file.

* `writerow()` means write one row and then another row. The input should be list type. `writerows()` means they will write row after row until loop all the elements from a list.


### Writerow vs Writerows: exercise

##### 1. Write "hello" in A1 in the excel table 
##### Try: fail 
```
import csv
with open('NAME.csv','w') as f:   
	myWriter=csv.writer(f)
	myWriter.writerows('hello')
``` 
![](/assets/Screen Shot 2018-03-07 at 8.18.06 pm.png)

##### Try: succeed

 you should put it in a list.Every item of the list will be write in a cell of the table.
```
	myWrite.writerow(['hello'])
```
![](/assets/Screen Shot 2018-03-07 at 8.19.02 pm.png)

##### 2. Write 2 rows

* If you want to write 2 rows:
```
	myWriter.writerow(['spam','1','2','3'])
	myWriter.writerow(['spam2','11','22','33'])
```
![](/assets/Screen Shot 2018-03-07 at 8.21.08 pm.png)

* Writerows example 1:
```
myWriter.writerows(['spam','1','2','3'])
```
![](/assets/Screen Shot 2018-03-07 at 8.36.30 pm.png)
`writerows()` means write all the rows in one time. It writes every item of the list into a row. Every item has a row. As 'spam' has 4 characters, or 4 strings, it can't understand the word. Then it is put in 4 columns.

* Writerow example 2:
```
myWriter.writerows([['spam','1'],['2','3'],['OK']) 
```
![](/assets/Screen Shot 2018-03-07 at 9.26.19 pm.png)
There are 3 items, or 3 lists, in the list. So there will be 3 rows. Every list is a row. 


# List and dictionary


```
list1=[1,2,3,4]
dictionary1={'title':'teacher', 'date':'2018/2/2'}
a=list1[0]
b=list1[1]
c=dictionary1['title']
```
![](/assets/Screen Shot 2018-03-07 at 9.37.08 pm.png)

* Some functions may require you input a list. Others may require you input a dictionary.

* Every dictionary has its key and value. The keys of dictionary1 are 'title' and 'date'. The value of dictionary1 are 'teacher' and '2018/2/2'. Every key has its own value. They are matched. 


```
list2=[[(40.7,-74.0),'NY'],[(49.2,-123.1),'Vancouver']]
list3=[{'code':0001,'price':11,'P/E':21},
       {'code':0002,'price':15,'P/E':3},
       {'code':0003,'price':13,'P/E':50},
]
dictionary2={'title':['NY','HK','TK'],'rank':[1,2,3]}
```
* list and dictionary can be very complete.Please understand the structure above.
### Scrape:IMDB (version1)

* The page's HTML is following. There are many 'contents'

>![](/assets/Screen Shot 2018-03-09 at 4.30.50 pm.png)
![](/assets/Screen Shot 2018-03-09 at 4.29.03 pm.png)

* ```
r='http://www.imdb.com/list/ls058982125/'
mypage=bs4.BeautifulSoup(r.text)
mymovies=mypage.find_all('div',attrs = {'class':'lister-item-content'})
```
Locate the content and name it as 'mymovies'.

>![](/assets/Screen Shot 2018-03-09 at 4.24.41 pm.png)
![](/assets/Screen Shot 2018-03-09 at 4.25.40 pm.png)

* So every item in 'mymovies' is a movie, which contains its header and rating like following. We need to find the information we want:

>![](/assets/Screen Shot 2018-03-09 at 4.18.42 pm.png)

* Next step is to have add these information in to the list.
* Create an empty list 'movie' in the former step 54. Then add `movie.append(mytitle,myrating)`
in the for loop, which means we add every movie's information into the list.
 
![](/assets/Screen Shot 2018-03-09 at 4.40.40 pm.png)


### Scrape:IMDB (version2)

>![](/assets/Screen Shot 2018-03-07 at 10.01.03 pm.png)

* Line 1-4 to import the module

>![](/assets/Screen Shot 2018-03-07 at 10.03.09 pm.png)

* Line 5-7 to get the text.
`request.get` means get response of the website.
`BeautifulSoup` is a function to understand to HTML content by the tool `html.parser`. 

>![](/assets/Screen Shot 2018-03-07 at 10.06.57 pm.png)

* Line 9-10 is to create 2 empty lists, which is a preparation step for Line16.

>![](/assets/Screen Shot 2018-03-07 at 10.10.49 pm.png)
![](/assets/Screen Shot 2018-03-07 at 10.07.26 pm.png)

* This part is to find the titles of the movie.
First, we locate the titles by `find_all('h3',attrs = {'class':'lister-item-header')`.

* If we don't use for loop, then will only find one 'a' tag, like the following picture.
![](/assets/Screen Shot 2018-03-09 at 4.03.04 pm.png)

* So we need a for loop: 
```
for title in titles:
  name = title.find('a')
  list_name.append(name.text)
```
* In this part, you can use every word you like to substitute 'title', like `for x in titles`. It is OK, as long as it is easy to understand. It means for every item in the 'titles',which we find in the last step, find 'a' tag ,and assign it to name.

* `append` means add something to a list. Every time you find an 'a' tag, define it as 'name'.Then add its text to the list 'list_name'. For loop is to apply this into every item in the 'titles'.

>![](/assets/Screen Shot 2018-03-09 at 4.08.46 pm.png)
![](/assets/Screen Shot 2018-03-09 at 3.58.13 pm.png)

* Line18-Line21 are the same as the previous part.

>![](/assets/Screen Shot 2018-03-09 at 4.11.59 pm.png)

* 

```
with open("movie.csv",'w') as f:
    writer = csv.writer(f)    
```
It means create a csv file called movie.csv.
* `len` means the length of the list.
For every items in the list, write the content in the format like the following:
```
writer.writerow([list_name[i],list_score[i]])
```
Every item in 'list_name' matches every item in 'list_score'.



# Submit homework on Github
* Register account on https://www.github.com

* Click the '+' to create a new repo.
![](/assets/Screen Shot 2018-03-09 at 3.38.06 pm.png) 


* Remember to create a 'readme' text by ticking the box in the picture.
![](/assets/Screen Shot 2018-03-09 at 3.37.51 pm.png) 

* Create folder name homework2 in your desktop, which contains your homework 'csv' and 'py' file, and drag your the folder into the window.
![](/assets/Screen Shot 2018-03-09 at 3.43.26 pm.png)
![](/assets/Screen Shot 2018-03-09 at 3.43.48 pm.png)

* Create a file at 'homework2/README.md' to briefly explain the dataset.








