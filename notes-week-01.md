# Week 01 - Terminal, Python, Jupyter Notebook

<div id="toc">

<!-- TOC -->

- [Week 01 - Terminal, Python, Jupyter Notebook](#week-01---terminal-python-jupyter-notebook)
    - [Objective of this week](#objective-of-this-week)
    - [About terminal on Mac](#about-terminal-on-mac)
        - [What is terminal on Mac？](#what-is-terminal-on-mac)
        - [What is the function of the terminal on Mac？](#what-is-the-function-of-the-terminal-on-mac)
        - [Why we need to use it？](#why-we-need-to-use-it)
        - [How to open terminal on MAC？](#how-to-open-terminal-on-mac)
    - [Shell commands](#shell-commands)
        - [Directory: Where you are](#directory-where-you-are)
        - [Create/delete/rename files and folders](#createdeleterename-files-and-folders)
        - [Get inline help in the command line](#get-inline-help-in-the-command-line)
            - [The `man` command](#the-man-command)
            - [Basic usage](#basic-usage)
        - [Bonus: Command return and command output](#bonus-command-return-and-command-output)
    - [Edit and execute python file](#edit-and-execute-python-file)
        - [Text editor](#text-editor)
        - [Install python 3](#install-python-3)
        - [Modify the `ex1.py` file by a text editor](#modify-the-ex1py-file-by-a-text-editor)
        - [Execute .py file](#execute-py-file)
    - [Familiar with python interactive mode](#familiar-with-python-interactive-mode)
        - [Python interpreter](#python-interpreter)
        - [Invoking the Interpreter](#invoking-the-interpreter)
        - [Two basic modes: script and interactive](#two-basic-modes-script-and-interactive)
            - [Execute an existing script interactively](#execute-an-existing-script-interactively)
    - [Learn to use Jupyter Notebook](#learn-to-use-jupyter-notebook)
        - [Virtual environment](#virtual-environment)
        - [Setup virtualenv and install Jupyter Notebook](#setup-virtualenv-and-install-jupyter-notebook)
        - [Basic usage](#basic-usage-1)
    - [Exercises and Challenges](#exercises-and-challenges)
    - [References and Further Readings](#references-and-further-readings)

<!-- /TOC -->

</div>

In this very first chapter, you will start a journey, swimming in the ocean of codes and data. During the following months, you may experience a staggering start, enjoyable progress or even deeply frustration. You have to step out your comfort zone, learning from each other and conquer the overwhelming information world with your persistence and intelligence. If you have the determination to accept this challenge, you will see a brand new yourself at the end of the course.

## Objective of this week

* Setup the Python environment. Please read [here](setup-environment.md).
* Learn what is terminal. Be able to navigate file system in Terminal using the shell.
* Create the first python script and execute it.
* Learn the interactive mode of Python interpreter -- convenient for rapid experimentation.
* Learn the Jupyter notebook -- our major working platform in following weeks.

## About terminal on Mac

### What is terminal on Mac？

Basically, Terminal is a shell which receives/sends input and output for command-line program.

### What is the function of the terminal on Mac？

The function of the terminal is very powerful, and all the basic operations of the system can be completed in terminal, such as modifying file permissions, hiding/displaying files, and so on.

### Why we need to use it？

* Many features of computers are not available in the graphical interface, only through the command line.
* Work can be more efficient with command-line scripts.

### How to open terminal on MAC？

* press **command+space** to open spotlight

![Chapter1-terminal search](/assets/terminal-search.png)

* search "terminal" to open terminal.

![Chapter1-terminal interface](/assets/terminal-interface.png)
When you open terminal, you can see these two lines. The first line represents the last time you log in. And the second line **xuyucandeMacbook-pro** shows your computer model. **~xuyucan** is your account/username. What you need to focus is notation `$` . Its the sign that you can input some commands, and after you click the return, the computer will send back the results in next line.

## Shell commands

Following are some elementary commands you should know in terminal.
![Chapter1-terminal commands](/assets/terminal-commands.png)

### Directory: Where you are

Please type often `pwd` and `ls` to know where you are. And use `cd` to the change the location.

* `ls` means listing, showing the files in current folder. e.g.:

  ```bash
  ~ xuyucan$ ls
  Applications    Library   chromedriver
  Calibre 书库    Movies    pandas
  Creative Cloud Files    Music   python-twitter
  Desktop   Pictures    venv
  Documents   Public
  Downloads   PycharmProjects
  ```

* `cd` xx means change directory to xx, or change to xx folder, and you can add the location after `cd`.

* `pwd` means print what directory, or show where you are
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
    17426316.py   hello.py    scrabe 2.py
    2_2.py    homework.py   scrabe.py
    Case1_Advanced.py   homework2.py    sight.py
    Case1_Fundamental.py    imdb.py   taiwan-comments.py
    H1.py   list.py   taiwan_earthquake.csv
    comments.csv    list2.py    taiwanearthquake.py
    ```
* Besides following `cd` with a explicit path, one can use those special notation as a shortcut to change-directory to some common locations:
  * `cd ~` or `cd` to return to home.  
  * `cd .` to go to current diretory.
  * `cd ..` to return back to the upper directory.
      ```bash
      python xuyucan$ cd ..
      desktop xuyucan$ cd ~
      ~ xuyucan$
      ```

### Create/delete/rename files and folders

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

![Chapter1-new folder](/assets/new-folder.png)  
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

### Get inline help in the command line

#### The `man` command

`man` - format and display the on-line manual pages, its helpful to get help and explanation from the official manual. It can be used to **display manual pages**, **search for occurrences of specific text**, and other useful functions.

If you specify section, man only looks in that section of the manual.  name  is  normally the  name of the manual page, which is typically the name of a command, function, or file.

#### Basic usage

Enter the manual page of any shell command:

```shell
man {command-name}
```

Frequent hotkeys in manual page window:

* Use `j` and `k` to move the page down/ up by one line.
* Use `ctrl+d` and `ctrl+u` to move down/ up by one-half screen.
* Use `q` to exit (return to shell prompt).

Following are several common use and examples:

* Display the usage of commands, like `ls`

```bash
$ man ls

LS(1)                     BSD General Commands Manual                    LS(1)

NAME
     ls -- list directory contents

SYNOPSIS
     ls [-ABCFGHLOPRSTUW@abcdefghiklmnopqrstuwx1] [file ...]

DESCRIPTION
     For each operand that names a file of a type other than directory, ls
     displays its name as well as any requested, associated information.  For
     each operand that names a file of type directory, ls displays the names
     of files contained within that directory, as well as any requested, asso-
     ciated information.

     If no operands are given, the contents of the current directory are dis-
     played.  If more than one operand is given, non-directory operands are
     displayed first; directory and non-directory operands are sorted sepa-
     rately and in lexicographical order.

     The following options are available:

     -@      Display extended attribute keys and sizes in long (-l) output.

     -1      (The numeric digit ``one''.)  Force output to be one entry per
             line.  This is the default when output is not to a terminal.
    ...
```

* List all chapters and their file path:  `-aw`

```bash
$ man -aw ls
/usr/share/man/man1/ls.1
$ man -aw printf
/usr/share/man/man1/printf.1
/usr/share/man/man3/printf.3
```

* Display the certain section of `printf`:  man + int + printf

```bash
$ man 3 printf

PRINTF(3)                BSD Library Functions Manual                PRINTF(3)

NAME
     printf, fprintf, sprintf, snprintf, asprintf, dprintf, vprintf, vfprintf,
     vsprintf, vsnprintf, vasprintf, vdprintf -- formatted output conversion

LIBRARY
     Standard C Library (libc, -lc)

SYNOPSIS
     #include <stdio.h>

     int
     printf(const char * restrict format, ...);

     int
     fprintf(FILE * restrict stream, const char * restrict format, ...);
     ...
```

* Display all the section of `printf`:  `-a`

```bash
man -a printf
```

* Search online manuals that contain the keyword: `-k`

```bash
man -k printf
```

* Search for files, whose name contain specified keywords: `-f`

```bash
man -k print
```

For more functions, you can type `man man` on terminal to see more.

### Bonus: Command return and command output

- Return value: it is a convention for UNIX-like system/ program to return a value upon completion of execution. The return value indicates whether the program executes as expected. Usually, the return value is `0`, meaning the execution is successful. If the return value is non-zero, it means an error ocurred and you should go check the error code with the mannual. One can use this command to check the return value of *the very last* command `echo $?`.
- Output: a command/ program can output information for the user. There are two output streams:
  - `stdout` -- "standard output" -- This is usually useful data for further processing, e.g. as input to next command, for the users to comprehend. Later of this section, you will see the first Python coding using `print()`. This `print()` basically writes texts to `stdout`.
  - `stderr` -- "standard error" -- This includes error information that can help the user to debug. By default, when you operate in a MAC Terminal, `stderr` and `stdout` are written to the same stream, so you can not distinguish them by eyesight. Interested readers can check [this discussion](https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file) to see how to divert the two streams.


## Edit and execute python file

### Text editor

Terminal is an interactive environment. The advantage of writing code inside is that you can get the result instantly, but the weakness is that you can't save it. When you want to run it again, you have to tap it again. This is why we need a text editor. In actual programming development, we always use a text editor to write the code and save it as a file, so that the computer can run repeatedly.
We recommend two text editors, [sublime](https://www.sublimetext.com/) and [visual studio code](https://code.visualstudio.com/)(*click to download*). Then you can edit a .py file by these editors by double clicking the file. MAC will open "TextEdit" by default editor. You can set one of those two editors as default editor if necessary.

### Install python 3

Python is a popular programming language that is widely used by beginners and longtime developers alike. Meanwhile, its the language that we learn in this course to scrape, clean, analyze, and visualize data.  And there are basically 2 main versions of python. Python 2 and 3. You can check the version using following command on your terminal:

```bash
python --version
```

In this course, we base our discussions and exercises on Python 3, you can check out the [difference between python 2 and 3](#difference-between-python-2-and-3) and the instruction for [installation of python 3](/setup-environment.md) in related materials in our gitbook *(if you have already set up the python 3, just ignore it)*.

### Modify the `ex1.py` file by a text editor

 `print` is a python language, which means print, or show the things that written in the files in the terminal. eg:`print ("hello")` on sublime to print the string hello.

![Chapter1-sublime](/assets/sublime-interface.png)

Press **Command+s** to save the file as "ex1.py" on desktop.

### Execute .py file

 `python ex1.py` on terminal to execute the file.

  ```bash
  desktop xuyucan$ python ex1.py
  hello
  ```

If the output is "2.x", you will need to try `python3`. For example, when you execute Python script, you need to type `python3 myscript.py` when our book uses `python myscript.py`.

## Familiar with python interactive mode

### Python interpreter

> An interpreter is a program that reads and executes code. This includes source code, pre-compiled code, and scripts. Basically, the Python interpreter is the application that runs your python script.

By default, Python source files are treated as encoded in UTF-8. But the standard library only uses ASCII characters for identifiers, a convention that any portable code should follow. To display all these characters properly, python interpreter will recognize that the file is UTF-8, and support all the characters in the file.

What the interpreter does in a nutshell:

1. Read the script line by line and converts that script into python byte code.
2. The interpreter then executes the file instruction by instruction, it is at this stage errors are created if your code generates such errors.

### Invoking the Interpreter

Typing the command `python` or `python3` on your terminal.
After that, you will see `>>>` notation which indicates you that you have already entered the interactive mode and the interpreter is waiting for your input. For instance:

```python
$ python3
>>> hello
hello
>>> 1 + 2
3
>>> a = 0
```

Type `control + d`， or use `quit()` function to the interpreter.

### Two basic modes: script and interactive

1. `The script mode` is the normal mode where the scripted and finished `.py` files are run in the Python interpreter.

2. `The interactive mode` is a command line shell which gives immediate feedback for each statement.

Differences between two modes：

* A `.py` file can only be executed in script mode, using `python3` + `filename.py` to run the file.
* In interactive mode, you can only enter one line and execute one line each time, while in script mode, you can execute all the code in the file at once by running the .py file directly.
* The interactive mode is primarily used to debug the code and testing.

#### Execute an existing script interactively

Sometimes, you have an existing script, maybe from past works or from others. You want to execute this script first but stays in the Python interpreter after that. In this way, the state of the interpreter, e.g. all the variables, will be fully preserved for your further exploration. One can use the `-i` option. The command line pattern is as follows:

```bash
python -i myscript.py
```

## Learn to use Jupyter Notebook

Jupyter notebook is originally called "IPython notebook" (interactive Python notebook), thus having the `.ipynb` suffix/ extention name of the the Jupyter notebook file.

It provides a web-based interface for you to interactively test and build Python codes. It is well suited for a bottom-up approach when buiding larger projects.

### Virtual environment

You will hear the term "environment" a lot of times when learning programming. It is a very broad term that refers to the context where the program is executed. The context can be time, operating system, current working folder, Python version, dependent module version, the status of system, the status of dependent components, ...

**TIP**: Two pieces of codes can act differently if the environments are different. When you find someone else's codes work but the same thing does not work at your side, it is a problem of "environment". Trouble shooting highly depends on experience and we will see a lot during the semester.

Python has a concept called virtual environment, "virtualenv" for short. You can use virtualenv to ensure the programs execute in the same environment. One common use case is to run Python2 and Python3 programs on the same computer. The system defaults to one of the major versions. However, you can use virtualenv to run some programs in Python2 and some programs in Python3. We also use virtualenv to ensure the dependent Python moduels are the same, whose version is usually specified in `requirements.txt`.

There are two commands to setup virtualenv:

* `virtualenv` -- old executable usually used in Python2.
* `pyvenv` -- the default and recommended way of setting up virtualenv in Python3. The tools is shipped with Python3 installation.

### Setup virtualenv and install Jupyter Notebook

If it's the first time you use jupyter notebook, you need create a virtual environment first. The following are the usual path to setup jupyter environment. For users in CVA 517 LAB, please see [here](#setup-jupyter-environment-in-cva517).

Step 1: Create virtual environment

```bash
pyvenv venv
```

Step 2: Enter virtual environment

```bash
source venv/bin/activate
```

Step 3: Install Jupyter notebook

```bash
pip3 install jupyter
```

Step 4: Enter Jupyter notebook

```bash
jupyter notebook
```

For details, Please see to our [tutorial](/module-jupyter.md) of how to install and enter jupyter notebook. The following is what jupyter notebook will look like.

![jupyter notebook example](/assets/jupyter-notebook-example.png)

### Basic usage

1. click `new` to create a new python 3 notebook
2. write codes like you usually do in text editors, and press `shift`+`return` to run the code. It will return the results or errors under the cell.
3. use `! pip3 install module_name` to install modules in jupyter notebook.
4. in front of every cell, there is an `in [ ]` sign, the number in `[]` means the sequences of cells, and if there is `*` in `[]`, means that this cell is still running, you can either wait it finish or click `stop` under the `kernel` to exit from the running,pressing `I` twice will also do the trick.
5. cell. `run cell` run step by step. `run all above` to run and check the previous steps of coding.
6. kernel. `kernel` is a tool for interactive input and output all the things you did from the beginning. By clicking`restart`, you can give a variable another value.


## Exercises and Challenges

- Write a Python script to output "Good evening" in the Terminal.
- Use shell commands to re-organise the notes you take from this course. We understand that you can do this very quickly in GUI (e.g. in Finder of OS X). Please try the command line way and make it part of your daily life.

## References and Further Readings

* [Terminal and shell commands (Chinese)](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)
* [Appendix A of "Learn Python the hard way"](https://learnpythonthehardway.org/python3/appendixa.html) - Suggest all students make some self-study of this tutorial. Being comfortable in shell environment can make one efficient in programming.

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)