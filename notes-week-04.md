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

# List and dictionary


```
list1=[1,2,3,4]
dictionary1={'title':'teacher', 'date':'2018/2/2'}
a=list1[0]
b=list1[1]
c=dictionary1['title']
```
![](/assets/Screen Shot 2018-03-07 at 9.37.08 pm.png)

* Some functions may require you input a list. Others may require you input a dictionary.

* Every dictionary has its key and value. The keys of dictionary1 are 'title' and 'date'. The value of dictionary1 are 'teacher' and '2018/2/2'. Every key has its own value. They are matched. 


```
list2=[[(40.7,-74.0),'NY'],[(49.2,-123.1),'Vancouver']]
list3=[{'code':0001,'price':11,'P/E':21},
       {'code':0002,'price':15,'P/E':3},
       {'code':0003,'price':13,'P/E':50},
]
dictionary2={'title':['NY','HK','TK'],'rank':[1,2,3]}
```
* list and dictionary can be very complete.Please understand the structure above.
### Scrape:IMDB (version1)

* The page's HTML is following. There are many 'contents'

>![](/assets/Screen Shot 2018-03-09 at 4.30.50 pm.png)
![](/assets/Screen Shot 2018-03-09 at 4.29.03 pm.png)

* ```
r='http://www.imdb.com/list/ls058982125/'
mypage=bs4.BeautifulSoup(r.text)
mymovies=mypage.find_all('div',attrs = {'class':'lister-item-content'})
```
Locate the content and name it as 'mymovies'.

>![](/assets/Screen Shot 2018-03-09 at 4.24.41 pm.png)
![](/assets/Screen Shot 2018-03-09 at 4.25.40 pm.png)

* So every item in 'mymovies' is a movie, which contains its header and rating like following. We need to find the information we want:

>![](/assets/Screen Shot 2018-03-09 at 4.18.42 pm.png)

* Next step is to have add these information in to the list.
* Create an empty list 'movie' in the former step 54. Then add `movie.append(mytitle,myrating)`
in the for loop, which means we add every movie's information into the list.
 
![](/assets/Screen Shot 2018-03-09 at 4.40.40 pm.png)


### Scrape:IMDB (version2)

>![](/assets/Screen Shot 2018-03-07 at 10.01.03 pm.png)

* Line 1-4 to import the module

>![](/assets/Screen Shot 2018-03-07 at 10.03.09 pm.png)

* Line 5-7 to get the text.
`request.get` means get response of the website.
`BeautifulSoup` is a function to understand to HTML content by the tool `html.parser`. 

>![](/assets/Screen Shot 2018-03-07 at 10.06.57 pm.png)

* Line 9-10 is to create 2 empty lists, which is a preparation step for Line16.

>![](/assets/Screen Shot 2018-03-07 at 10.10.49 pm.png)
![](/assets/Screen Shot 2018-03-07 at 10.07.26 pm.png)

* This part is to find the titles of the movie.
First, we locate the titles by `find_all('h3',attrs = {'class':'lister-item-header')`.

* If we don't use for loop, then will only find one 'a' tag, like the following picture.
![](/assets/Screen Shot 2018-03-09 at 4.03.04 pm.png)

* So we need a for loop: 
```
for title in titles:
  name = title.find('a')
  list_name.append(name.text)
```
* In this part, you can use every word you like to substitute 'title', like `for x in titles`. It is OK, as long as it is easy to understand. It means for every item in the 'titles',which we find in the last step, find 'a' tag ,and assign it to name.

* `append` means add something to a list. Every time you find an 'a' tag, define it as 'name'.Then add its text to the list 'list_name'. For loop is to apply this into every item in the 'titles'.

>![](/assets/Screen Shot 2018-03-09 at 4.08.46 pm.png)
![](/assets/Screen Shot 2018-03-09 at 3.58.13 pm.png)

* Line18-Line21 are the same as the previous part.

>![](/assets/Screen Shot 2018-03-09 at 4.11.59 pm.png)

* 

```
with open("movie.csv",'w') as f:
    writer = csv.writer(f)    
```
It means create a csv file called movie.csv.
* `len` means the length of the list.
For every items in the list, write the content in the format like the following:
```
writer.writerow([list_name[i],list_score[i]])
```
Every item in 'list_name' matches every item in 'list_score'.



# Submit homework on Github
* Register account on https://www.github.com

* Click the '+' to create a new repo.
![](/assets/Screen Shot 2018-03-09 at 3.38.06 pm.png) 


* Remember to create a 'readme' text by ticking the box in the picture.
![](/assets/Screen Shot 2018-03-09 at 3.37.51 pm.png) 

* Create folder name homework2 in your desktop, which contains your homework 'csv' and 'py' file, and drag your the folder into the window.
![](/assets/Screen Shot 2018-03-09 at 3.43.26 pm.png)
![](/assets/Screen Shot 2018-03-09 at 3.43.48 pm.png)

* Create a file at 'homework2/README.md' to briefly explain the dataset.








