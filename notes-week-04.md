# JSON and API

## Objective

* Learn to use Jupyter notebook. All demos following this week will be conducted in Jupyter notebook.
* Understand API/ JSON and can retrieve data from online databases (twitter, GitHub, weibo, douban, ...)
* Understand basic file format like json and csv.
    * Be able to comfortably navigate through compound structures like {} and [].
    * Be able to comfortably use (multiple layer of) for-loop to re-format data.
    * Be able to use serialisers to handle input/ output to files.

The brief of Application Programming Interface (API):

Operate in client-and-server mode.
Client does not have to download the full volume of data from server. Only use the data on demand.
Server can handle intensive computations that not available by client.
Server can send updated data upon request.

## Learn to use Jupyter Notebook

### Installing the Jupyter Notebook

Please see to our [tutorial](/module-jupyter.md) of how to install and enter jupyter notebook.
![jupyter notebook example](/assets/jupyter-notebook-example.png)

### Basic usage

1. click `new` to create a new python 3 notebook
2. write codes like you usually do in text editors, and press `shift`+`return` to run the code. It will return the results or errors under the cell.
3. use `! pip3 install module_name` to install modules in jupyter notebook.
4. in front of every cell, there is an `in [ ]` sign, the number in `[]` means the sequences of cells, and if there is `*` in `[]`, means that this cell is still running, you can either wait it finish or click `stop` under the `kernel` to exit from the running,pressing `I` twice will also do the trick.
5. cell. `run cell` run step by step. `run all above` to run and check the previous steps of coding.
6. kernel. `kernel` is a tool for interactive input and output all the things you did from the beginning. By clicking`restart`, you can give a variable another value.

## CSV

The CSV (Comma Separated Values) format is the most common import and export format for spreadsheets and databases,just like `xlsx` file, which is used for storing your data and make it easy to read and write. You don't need to pip install csv in terminal. Just import csv before using it.

The csv has two basic functions: `reader` and `writer` .objects read and write.

### csv.reader

Return a reader object which will iterate over lines in the given csv file. Each row read from the csv file is returned as a list of strings. No automatic data type conversion is performed.

Suppose we have a csv file, `name_list.csv`, the content is as follows:

| name  | id   | gender | location | phone|
|-------|------|--------|----------|------|
| Chico | 1742 |    M   |  KLN     |  3344|
| Ri    | 1743 |    F   |  LOS     |  5168|
| Ivy   | 1655 |    F   |   MK     |  7323|

Example 1: How to read this csv?

```python
import csv
with open('name_list.csv', newline='') as f: # open csv
    rows = csv.reader(f) # read CSV
    for row in rows: #loop every row
        print(row)
```

```
Answer:
['name', 'id', 'gender', 'location', 'phone']
['Chico', '1742', 'M', 'KLN', '3344']
['Ri', '1743', 'F', 'LOS', '5168']
['Ivy', '1655', 'F', 'MK', '7323']
['', '', '', '', '']
```

**Note:**

* `with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening.

* `open()` means open the file. If there is no such file, it will create a new one. If there is a existing one, writer function will clear all the previous content and then write the new content.

* `newline=' '` is one of the certain structure, which is used to avoid blank line.

### csv.writer

Return a writer object responsible for converting the user’s data into delimited strings. Csvfile can be any object with a write() method. If csvfile is a file object, it should be opened with `newline=''`.

Example 2: How to write a csv?

```python
with open('NAME.csv','w',newline='') as f:
    mywriter=csv.writer(f)  #writer is the function to write something
    mywriter.writerow(['Chico','Male'])  #you can just use writer.writerow()
    mywriter.writerow(['Ri','Female'])  
    mylist=[['KLN',1742,3344],['Los',1743,5168]]  
    mywriter.writerows(mylist)  
```  

The output will be a NAME.csv, whose content is like this:
![write a csv](/assets/csv-write-a-csv.png)

**Note:**

* `w` means write. By the way, if you want to read the file, you can input`r`,representing "read".

* `csv.writer()` means to write something in the NAME.csv file.

* `writerow()` means write one row and then another row. The input should be list type. `writerows()` means they will write row after row until loop all the elements from a list.

* arguments in `writerow()` should be a list, because `csv` function treat a row as a list, therefore you should use`[]` to wrap up the argument.

### Exercise

1. Writerow ['hello','python'] in A1 in the csv table

```python
import csv
with open('hello.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerow(['hello','python']) #writerow('hello','python') won't work, you should put it in a list. Every item of the list will be write in a cell of the table.
```

2. Writerows

```python
import csv
with open('test1.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerows(['spam','1','22','333'])
```

![CSV write rows](/assets/csv-write-rows.png)

**Note:** `writerows()` means write all the rows in one time. It writes every item of the list into a row. Like we said, csv.writerow function treat a row as a list, for which it will regard the first row 'spam' as a list of items with 4 characters, or 4 strings. Then it is put in 4 columns. But if there are lists inside of list,`writerows()` function will recognize the word 'spam', following are examples:

```python
import csv
with open('test2.csv','w') as f:
    mywriter=csv.writer(f)
    mywriter.writerows([['spam','1'],['22','333'],['OK','Good']])
```

![CSV write rows2](/assets/csv-write-rows-2.png)
There are 3 items, or 3 lists, therefore it will output 3 rows. And inside each row, there are different items,So it will write each item in one cell.

## Json

>JSON (JavaScript Object Notation) is a lightweight data interchange format inspired by JavaScript object literal syntax.

* JSON is a syntax for storing and exchanging data.
* JSON is text, written with JavaScript object notation.

**What does json looks like?**

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

**Why to use json?**

The advantages of json:

1. The data size is small. Compared with XML(another) file type to store and exchange data, JSON is small in size and faster in passing.
2. The transmission speed is fast. JSON is much faster than XML.
3. Data format is simple, easy to read and write, and the format is compressed.
4. Easy to use with python, Json is a form of `k-v` structure.

In simple terms, json is a dict, which has keys, each key corresponds to a value. The middle is separated by `:` , the outermost is surrounded by `{}`, and the different key-value pairs are separated by `,`. Example like this

```python

{'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}
```

If there is a case where a Key corresponds to multiple values, use [] to include all the corresponding values.

```python
{'key1': ['v11', 'v12', 'v13'], 'key2': 'v22'}
```

Now you can go back to have a look of example 3, test yourself whether you have understand the json structure.

### Json functions

#### json.dump: Convert from Python to JSON

**Syntax**

```python
json.dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding="utf-8", default=None, sort_keys=False, **kw)
```

Don't be panic, we do not have to use those all parameters. Basically, you need to know those two.

1. If sort_keys is true (default: False), then the output of dictionaries will be sorted by key.
2. If ensure_ascii is true (the default), the output is guaranteed to have all incoming non-ASCII characters escaped like Chinese. If ensure_ascii is false, these characters will be output as-is.

Example 4:

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

```
Answer: '{"name": "ACME", "shares": 100, "price": 542.23}'
```

#### json.load: Convert from JSON to Python

**Syntax**

```python
json.load(fp, cls=None, object_hook=None, parse_float=None, parse_int=None, parse_constant=None, object_pairs_hook=None, **kw)
```

one thing you need to know - `parse_constant`, if specified, will be called with one of the following strings: '-Infinity', 'Infinity', 'NaN'. This can be used to raise an exception if invalid JSON numbers are encountered.

Example 5:

```python
import json
with open("json_test") as f:
     result=json.load(f)
result
```

```python
Answer:
{'dataset': {'test': {'data_set': 'test',
   'layout_x': 'tensor',
   'type': 'mnist'},
  'train': {'data_set': 'train', 'layout_x': 'tensor', 'type': 'mnist'}},
}
```

If you try to check the json decoded data, it is often difficult to know its structure by simple printing, especially when the data is nested deeply or contains a large number of fields. To solve this problem, you can use the `pprint()` function instead of the normal `print()` function. After you understand its structure, you can use `class['key']` to access the items.

```python
import json
import pprint
with open("json_test") as f:
     result=json.load(f)
pprint.pprint(result)
```

```python
{'dataset': {'test': {'data_set': 'test',
                      'layout_x': 'tensor',
                      'type': 'mnist'},
             'train': {'data_set': 'train',
                       'layout_x': 'tensor',
                       'type': 'mnist'}}}

```

### Requests

Requests are the primary module we use to crawl website and get the content.

#### Make a Request

Making a request is easy. First of all, import the `requests` module. Usually, we use `requests.get` to make a request for data.

```python
import requests
r = requests.get('http://www.imdb.com/list/ls058982125/') #2017 Movie List
```

Now, we have a Response object called r. We can get all the information we need from this object, information about the 2017 movie list.

### Response Content

After we get the response object r, we need to read the content of the server’s response. There are three ways  to read contents.

```python
import requests
r = requests.get('http://www.imdb.com/list/ls058982125/') #pass url in ()
r.text
r.json
r.content
```

If you want to return text data, use `r.text`.(Use mostly)

If you want to return json, use `r.json`

If you want to return pictures and files, use `r.content`, it will return the binary data.

### API

