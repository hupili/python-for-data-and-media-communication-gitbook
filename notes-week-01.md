# Week 01: Hand-on the Terminal

## Introduction
In this very first chapter, you will start a journey, swimming in the ocean of codes and data. During the following months, you may experience a staggering start, enjoyable progress or even deeply frustration. You have to step out your comfort zone, learning from each other and conquer the overwhlming information world with your persistence and intelligence. If you have the determination to accept this chanllenge, you will see a brand new yourself at the end of the course.
## Objective of this week
* Learn what is terminal, and use terminal to do certain simple tasks.

## 1. About terminal on Mac
### What is terminal on Mac？
Basically, Terminal is a shell which receive/send input and output for command-line program.
### What is the function of the terminal on Mac?
The function of the terminal is very powerful, and all the basic operations of the system can be completed in terminal, such as modifying file permissions, hiding/displaying files, and so on.
### Why we need to use it?
* Many features of computers are not available in the graphical interface, only through the command line.
* Work can be more efficient with command-line scripts.
### How to open terminal on MAC
* press **command+space** to open spotlight
* search "terminal" to open terminal.

![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13ckagp5j20g701swel.jpg) <br>
*Terminal interface*
## 2. Shell commands
Following are some elementary commands you should know in terminal.
### Directory: Where you are 
Please type often `pwd` and `ls` to know where you are. 
* `ls` means listing, showing the files in current folder.
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13e6cg8yj20fg01v0ss.jpg)

* `cd` means change directory, or change to a folder, and you can add the location after `cd`.

  eg:

     `cd desktop` to go to "desktop".<br>
    ![](https://ws1.sinaimg.cn/large/5b088c35gy1fo1c690shmj20eh015t8n.jpg)  
    
    `cd ~` or `cd `to return to home.<br>
    ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13ghb9grj20es012747.jpg)
    
    `cd desktop/17444519` <br>
    ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13j4q9jkj20dr00wwee.jpg)
    
    `cd .` to go to current diretory. 
    
    `cd ..` to return back to the upper directory.<br>
   ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13k20gw1j20ea00yglj.jpg)

* `pwd ` means print what directory, or show where you are.<br>
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13l2gwb2j20ep01g0sp.jpg)

### Creat/delete/rename files and folders 
Space separates the arguments and commands. So be careful.You can `ls` to check the new file or folder.
*(Make sure it exists.)*

* `touch` means creat a file
* `rm` means delete a file
eg:
  At first, `ls` to see files in current folder.
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13qeisecj20e700t0so.jpg)
  
  `touch ex1.py` to creat a file called "ex1.py",then `ls`.
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13qx0ejmj20ek01y3yl.jpg)
  
  `rm ex1.py` to remove a file called "ex1.py". 


* `mkdir` means creat a folder
* `rmdir` means delete a folder
eg:
  `ls`to see files in current folder.
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13sjhu6hj20ed016mx4.jpg)
  
  `mkdir Big_data` to creat a new directory, or a folder.
    ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13sucn5ej20f601v3ym.jpg)
    
  `rmdir Big_data` to remove the directory.

* `mv` means rename
eg:
  `mv ex1.py exercise.py` to rename "ex1.py" as "exercise.py".
  `mv 123 456`to rename "123" as "456".

## 3. Edit and execute python file:
You can open .py by double clicking the file.
*(If it doesn't work, you can download some third party editors,such as **sublime**, **visual studio code**. You can edit .py file by these editors.)*
* type something and save the file
 `print ` is a python language, which means print, or show the things that written in the files in the terminal.
eg:
  `print "hello"` on sublime to print the string hello.<br>
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13ui71hqj20at03fjre.jpg)
  *sublime interface* 
* press **command+S** to save the file as "ex1.py" on desktop.
  
### Execute .py file
  `python ex1.py`on terminal to execute the file.<br>
![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13vng40hj20f201vq2y.jpg)

