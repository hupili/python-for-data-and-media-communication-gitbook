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

`with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening.
* `csv.writer()` means to write something in the NAME.csv file.

* `writerow()` means wirte one row and then another row. The input should be list type.

* example 1：

  `myWrite.writerow("hello")` 
  ![](/assets/Screen Shot 2018-03-07 at 8.18.06 pm.png)
  
  If you want to write "hello" in A1 in the excel table, you should code `myWrite.writerow(["hello"])`.
  ![](/assets/Screen Shot 2018-03-07 at 8.19.02 pm.png)

* example 2:
```
  import csv
with open('NAME.csv','w') as f:   
	myWriter=csv.writer(f)
	myWriter.writerow(['spam','1','2','3'])
	myWriter.writerow(['spam2','11','22','33'])
```
![](/assets/Screen Shot 2018-03-07 at 8.21.08 pm.png)
  

`writerows()` means write all the rows in one time. 



`writeheader()` means you a 











### da da





