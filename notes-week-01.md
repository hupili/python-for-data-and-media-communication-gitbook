# Chapter 1: Hand-on the Terminal

In this very first chapter, you will start a journey, swimming in the ocean of codes and data. During the following months, you may experience a staggering start, enjoyable progress or even deeply frustration. You have to step out your comfort zone, learning from each other and conquer the overwhlming information world with your persistence and intelligence. If you have the determination to accept this chanllenge, you will see a brand new yourself at the end of the course.

## Objective of this week
* Learn what is terminal, Able to navigate file system in Terminal, using shell.
* Create the first python script and execute it.

## 1. About terminal on Mac
### What is terminal on Mac？
Basically, Terminal is a shell which receive/send input and output for command-line program.
### What is the function of the terminal on Mac?
The function of the terminal is very powerful, and all the basic operations of the system can be completed in terminal, such as modifying file permissions, hiding/displaying files, and so on.
### Why we need to use it?
* Many features of computers are not available in the graphical interface, only through the command line.
* Work can be more efficient with command-line scripts.
### How to open terminal on MAC
* press **command+space** to open spotlight<br>
![](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assets/terminal%20search%202018-07-20%20%E4%B8%8B%E5%8D%882.00.29.png)
* search "terminal" to open terminal.<br>
![](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assets/terminal%20interface%202018-07-20%20%E4%B8%8B%E5%8D%882.01.53.png) <br> 
## 2. Shell commands
Following are some elementary commands you should know in terminal.
![](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assets/terminal%20commands%202018-07-20%20%E4%B8%8B%E5%8D%882.48.27.png)
### Directory: Where you are 
Please type often `pwd` and `ls` to know where you are. 
* `ls` means listing, showing the files in current folder. ps:`$` represent this line is your input 
  ```bash
  $ ls
  Applications		Library			chromedriver
  Calibre 书库		Movies			pandas
  Creative Cloud Files	Music			python-twitter
  Desktop			Pictures		venv
  Documents		Public
  Downloads		PycharmProjects
  ```
* `cd` means change directory, or change to a folder, and you can add the location after `cd`.<br>
  `pwd ` means print what directory, or show where you are
  eg:<br>
    ```bash
    $ cd Desktop
    desktop$ pwd 
    /Users/xuyucan/desktop
                           // `cd ~` or `cd `to return to home.
                           // `cd python`, cd to a certain folder
    $ cd python
    python$ ls
    17426316.py		hello.py		scrabe 2.py
    2_2.py			homework.py		scrabe.py
    Case1_Advanced.py	homework2.py		sight.py
    Case1_Fundamental.py	imdb.py			taiwan-comments.py
    H1.py			list.py			taiwan_earthquake.csv
    comments.csv		list2.py		taiwanearthquake.py
  
                          // `cd .` to go to current diretory.
                          // `cd ..` to return back to the upper directory.
    python $ cd ..
    desktop$
    ```

### Creat/delete/rename files and folders 
Space separates the arguments and commands. So be careful.You can `ls` to check the new file or folder.
*(Make sure it exists.)*

* `touch` means creat a file
* `rm` means delete a file
* `mkdir` means creat a folder
* `rmdir` means delete a folder
* `mv` means rename
eg:
  At first, cd to desktop and creat a new folder `big_data`
  ```bush
  $ cd desktop
  desktop$ mkdir big_data
  ```
![](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assets/folder%202018-07-20%20%E4%B8%8B%E5%8D%884.25.42.png) you can see the new folder in your desktop
  then cd to `big_data` folder, creat a new python file `ex1.py`, rename it as `exercise.py`, delete this file, and delete the `big_data` directory. During the process, you can check out whther the file/folder changed.
  ```bush
  $ cd big_data
  big_data$ touch ex1.py
  big_data$ mv ex1.py exercise.py
  big_data$ rm exercise.py
  big_data$ cd ..
  desktop$ rmdir big_data
  ```

## 3. Edit and execute python file
You can open .py by double clicking the file.
*(If it doesn't work, you can download some third party editors,such as **sublime**, **visual studio code**. You can edit .py file by these editors.)*
* type something and save the file
 `print ` is a python language, which means print, or show the things that written in the files in the terminal.
eg:
  `print "hello"` on sublime to print the string hello.<br>
  ![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13ui71hqj20at03fjre.jpg)<br>
  *sublime interface* 
* press **command+S** to save the file as "ex1.py" on desktop.
  
### Execute .py file
  `python ex1.py`on terminal to execute the file.<br>
![](https://ws1.sinaimg.cn/large/5b088c35ly1fo13vng40hj20f201vq2y.jpg)

## Challenge
* Write a Python script to output "Good evening" in the Terminal.
## References
* [Terminal and shell commands (Chinese)](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)
* [Appendix A of "Learn Python the hard way"](https://learnpythonthehardway.org/python3/appendixa.html)
