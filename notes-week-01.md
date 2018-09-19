# Week 01 - Hands-on the Terminal

<div id="toc">

<!-- TOC -->

- [Week 01 - Hands-on the Terminal](#week-01---hands-on-the-terminal)
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
    - [Exercises and Challenges](#exercises-and-challenges)
    - [References and Further Readings](#references-and-further-readings)

<!-- /TOC -->

</div>

In this very first chapter, you will start a journey, swimming in the ocean of codes and data. During the following months, you may experience a staggering start, enjoyable progress or even deeply frustration. You have to step out your comfort zone, learning from each other and conquer the overwhelming information world with your persistence and intelligence. If you have the determination to accept this challenge, you will see a brand new yourself at the end of the course.

## Objective of this week

* Setup the Python environment. Please read [here](setup-environment.md).
* Learn what is terminal, Able to navigate file system in Terminal, using the shell.
* Create the first python script and execute it.

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

In this course, we base our discussions and exercises on Python 3, you can check out the [difference between python 2 and 3](/python-2-vs-python-3.md) and the instruction for [installation of python 3](/setup-environment.md) in related materials in our gitbook *(if you have already set up the python 3, just ignore it)*.

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

## Exercises and Challenges

- Write a Python script to output "Good evening" in the Terminal.
- Use shell commands to re-organise the notes you take from this course. We understand that you can do this very quickly in GUI (e.g. in Finder of OS X). Please try the command line way and make it part of your daily life.

## References and Further Readings

* [Terminal and shell commands (Chinese)](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)
* [Appendix A of "Learn Python the hard way"](https://learnpythonthehardway.org/python3/appendixa.html) - Suggest all students make some self-study of this tutorial. Being comfortable in shell environment can make one efficient in programming.

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)