# Chapter 1: Hands-on the Terminal

In this very first chapter, you will start a journey, swimming in the ocean of codes and data. During the following months, you may experience a staggering start, enjoyable progress or even deeply frustration. You have to step out your comfort zone, learning from each other and conquer the overwhelming information world with your persistence and intelligence. If you have the determination to accept this challenge, you will see a brand new yourself at the end of the course.

## Objective of this week

* Learn what is terminal, Able to navigate file system in Terminal, using the shell.
* Create the first python script and execute it.

## 1. About terminal on Mac

### What is terminal on Mac？

Basically, Terminal is a shell which receives/sends input and output for command-line program.

### What is the function of the terminal on Mac?

The function of the terminal is very powerful, and all the basic operations of the system can be completed in terminal, such as modifying file permissions, hiding/displaying files, and so on.

### Why we need to use it?

* Many features of computers are not available in the graphical interface, only through the command line.
* Work can be more efficient with command-line scripts.

### How to open terminal on MAC

* press **command+space** to open spotlight  
![](/assets/Chapter1-terminal%20search.png)
* search "terminal" to open terminal.
![](/assets/Chapter1-terminal%20interface.png) 
When you open terminal, you can see these two lines. The first line represents the last time you log in. And the second line **xuyucandeMacbook-pro** shows your computer model.**~xuyucan** is your account/username. What you need to focus is notation `$` . Its the sign that you can input some commands, and after you click the return, the computer will send back the results in next line.

## 2. Shell commands

Following are some elementary commands you should know in terminal.
![](/assets/Chapter1-terminal%20commands.png)

### Directory: Where you are 

Please type often `pwd` and `ls` to know where you are. And use `cd` to the change the location.

* `ls` means listing, showing the files in current folder. e.g.: 

  ```bash
  ~ xuyucan$ ls
  Applications		Library			chromedriver
  Calibre 书库		Movies			pandas
  Creative Cloud Files	Music			python-twitter
  Desktop			Pictures		venv
  Documents		Public
  Downloads		PycharmProjects
  ```

* `cd` xx means change directory to xx, or change to xx folder, and you can add the location after `cd`.

* `pwd ` means print what directory, or show where you are
  e.g.:
    ```bash
    ~ xuyucan$ cd Desktop
    desktop xuyucan$ pwd 
    /Users/xuyucan/desktop
    ```
  e.g.2: try to `cd` to a certain folder in your desktop. As for me, I have created a folder named python in my desktop within several .py files, and I `cd` to this folder and list the file in this folder.  
    ```bash  
    desktop xuyucan$ cd python
    python xuyucan$ ls
    17426316.py		hello.py		scrabe 2.py
    2_2.py			homework.py		scrabe.py
    Case1_Advanced.py	homework2.py		sight.py
    Case1_Fundamental.py	imdb.py			taiwan-comments.py
    H1.py			list.py			taiwan_earthquake.csv
    comments.csv		list2.py		taiwanearthquake.py
    ```
* Besides following `cd` with a explicit path, one can use those special notation as a shortcut to change-directory to some common locations:
  * `cd ~` or `cd ` to return to home.  
  * `cd .` to go to current diretory.
  * `cd ..` to return back to the upper directory.
      ```bash
      python xuyucan$ cd ..
      desktop xuyucan$ cd ~
      ~ xuyucan$
      ```

### Creat/delete/rename files and folders 

Space separates the arguments and commands. So be careful. You can `ls` to check the new file or folder. *(Make sure it exists.)*

* `touch` means to create a file
* `rm` means to delete a file
* `mkdir` means to create a folder
* `rmdir` means to delete a folder
* `mv` means to rename 

e.g.: At first, cd to desktop and create a new folder `big_data`

  ```bash
  ~ xuyucan$ cd desktop
  desktop xuyucan$ mkdir big_data
  ```

![](/assets/Chapter1-new%20folder.png)   
you can see the new folder in your desktop
then cd to `big_data` folder, create a new python file `ex1.py`, rename it as `exercise.py`, delete this file, and delete the `big_data` directory. During the process, you can check out whether the file/folder changed.
  ```bash
  desktop xuyucan$ cd big_data
  big_data xuyucan$ touch ex1.py
  big_data xuyucan$ mv ex1.py exercise.py
  big_data xuyucan$ rm exercise.py
  big_data xuyucan$ cd ..
  desktop xuyucan$ rmdir big_data
  ```

## 3. Edit and execute python file

### Text editor
Terminal is an interactive environment. The advantage of writing code inside is that you can get the result instantly, but the weakness is that you can't save it. When you want to run it again, you have to tap it again. This is why we need a text editor. In actual programming development, we always use a text editor to write the code and save it as a file, so that the computer can run repeatedly.
We recommend two text editors, [sublime](https://www.sublimetext.com/) and [visual studio code](https://code.visualstudio.com/)(*click to download*). Then you can edit a .py file by these editors by double clicking the file. MAC will open "TextEdit" by default editor. You can set one of those two editors as default editor if necessary.

### Install python 3
Python is a popular programming language that is widely used by beginners and longtime developers alike. Meanwhile, its the language that we learn in this course to scrape, clean, analyze, and visualize data.  And there are basically 2 main versions of python. Python 2 and 3. But in this course, we base our discussions and exercises on Python 3, and you can check out the [difference between python 2 and 3](/python-2-vs-python-3.md) and the instruction for [installation of python 3](/first-question.md).

* Modify the `ex1.py` file by a text editor.

  * `print ` is a python language, which means print, or show the things that written in the files in the terminal. eg:
  * `print ("hello")` on sublime to print the string hello.
![](/assets/Chapter1-sublime.png)  
  * Press **Command+s** to save the file as "ex1.py" on desktop.
  * Execute .py file
  `python ex1.py`on terminal to execute the file.
    ```bash
    desktop xuyucan$ python ex1.py
    hello
    ```

## Challenge

* Write a Python script to output "Good evening" in the Terminal.

## References and Further Readings

* [Terminal and shell commands (Chinese)](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)
* [Appendix A of "Learn Python the hard way"](https://learnpythonthehardway.org/python3/appendixa.html) - Suggest all students make some self-study of this tutorial. Being comfortable in shell environment can make one efficient in programming. 
