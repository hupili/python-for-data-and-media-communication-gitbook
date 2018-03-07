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


### list and dictionary

```
list1=[1,2,3,4]
dictionary1={'title':'teacher', 'date':'2018/2/2'}
a=list1[0]
b=list1[1]
c=dictionary1['title']
```

The keys of dictionary1 are 'title' and 'date'. The value of dictionary1 are 'teacher' and '2018/2/2'. Every key has its own value. They are matched. 






### da da











