# Week 05 - Serialization: File, CSV, JSON

<div id="toc">

<!-- TOC -->

- [Week 05 - Serialization: File, CSV, JSON](#week-05---serialization-file-csv-json)
    - [Objective](#objective)
    - [Learn to use Jupyter Notebook](#learn-to-use-jupyter-notebook)
        - [Virtual environment](#virtual-environment)
        - [Setup virtualenv and install Jupyter Notebook](#setup-virtualenv-and-install-jupyter-notebook)
        - [Setup jupyter environment in CVA517](#setup-jupyter-environment-in-cva517)
        - [Basic usage](#basic-usage)
    - [File operation](#file-operation)
        - [Write a file](#write-a-file)
        - [Read a file](#read-a-file)
        - [Append ()](#append-)
    - [CSV](#csv)
        - [csv.reader](#csvreader)
        - [csv.writer](#csvwriter)
            - [Write row](#write-row)
            - [Write rows](#write-rows)
        - [Exercise](#exercise)
    - [JSON](#json)
        - [JSON functions](#json-functions)
            - [json.dumps: Serialize object to a JSON formatted str](#jsondumps-serialize-object-to-a-json-formatted-str)
            - [json.loads: Deserialize JSON str to a Python object](#jsonloads-deserialize-json-str-to-a-python-object)
            - [json.load & json dump](#jsonload--json-dump)
    - [Exercises and Challenges](#exercises-and-challenges)
    - [References](#references)

<!-- /TOC -->

</div>

Previously, we learned composite data types, and the basic control flows. This week, we will learns how to get data, convert data and save data. Before we step into scraping from the HTML, we will introduce a more convenient method - API. From this week on, you are gradually entering the door of "big data", the API allows you to get more types and a larger bass of data at the same time. After this week, you can use API method to request data from open data websites and social media platforms. And even create an automatic writing robot on Twitter.

## Objective

* Learn to use Jupyter notebook. All demos following this week will be conducted in Jupyter notebook.
* Understand API/ JSON and can retrieve data from online databases (twitter, GitHub, weibo, douban, ...)
* Understand basic file format like JSON and CSV.
    * Be able to comfortably navigate through compound structures like {} and [].
    * Be able to comfortably use (multiple layer of) for-loop to re-format data.
    * Be able to use serialisers to handle input/ output to files.

The brief of Application Programming Interface (API):

Operate in client-and-server mode.
Client does not have to download the full volume of data from server. Only use the data on demand.
Server can handle intensive computations that not available by client.
Server can send updated data upon request.

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

### Setup jupyter environment in CVA517

Due to the jupyter and the python conflict, there are problems of installing jupyter by the usual way. Instead, the following will work. For more details explanation, please see [here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/48).

```bash
pyvenv venv
source venv/bin/activate
pip install --upgrade pip
pip3 install jupyter
pip3 install 'ipython ==6.5.0'
pip3 install 'prompt-toolkit ==1.0.15'
```

Then, next time, you can just type the following command to open jupyter notebook

```bash
source venv/bin/activate
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

## File operation

### Write a file

Step 1: Create the file

```python
f = open("test.txt","w")
```

* You can write different kind of files by changing file name, like `name.txt`,`name.json`,`name.json`. But different file has different ways to write and read.
* ‘w' means write.

Step 2: Write content

```python
f.write('python tutorial')
f.close()
```

* f.close() to close the writing, this will close the instance of the file test.txt stored.

### Read a file

You also need to open the file first and then read the content.

**Syntax:**

```python
f = open("test.txt", "r+")
contents=f.read() #read all
content =f.read(6) #read first 6 characters
```

* ‘r' means read. 'r+' means it will read from the beginning, if you want to print certain part of the string, you should use this method.

### Append ()

The append function is used to append to the file instead of overwriting it. To append to an existing file, simply open the file in append mode ("a")

**Syntax:**

```python
h = open("Hello.txt", "a")
write("Hello World again")
h.close
```

## CSV

The CSV (Comma Separated Values) format is the most common import and export format for spreadsheets and databases,just like `xlsx` file, which is used for storing your data and make it easy to read and write. You don't need to pip3 install csv. Just `import csv` before using it.

The CSV has two basic functions: `reader` and `writer` .objects read and write.

### csv.reader

Return a reader object which will iterate over lines in the given CSV file. Each row read from the CSV file is returned as a list of strings. No automatic data type conversion is performed.

Suppose we have a CSV file, `name_list.csv`, you can download it [here](assets/chapter4-example-name_list.csv). The content is as follows:

| name  | id   | gender | location | phone|
|-------|------|--------|----------|------|
| Chico | 1742 |    M   |  KLN     |  3344|
| Ri    | 1743 |    F   |  LOS     |  5168|
| Ivy   | 1655 |    F   |   MK     |  7323|

Example 1: How to read this CSV?

```python
import csv
with open('chapter4-example-name_list.csv','r') as f: # open CSV
    rows = csv.reader(f) # read CSV
    for row in rows: #loop every row
        print(row)
```

Note: **If you download the csv, you should copy the csv file in the folder where your venv folder are. Usually, it's in the user path. All the files you write and read should in this folder.**

![Find your file](assets/jupyter-where-your-files-are.png)

Output:

```text
['name', 'id', 'gender', 'location', 'phone']
['Chico', '1742', 'M', 'KLN', '3344']
['Ri', '1743', 'F', 'LOS', '5168']
['Ivy', '1655', 'F', 'MK', '7323']
```

**Note:**

* `with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening. It's equal to `f = open('chapter4-example-name_list.csv',mode='r')`.
* `open()` means open the file. If there is no such file, it will create a new one. If there is a existing one, writer function will clear all the previous content and then write the new content.

### csv.writer

Return a writer object responsible for converting the user’s data into delimited strings. CSV file can be any object with a write() method.

Example 2: How to write a CSV file?

#### Write row

```python
import csv
with open('name.csv','w') as f:
    mywriter=csv.writer(f)  #writer is the function to write something
    mywriter.writerow(['Chico','Male'])  #you can just use writer.writerow()
    mywriter.writerow(['Ri','Female']) #write another row  
```

Output:
![write row](/assets/csv-writer-writerow.png)

**Note:**

* `w` means write. By the way, if you want to read the file, you can input`r`,representing "read".
* `csv.writer()` means to write something in the name.csv file.
* `writerow()` means write one row and then another row. The input should be list type. `writerows()` means they will write row after row until loop all the elements from a list.
* arguments in `writerow()` should be a list, because `csv` function treat a row as a list, therefore you should use`[]` to wrap up the argument.

#### Write rows

**Method 1:**

```python
import csv
mylist=[['KLN',1742,3344],['Los',1743,5168]]  
with open('location.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerows(mylist) #if there are sub-list in the list
```

Output:
![write rows m1](/assets/csv-writer-writerows-m1.png)

**Method 2:**

```python
import csv
number_list = [11,22,33,44,55,66]
with open('number.csv','w',) as f:
    mywriter=csv.writer(f)
    mywriter.writerows([[number] for number in number_list]) # equal to a for loop
```

Output:

![write rows m2](/assets/csv-writer-writerows-m2.png)

**Method 3:**

```python
student_list = ['Chico','Ri','Ken','Aaliyah','Voodoo']
with open('student.csv','w',) as f:
    writer=csv.writer(f)
    for i in range(0,len(student_list)):
        writer.writerow(student_list[i])
```

Output:

![write rows m3](/assets/csv-writer-writerows-m3.png)

**Note:** I guess you already find what's wrong here.  `writerows()` means write all the rows in one time. It writes every item of the list into a row. Like we said, csv.writerow function treat a row as a list, for which it will regard the first row 'Chico' as a list of items with 5 characters, or 5 strings. Then it is put in 5 cells. So how to avoid spilt characters of a string into different cells?

Try change `writer=csv.writer(f)` to `writer=csv.writer(f,delimiter=' ')`, see what will happen.

### Exercise

1. Write row ['hello','python'] in A1 in the CSV file

```python
import csv
with open('hello.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerow(['hello','python']) #writerow('hello','python') won't work, you should put it in a list. Every item of the list will be write in a cell of the table.
```

2. Use writerows to write [['spam','1'],['22','333'],['OK','Good']] in the CSV file

```python
import csv
with open('test.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerows([['spam','1'],['22','333'],['OK','Good']])
```

![CSV write rows2](/assets/csv-write-rows-2.png)
There are 3 items, or 3 lists, therefore it will output 3 rows. And inside each row, there are different items,So it will write each item in one cell.

## JSON

>JSON (JavaScript Object Notation) is a lightweight data interchange format inspired by JavaScript object literal syntax.

* JSON is a syntax for storing and exchanging data.
* JSON is text, written with JavaScript object notation.

**What does JSON looks like?**

Example 3:

```json
{
    "firstName": "Jane",
    "lastName": "Doe",
    "hobbies": ["running", "sky diving", "singing"],
    "age": 35,
    "children": [
        {
            "firstName": "Alice",
            "age": 6
        },
        {
            "firstName": "Bob",
            "age": 8
        }
    ]
}
```

**Why to use JSON?**

The advantages of JSON:

1. The data size is small. Compared with XML(another) file type to store and exchange data, JSON is small in size and faster in passing.
2. The transmission speed is fast. JSON is much faster than XML.
3. Data format is simple, easy to read and write, and the format is compressed.
4. Easy to use with python, JSON is a form of `k-v` structure.

In simple terms, JSON is a dict, which has keys, each key corresponds to a value. The middle is separated by `:` , the outermost is surrounded by `{}`, and the different key-value pairs are separated by `,`. Example like this

```python

{'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}
```

If there is a case where a Key corresponds to multiple values, use [] to include all the corresponding values.

```python
{'key1': ['v11', 'v12', 'v13'], 'key2': 'v22'}
```

Now you can go back to have a look of example 3, test yourself whether you have understand the JSON structure.

### JSON functions

#### json.dumps: Serialize object to a JSON formatted str

**Syntax**

```python
json.dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding="utf-8", default=None, sort_keys=False, **kw)
```

Don't be panic, we do not have to use those all parameters. Basically, you need to know those two.

1. If sort_keys is true (default: False), then the output of dictionaries will be sorted by key.
2. If ensure_ascii is true (the default), the output is guaranteed to have all incoming non-ASCII characters escaped like Chinese. If ensure_ascii is false, these characters will be output as-is.

Example 4: Convert Python object data into JSON string

```python
import json

data = {
    'name' : 'ACME',
    'shares' : 100,
    'price' : 542.23
}
json_str = json.dumps(data)
json_str
```

Output:

```txt
'{"name": "ACME", "shares": 100, "price": 542.23}'
```

If you want to save the JSON string to a file, so that others can re-use this file, you can use `open()` with the `.write()` function to achieve that.

```python
with open('json_data.json', "w") as f:
    f.write(json_str)
    f.close()
```

**TIP:** In **Jupyter notebook**, you can write shell commands after `!`. `cat` is essentially a shell command that reads the content of a file and output to the screen. It is a common way to check if the output (to a file) is intended. In [notes-week-01.md](notes-week-01.md), we have learned some useful commands like `cd`, `pwd` and `ls`. Those can all be used here. Also recall how we install new Python modules in a Jupyter notebook: `!pip install <package-name>`.

```shell
!cat json_data.json
```

```txt
{"name": "ACME", "shares": 100, "price": 542.23}
```

#### json.loads: Deserialize JSON str to a Python object

**Syntax**

```python
json.loads(s, *, encoding=None, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)
```

Example 5: Parse JSON string to Python internal data structure.

```python
json_str = '''
{
    "dataset": {
        "train": { "type": "mnist", "data_set": "train", "layout_x": "tensor" },
        "test": { "type": "mnist", "data_set": "test", "layout_x": "tensor" }
    }
}
'''

import json
result = json.loads(json_str)
```

**TIP**: when you write a large chunk of data in Python, this "multi-line string", "block string literal", or "verbatim" is very useful. It helps you to reserve all the format like indentations in the data. This feature appears in nearly all programming languages and the official name is [HEREDOC](https://en.wikipedia.org/wiki/Here_document#Python).

In the above example, you can `.read()` the `json_str` from a file instead of using HEREDOC. Try it yourself.

Output: the content (string representation) of `result`

```python
{'dataset': {'test': {'data_set': 'test',
   'layout_x': 'tensor',
   'type': 'mnist'},
  'train': {'data_set': 'train', 'layout_x': 'tensor', 'type': 'mnist'}}}
```

#### json.load & json dump

Actually, if we want to convert between json file with python object. We can directly use `json.load` & `json.dump`. The difference between `loads` and `load` or `dumps` and `dump` is that you can get the string by using `-s` method. And sometimes, we need those strings to do other things instead of justing writing into files.

Example 6: Converting between JSON file and Python object

```python
stu = {
    "age": 20,
    "score": 88,
    "name": "Bob"
}
with open('stu.json', 'w') as f:
    json.dump(stu, f) #converting Python object to JSON file
```

Open the stu.json file, it will output like:

```text
{"age": 20, "score": 88, "name": "Bob"}
```

```python
with open('stu.json', 'r') as f:
     data = json.load(f) #converting JSON file to Python object
data
```

Output:

```text
{"age": 20, "score": 88, "name": "Bob"}
```

## Exercises and Challenges

**TODO**

## References

* Python official doc about [json](https://docs.python.org/3/library/json.html)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)