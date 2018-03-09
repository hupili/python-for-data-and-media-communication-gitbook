# Week 05

# Learn to use Jupyter
"cell" and "kernel" to make it more efficient

* cell
 
 `run cell` run step by step
 `run  all above` to run and check the previous steps of coding.
* kernel

  `kernel` is a tool for interactive input and output record all the things you did from the beginning.By clicing`restart`, you can give a variable another value.
  
  example:

    step 1 : `a=1` you give a a value,which equals to 1.
    step 2 : click`restart` you clear the value of a, which means a is not defined any more.
    step 3 : `print(a)`then you will find that the a is not defined, thus there is an error.

# csv
### Introduction
csv is an inside function in python, which is easy to read and write, You don't need to pip install csv in terminal. Just import csv before using it.
* example:
```
with open('NAME.csv','w',newline='') as f:      
    myWriter=csv.writer(f)  
    myWriter.writerow([7,'g'])  
    myWriter.writerow([8,'h'])  
    myList=[[1,2,3],[4,5,6]]  
    myWriter.writerows(myList)  
```   
The output will be a NAME.csv, whose contents are following:
![](/assets/Screen Shot 2018-03-07 at 7.26.06 pm.png)


* `with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening.

* `open()` means open the file. If there is no such file, it will create a new one. If there is a existing one, writer function will clear all the previous content and then  write the new content.

* `w` means write. By the way, if you want to read the file, you can input`r`,representing "read".

* `newline=' '` is one of the certain structure, which is used to avoid blank line.

* `csv.writer()` means to write something in the NAME.csv file.

* `writerow()` means wirte one row and then another row. The input should be list type.


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








