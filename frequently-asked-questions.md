# Other Frequently Asked Questions

<!-- TOC -->

- [Other Frequently Asked Questions](#other-frequently-asked-questions)
    - [Notes](#notes)
    - [Environment](#environment)
        - [Two basic modes of executing codes: script and interactive](#two-basic-modes-of-executing-codes-script-and-interactive)
        - [Setup virtual venv and install Jupyter Notebook](#setup-virtual-venv-and-install-jupyter-notebook)
        - [Install modules in venv, it's equivalent to install in Jupyter](#install-modules-in-venv-its-equivalent-to-install-in-jupyter)
    - [Tricks & Hot key](#tricks--hot-key)
        - [Restart kernel helps](#restart-kernel-helps)
    - [Frequently asked bugs](#frequently-asked-bugs)
        - [No such file or directory in jupyter or file xxx does not exist](#no-such-file-or-directory-in-jupyter-or-file-xxx-does-not-exist)
    - [Encoding & Decoding](#encoding--decoding)
        - [U+FEFF encoding issue](#ufeff-encoding-issue)
        - [Csv writer newline](#csv-writer-newline)
        - [Cannot read csv files downloaded from a website](#cannot-read-csv-files-downloaded-from-a-website)
        - [Cannot import list of files](#cannot-import-list-of-files)
        - [Expecting value: line 1 column 1 (char 0)](#expecting-value-line-1-column-1-char-0)
    - [Data extraction - slice elements when one of them may be None](#data-extraction---slice-elements-when-one-of-them-may-be-none)

<!-- /TOC -->

## Notes

This is the page for "other" uncategorised FAQs. When some problems of a new area appear, they are likely to arrive here as first stop. When there are enough number of Q/As under certain topic, they will be diverted to the page dedicated to that area.

The whole catalogue is the first entry point for usual readers. It can be found here: [FAQ Catalogue](README.md#faq-catalogue)

## Environment

### Two basic modes of executing codes: script and interactive

please see [here](notes-week-02.md#two-basic-modes-script-and-interactive)

### Setup virtual venv and install Jupyter Notebook

please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/module-jupyter.md#virtual-environment)

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

### Restart kernel helps

In the coding process, we may keep renaming the variables or adjust the sequences of the cells. In such circumstances, there might be errors arisen. Therefore, a good practice here is always try `restarting kernels` if encounter the weird errors.

## Frequently asked bugs

### No such file or directory in jupyter or file xxx does not exist

If you download the csv from some where, and you want to import it in Jupyter notebook. you should put the csv file in the folder where your venv folder are first. Usually, it's in the user path. All the files you write and read should in this folder. Another method is to type `pwd` in Jupyter, it will return the path, where you should put the file in.

## Encoding & Decoding

### U+FEFF encoding issue

CSV Sample output:

```text
['U+FEFF/name', 'id', 'gender', 'location', 'phone']
['Chico', '1742', 'M', 'KLN', '3344']
['Ri', '1743', 'F', 'LOS', '5168']
['Ivy', '1655', 'F', 'MK', '7323']
```

In some cases, the csv you read may have some encoding issue like the above.`U+FEFF` is the byte order mark, or BOM, and is used to tell the difference between big- and little-endian UTF-16 encoding. To omit BOM, just add a encoding line in the `with....open` command, as `with open('chapter4-example-name_list.csv',encoding='utf-8-sig') as f:`. Further reading about this [issue](https://stackoverflow.com/questions/17912307/u-ufeff-in-python-string).

### Csv writer newline

For more explanation, please refer to the documentation on the [open function](https://docs.python.org/3/library/functions.html#open)

### Cannot read csv files downloaded from a website

This error is usually raised as the following:

`UTF-8 cannot decode byte 0xff in postion x: invalid byte`

Solution:

First, try to copy and paste the contains/data to Google drive with a new sheet, and downloaded it as a new csv.

![Google drive new](assets/google-drive-new.png)
![Google drive new2](assets/google-drive-new-2.png)
![Google drive copy data](assets/google-drive-copy-data.png)
![Google drive download data](assets/google-drive-download-data.png)

Then, we can successfully read the data by the usual way.

```python
# -*- coding: utf-8 -*-
import pandas as pd
df = pd.read_csv('REITs.csv', 'rb')
```

![Read data successfully](assets/read-data-successfully.png)

### Cannot import list of files

For example, using `os.listdir` to import a list of files.

```python
def read_txt(path): #read files and get content
    all_text = []
    for file in os.listdir(path):
        f=open(file,"r")
        contents= f.read()
        all_text.append(contents)
    all_words = "".join(all_text)
    for ch in '\s+\.\!\/_,$%^*(+\"\')]+|[+——()?:【】“”‘’':
        words = all_words.replace(ch," ")
    return words
words = read_txt("text/") #pass your own file path that include list of .txt
```

Error: `'utf-8' codec can't decode byte 0x80 in position 3131`

Even though your files are encodes by `utf-8`, somehow it may still rising error above, you can using following solution in the terminal:

```bash
cd to desktop/chicoxyc/text #cd to the folder where your txt files are
ls -a #list all the files
rm .DS_Store #delete .DS_Store if there is any
```

### Expecting value: line 1 column 1 (char 0)

It's a common error of `JSONDecodeError` meaning that there is no JSON can be parsed. You need to check the response object before doing further processing.

For some specify example solutions, you can refer to [here](https://stackoverflow.com/questions/16573332/jsondecodeerror-expecting-value-line-1-column-1-char-0) .

<!-- TODO: This is not necessarily caused by encoding problem. sometimes malformed JSON format will also cause the problem. Try to bring up a concrete case. What did you send to the JSON decoder when the error arises? -->

## Data extraction - slice elements when one of them may be None

We can use list slicing, if...else or try...except to test the boundary condition and separate different elements we want.

example: following is the content of series `df['time_countries']`, and we want to get country and time separately.

```text
上映时间：1993-01-01
上映时间：1994-10-14(美国)
上映时间：1953-09-02(美国)
上映时间：1994-09-14(法国)
上映时间：1972-03-24(美国)
上映时间：1998-04-03
上映时间：1993-07-01(中国香港)
上映时间：2001-07-20(日本)
上映时间：1940-05-17(美国)
上映时间：1939-12-15(美国)
```

You might notice that some entries have no country, therefore we have to handle two different situations. `if...else` here can helps. We can see that countries starts from index 15 in the string, therefore, we can use 15 to set the condition.

```python
def get_country(x):
    #if length > 15, we first separate by (, get the second parts and then separate ), get the first part, which is pure countries name we want.
    #if length < 15, there is no countries, we return blank
    if len (x) > 15:
        return x.split('(')[1].split(')')[0]
    else:
        return''
df['country'] = df['time_countries'].apply(get_country)


def get_time(x):
    #every entries have time, therefore we dont need set condition here. We first separate by ：, get the second parts and then separate (, get the first part, which is pure time we want.
    return x.split('：')[1].split('(')[0]

df['time'] = df['time_countries'].apply(get_time)
```
