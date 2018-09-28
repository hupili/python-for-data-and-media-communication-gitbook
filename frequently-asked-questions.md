# Frequently asked questions

<!-- TOC -->

- [Frequently asked questions](#frequently-asked-questions)
    - [Github](#github)
        - [why we should preview Jupyter notebook on NBview? Are there any relationship with Github?](#why-we-should-preview-jupyter-notebook-on-nbview-are-there-any-relationship-with-github)
        - [What is index.html](#what-is-indexhtml)
        - [How to change default branch for GitHub pages?](#how-to-change-default-branch-for-github-pages)
    - [Environment](#environment)
        - [What is Terminal and what is shell](#what-is-terminal-and-what-is-shell)
        - [Install python3](#install-python3)
        - [Difference between python 2 and 3](#difference-between-python-2-and-3)
        - [Different shell commands in Win and Mac](#different-shell-commands-in-win-and-mac)
        - [Two basic modes of shell: script and interactive](#two-basic-modes-of-shell-script-and-interactive)
        - [Install Python3 on Windows and Set Environment](#install-python3-on-windows-and-set-environment)
        - [Setup virtual venv and install Jupyter Notebook](#setup-virtual-venv-and-install-jupyter-notebook)
        - [Instructions of Installing Jupyter Notebook on Windows](#instructions-of-installing-jupyter-notebook-on-windows)
        - [Install pip3](#install-pip3)
        - [pip3 install modules](#pip3-install-modules)
        - [Install modules in venv, it's equivalent to install in Jupyter](#install-modules-in-venv-its-equivalent-to-install-in-jupyter)
    - [Tricks & Hot key](#tricks--hot-key)
    - [Frequently asked bugs](#frequently-asked-bugs)
        - [No such file or directory in jupyter or file xxx does not exist](#no-such-file-or-directory-in-jupyter-or-file-xxx-does-not-exist)
        - [Message: 'chromedriver' executable needs to be in PATH](#message-chromedriver-executable-needs-to-be-in-path)
    - [Encoding & Decoding](#encoding--decoding)
        - [Declare file encoding other than the default](#declare-file-encoding-other-than-the-default)
        - [Expecting value: line 1 column 1 (char 0)](#expecting-value-line-1-column-1-char-0)
    - [Useful knowledge](#useful-knowledge)
        - [How to apply twitter API key？](#how-to-apply-twitter-api-key)
        - [https status code](#https-status-code)

<!-- /TOC -->

## Github

### why we should preview Jupyter notebook on NBview? Are there any relationship with Github?

One can directly preview a Python notebook on GitHub. However, GitHub prohibits Javascript execution for security reasons. If you have interactive chart, e.g. from `echart`, `plotly`, those will not render on GitHub. NBViewer supports javascript and it is the first free online tool to preview Python notebook, so we recommend it. For concrete examples of dynamic charts, @ChicoXYC can find one notebook from our project archive: https://github.com/data-projects-archive .

### What is index.html

Basically, index.html is the default file served by the web server. So it is equivalent to visit example.com and example.com/index.html. Naming your file as index.html can lead to this more concise notation in browser's address bar and in communication campaigns -- the naming in the world of web is usually the shorter the better. More explanations are [here](https://en.wikipedia.org/wiki/Webserver_directory_index) .

### How to change default branch for GitHub pages?

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/23)

## Environment

### What is Terminal and what is shell

A terminal refers to a wrapper program which runs a shell.

The shell is the program which actually `processes commands` and `returns output`.

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

### Setup virtual venv and install Jupyter Notebook

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-04.md#setup-virtualenv-and-install-jupyter-notebook)

### Instructions of Installing Jupyter Notebook on Windows

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/30).

### Install pip3

pip is already installed if you are using Python 2 >=2.7.9 or Python 3 >=3.4. You can type python --version to check out current version. If you are the older versions, please check out [here](https://pip.pypa.io/en/stable/installing/) to install and upgrade pip.

If you install pip in anaconda environment, try to use `!conda install pip3` in Jupyter.

### pip3 install modules

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-02.md#step-1-pip-install-modules). If you install in Jupyter, add `!` ahead of the command.

### Install modules in venv, it's equivalent to install in Jupyter

If you are using Jupyter for the first time, you should create virtual environment first by `pyvenv venv`. Then enter the `venv` environment by typing `source venv/bin/activate`. This is the right place where you should install all the modules you will use, after that you can enter the Jupyter by command `jupyter notebook`. Once you finish your work, use `deactivate` to exit `venv` environment. Do remember, you just need to create virtual environment once, next time when you use Jupyter, just type`source venv/bin/activate` + `jupyter notebook` will work.

## Tricks & Hot key

1. Exit Python interactive mode: `quit()`,`exit()` or `Control-D` on Mac, `Control-Z` on Windows.
2. Auto supplementation when executing the code files: type the first letter of the file name then `tab`
3. Indent: `tab`
4. Indent back: `tab` + `shift`
5. Comment single line: `#` ahead of the line
6. Comment multiple lines: select multiple lines, then type `command` + `/`, type again to un-comment
7. Force quit boxes - `command`+`option`+`esc`

## Frequently asked bugs

### No such file or directory in jupyter or file xxx does not exist

If you download the csv from some where, and you want to import it in Jupyter notebook. you should put the csv file in the folder where your venv folder are first. Usually, it's in the user path. All the files you write and read should in this folder. Another method is to type `pwd` in Jupyter, it will return the path, where you should put the file in.

### Message: 'chromedriver' executable needs to be in PATH

Please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/notes-week-06.md#drivers) .

## Encoding & Decoding

### Declare file encoding other than the default

To declare an encoding other than the default one, a special comment line should be added as the first line of the file. the syntax is as follows:

`# coding=-*-`

For example, if you use `chinese` in your codes. It is better to declare the coding by writing the following as the first line in your source code file:

`# coding=utf-8` or `# -*- coding: utf-8 -*-`

There might be other situations and encoding format, and its a case by case situation, if you encounter more situation, please free feel to open an issue.

### Expecting value: line 1 column 1 (char 0)

It's a common error of `JSONDecodeError` meaning that there is no JSON can be parsed. You need to check the response object before doing further processing.

For some specify example solutions, you can refer to [here](https://stackoverflow.com/questions/16573332/jsondecodeerror-expecting-value-line-1-column-1-char-0) .

## Useful knowledge

### How to apply twitter API key？

Please see the applying experience of 2018 fall students [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/45). 

### https status code

When you make a request to a website, there might be different status responded. Common examples here:

- 200 OK
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden

For more examples, please refer to [here](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) .
