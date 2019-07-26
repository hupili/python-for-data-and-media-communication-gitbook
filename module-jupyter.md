# Jupyter

<!-- TOC -->

- [Jupyter](#jupyter)
  - [Virtual environment](#virtual-environment)
    - [Create virtual environment](#create-virtual-environment)
    - [Enter virtual environment](#enter-virtual-environment)
    - [Exit virtual environment](#exit-virtual-environment)
  - [Jupyter Notebook](#jupyter-notebook)
    - [Install Jupyter notebook](#install-jupyter-notebook)
    - [Run Jupyter notebook](#run-jupyter-notebook)
    - [Quit the Jupyter notebook](#quit-the-jupyter-notebook)
    - [Set jupyter environment in CVA517](#set-jupyter-environment-in-cva517)
  - [NBViewer](#nbviewer)
    - [How to use NBViewer to view the notebook online](#how-to-use-nbviewer-to-view-the-notebook-online)
    - [Codes on NBViewer is not updated](#codes-on-nbviewer-is-not-updated)
  - [Basic usage](#basic-usage)
  - [Runtime troubleshooting guide](#runtime-troubleshooting-guide)
  - [Install frequently used dependencies](#install-frequently-used-dependencies)
  - [Windows](#windows)
    - [Instructions of Installing Jupyter Notebook on Windows](#instructions-of-installing-jupyter-notebook-on-windows)
  - [Display charts in nbviwer](#display-charts-in-nbviwer)
    - [Import interactive charts in Jupyter notebook](#import-interactive-charts-in-jupyter-notebook)
    - [Cannot display some static charts](#cannot-display-some-static-charts)
  - [Run shell commands in Jupyter notebook](#run-shell-commands-in-jupyter-notebook)

<!-- /TOC -->

[Jupyter Notebook](http://jupyter.org/) is an open-source web application that allows you to create and share documents that contain live code, equations, visualizations and narrative text. In our course, Jupyter notebook will be our daily tool to write, test, and sharing our codes and works. It's very useful for us to learn and make **reproducible works**. The good advantage of Jupyter notebook includes:

- The Notebook has support for over 40 programming languages, including Python, R, Julia, and Scala.
- Notebooks can be shared with others using email, Dropbox, GitHub and the Jupyter Notebook Viewer.
- Your code can produce rich, interactive output: HTML, images, videos, LaTeX, and custom MIME types.

It is suggested to enter virtual environment before using Jupyter notebook. Because in the following study, we may need to install some packages and modules in Jupyter notebook. It's necessary to keep those files in the same path, so Jupyter can source the modules when you want to use.

## Virtual environment

The following are the usual path to setup jupyter environment. For users in CVA 517 LAB, please see [here](#set-jupyter-environment-in-cva517).

### Create virtual environment

```bash
pyvenv venv
```

### Enter virtual environment

```bash
source venv/bin/activate
```

When you see `(venv)` appear in front of your command line prompt, that means the you are in the virtual environment. Always check this prefix to make sure you are working in the right environment.

### Exit virtual environment

You can use `deactivate` command to exit current virtual environment.

## Jupyter Notebook

Now you can install and enter Jupyter notebook.

### Install Jupyter notebook

Note: **you only need to do this once for every virtual environment**

```bash
pip3 install jupyter
```

### Run Jupyter notebook

Always run your Jupyter notebook in the virtual environment.

```bash
jupyter notebook
```

By default the notebook will be available at [http://localhost:8888/tree](http://localhost:8888/tree)

So, next time when you use your jupyter notebook, you just need to type following commands in your terminal

```bash
source venv/bin/activate
jupyter notebook
```

### Quit the Jupyter notebook

```bash
$ control+C
```

Pay attention to the text. Then you will get the following picture. Please input `y` in 5 seconds.

![Jupyter Quit](assets/jupyter-quit-jupyter.png)

### Set jupyter environment in CVA517

Due to the jupyter and the python conflict, there are problems of installing jupyter by the usual way. Instead, the following will work. For more details explanation, please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/48).

```bash
pyvenv venv
source venv/bin/activate
pip install --upgrade pip
pip3 install jupyter
pip3 install 'ipython ==6.5.0'
pip3 install 'prompt-toolkit ==1.0.15'
```

## NBViewer

### How to use NBViewer to view the notebook online

You can use [NBViewer](https://nbviewer.jupyter.org/) to check out a Jupyter notebook hosted on GitHub. You only need to input the GitHub URL link into the input box.

### Codes on NBViewer is not updated

Sometimes, you change codes after first preview on NBViewer. You find the codes are updated on GitHub. However, NBViewer still shows the outdated codes used before. This is a common "cache" problem. You can try to trigger a cache invalidation by adding query string in the URL.

Suppose this is your original NBviewer link:

```text
https://nbviewer.jupyter.org/xxxxx/yyyyy.ipynb
```

You can add anything after the `?` mark:

```text
https://nbviewer.jupyter.org/xxxxx/yyyyy.ipynb?fffffff
```

The `fffffff` here can be arbitrary. Note, in your submission of the work, if the an NBviewer link is required, please paste the one that shows exactly the result you want, i.e. the one with some taililng querystring with which you can see the latest result. Or else, we may see the old content.

## Basic usage

1. click new to create a new python 3 notebook
2. write codes like you usually do in text editors, and press `shift+return` to run the code. It will return the results or errors under the cell.
3. use `! pip3 install module_name` to install modules in jupyter notebook.
4. in front of every cell, there is an in [ ] sign, the number in [] means the sequences of cells, and if there is * in [], means that this cell is still running, you can either wait it finish or click `stop` under the kernel to exit from the running, pressing `I` twice will also do the trick.
5. cell. run cell run step by step. run all above to run and check the previous steps of coding.
6. kernel. kernel is a tool for interactive input and output all the things you did from the beginning. By clicking `restart`, you can give a variable another value.
7. `type()` more to check the object. It is very useful when we write complicated codings. Eg:a = 1, type(a)
8. `help()` to know the details. Eg: help(str.strip)
9. `print` step by step to check where the error is. (In Jupyter, you can just input the variables without the function of print.) Like, type data in cell equals to print(data).

## Runtime troubleshooting guide

* Rerun all the cells
* Restart the kernel
* Clear the output cells

## Install frequently used dependencies

You do not want to install and re-install dependencies every time. It is more convenient to setup a virtual environment and install common dependencies/ modules for data analysis.

You can download this [requirement.txt](https://github.com/hupili/python-for-data-and-media-communication/blob/master/requirements.txt) and then run the following command (inside virtual environment)

```bash
pip install -r requirements.txt
```

## Windows

### Instructions of Installing Jupyter Notebook on Windows

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/30).

## Display charts in nbviwer

### Import interactive charts in Jupyter notebook

Different libraries to save `.html` locally.

```python
#plotly
plotly.offline.plot(data, filename='file name')
#pyecharts
bar/line.render('file name.html')
#bokeh
output_file("file name.html")
```

Import the html file it generate on your local computer.

```python
from IPython.display import IFrame
IFrame('file_name.html', width=700, height=400)
```

### Cannot display some static charts

This is caused by the temporary cache in the browser. The first solution is you can change another browser to visit the link. The second, add several `???` in the nbviwer link to refresh the link, then the chart will display correctly.

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)


## Run shell commands in Jupyter notebook

In **Jupyter notebook**, you can write shell commands after `!`. `cat` is essentially a shell command that reads the content of a file and output to the screen. It is a common way to check if the output (to a file) is intended. In [notes-week-01.md](notes-week-01.md), we have learned some useful commands like `cd`, `pwd` and `ls`. Those can all be used here. Also recall how we install new Python modules in a Jupyter notebook: `!pip install <package-name>`.
