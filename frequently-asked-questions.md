# Frequently asked questions

<!-- TOC -->

- [Frequently asked questions](#frequently-asked-questions)
    - [Github](#github)
        - [why we should preview Jupyter notebook on NBview? Are there any relationship with Github?](#why-we-should-preview-jupyter-notebook-on-nbview-are-there-any-relationship-with-github)
        - [What is index.html](#what-is-indexhtml)
        - [How to change default branch for GitHub pages?](#how-to-change-default-branch-for-github-pages)
    - [Environment](#environment)
        - [Install python3](#install-python3)
        - [Difference between python 2 and 3](#difference-between-python-2-and-3)
        - [Different shell commands in Win and Mac](#different-shell-commands-in-win-and-mac)
        - [Two basic modes of shell: script and interactive](#two-basic-modes-of-shell-script-and-interactive)
        - [Install Python3 on Windows and Set Environment](#install-python3-on-windows-and-set-environment)
        - [Instructions of Installing Jupyter Notebook on Windows](#instructions-of-installing-jupyter-notebook-on-windows)
        - [pip install](#pip-install)
    - [Frequently asked bugs](#frequently-asked-bugs)
        - [No such file or directory in jupyter or file xxx does not exist](#no-such-file-or-directory-in-jupyter-or-file-xxx-does-not-exist)
    - [Tricks & Hot key](#tricks--hot-key)
    - [How to exit Python shell if entered accidentally](#how-to-exit-python-shell-if-entered-accidentally)
    - [Invalid ASCII character problem when executing a script](#invalid-ascii-character-problem-when-executing-a-script)
    - [MAC's TextEdit change quotes from ASCII character to unicode character (smart quotes)](#macs-textedit-change-quotes-from-ascii-character-to-unicode-character-smart-quotes)
    - [Declare file encoding other than the default](#declare-file-encoding-other-than-the-default)
    - [What is Terminal and what is shell](#what-is-terminal-and-what-is-shell)
    - [With or without ".py" extension name?](#with-or-without-py-extension-name)
    - [Check modules before enter PYVENV VENV](#check-modules-before-enter-pyvenv-venv)
    - [I already install some module before executing the Jupyter, why is this happen?](#i-already-install-some-module-before-executing-the-jupyter-why-is-this-happen)

<!-- /TOC -->
## Github

### why we should preview Jupyter notebook on NBview? Are there any relationship with Github?

One can directly preview a Python notebook on GitHub. However, GitHub prohibits Javascript execution for security reasons. If you have interactive chart, e.g. from `echart`, `plotly`, those will not render on GitHub. NBViewer supports javascript and it is the first free online tool to preview Python notebook, so we recommend it. For concrete examples of dynamic charts, @ChicoXYC can find one notebook from our project archive: https://github.com/data-projects-archive .

### What is index.html

Basically, index.html is the default file served by the web server. So it is equivalent to visit example.com and example.com/index.html. Naming your file as index.html can lead to this more concise notation in browser's address bar and in communication campaigns -- the naming in the world of web is usually the shorter the better. More explanations are [here](https://en.wikipedia.org/wiki/Webserver_directory_index) .

### How to change default branch for GitHub pages?

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/23)

## Environment

### Install python3

Please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/setup-environment.md)

### Difference between python 2 and 3

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/python-2-vs-python-3.md) 

### Different shell commands in Win and Mac

please see [here](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)

### Two basic modes of shell: script and interactive

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-02.md#two-basic-modes-script-and-interactive)

### Install Python3 on Windows and Set Environment

This question is usually accompanied by another problem/error:

```text
不是内部或外部命令，也不是可运行的程序或批处理文件
or
‘python’ is not recognized as an internal or external command
```

Details please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/32).

### Instructions of Installing Jupyter Notebook on Windows

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/30).

### pip install

## Frequently asked bugs

### No such file or directory in jupyter or file xxx does not exist

If you download the csv from some where, and you want to import it in Jupyter notebook. you should put the csv file in the folder where your venv folder are first. Usually, it's in the user path. All the files you write and read should in this folder. Another method is to type `pwd` in Jupyter, it will return the path, where you should put the file in.

## Tricks & Hot key

## How to exit Python shell if entered accidentally

Exit with a zero exit status: `quit()` or **Control-D** on Unix, **Control-Z** on Windows

## Invalid ASCII character problem when executing a script

Use **unicode\(\)** access to all registered Unicode codecs, then converted with **str\(\)**

## MAC's TextEdit change quotes from ASCII character to unicode character (smart quotes)

It is suggested to disable system wide smart quotes and smart dashes function. Read more [here](https://support.apple.com/kb/PH25635?viewlocale=en_GB&locale=en_GB).![](/assets/Screen Shot 2018-01-25 at 10.00.11 PM.png)

![](/assets/Screen Shot 2018-01-24 at 6.57.18 PM.png)

## Declare file encoding other than the default

To declare an encoding other than the default one, a special comment line should be added as the first line of the file. the syntax is as follows:

`#-*-coding: encoding -*-`

where encoding is one of the valid codes supported by Python.

For example, to declare that Windows-1252 encoding is to be used, the first line of your source code file should be:

`#-*-coding: cp-1251-*-`

One exception to the first line rule is when the source code starts with a UNIX"shebang" line. In this case, the encoding declaration should be added as the second line of the file. For example:

`#!/user/bin/env python`

`#-*-coding: cp-1251-*-`

## What is Terminal and what is shell

Terminal is a session which can receive and send input and output for command-line program.

Shell is a program which is used for controlling and running programs.

## With or without ".py" extension name?

Without the extension name, Visual Studio Code can not highlight the code:![](/assets/no py..jpeg)After adding to the extension name, the interface become normal:![](/assets/with py..jpeg)

## Check modules before enter PYVENV VENV

PYVENV means setting up a new VENV environment, and it probably erases some modules you installed previously.

So, if you have already entered ‘pyvenv venv’ before and deactivate, next time you use the same computer, you could enter ‘source venv/bin/activate’ to get into VENV environment, and ‘deactivate’ to exit VENV environment.

In the lab, you probably will change the seat and computer, before you enter the ‘VENV’ and use the Jupyter, you could check in the terminal to check whether the module is on the computer:

![](/assets/1.png)

and to check this module again:

![](/assets/2.png)

It means you successfully installed this module.
This situation is same to those modules: ‘requests’, ‘bs4’, etc.

## I already install some module before executing the Jupyter, why is this happen?

![](/assets/3.png)

Maybe you enter ’pyvenv venv’ again before you enter ‘jupyter notebook’, try to enter the ‘venv’ environment by typing ‘source venv/bin/activate’.

If it does not work, you could set up the ‘venv’ environment again by typing ’pyvenv venv’. Then install all the modules you will use before enter the ‘jupyter notebook’. Once you finish your work, use ‘deactivate’ to exit ‘venv’ environment. Do remember that you should use ‘source venv/bin/activate’ next time, not ‘pyvenv venv’.

