# Get structured data: CSV, JSON and API

<div id="toc">

<!-- TOC -->

- [Get structured data: CSV, JSON and API](#get-structured-data-csv-json-and-api)
    - [Objective](#objective)
    - [Learn to use Jupyter Notebook](#learn-to-use-jupyter-notebook)
        - [Installing the Jupyter Notebook](#installing-the-jupyter-notebook)
        - [Basic usage](#basic-usage)
    - [File operation](#file-operation)
        - [write a file](#write-a-file)
        - [Read a file](#read-a-file)
        - [Append ()](#append-)
    - [CSV](#csv)
        - [csv.reader](#csvreader)
        - [csv.writer](#csvwriter)
            - [writerow](#writerow)
            - [writerows](#writerows)
        - [Exercise](#exercise)
    - [JSON](#json)
        - [JSON functions](#json-functions)
            - [json.dump: Convert from Python to JSON](#jsondump-convert-from-python-to-json)
            - [json.load: Convert from JSON to Python](#jsonload-convert-from-json-to-python)
    - [Requests](#requests)
        - [Make a Request](#make-a-request)
        - [Response Content](#response-content)
    - [API](#api)
        - [Why use api](#why-use-api)
        - [Use API via HTTP request/ response](#use-api-via-http-request-response)
        - [Use API via function calls to other modules/ packages](#use-api-via-function-calls-to-other-modules-packages)
    - [Exercises and Challenges](#exercises-and-challenges)

<!-- /TOC -->

</div>


## Objective

* Learn to use Jupyter notebook. All demos following this week will be conducted in Jupyter notebook.
* Understand API/ JSON and can retrieve data from online databases (twitter, GitHub, weibo, douban, ...)
* Understand basic file format like JSON and CSV.
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

If it's the first time you use jupyter notebook, you need create a virtual environment first. Please follow the 4 steps to correctly use jupyter notebook.

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

Then, next time, you can just type the following command to open jupyter notebook

```bash
source venv/bin/activate
jupyter notebook
```

For details, Please see to our [tutorial](/module-jupyter.md) of how to install and enter jupyter notebook.
![jupyter notebook example](/assets/jupyter-notebook-example.png)

### Basic usage

1. click `new` to create a new python 3 notebook
2. write codes like you usually do in text editors, and press `shift`+`return` to run the code. It will return the results or errors under the cell.
3. use `! pip3 install module_name` to install modules in jupyter notebook.
4. in front of every cell, there is an `in [ ]` sign, the number in `[]` means the sequences of cells, and if there is `*` in `[]`, means that this cell is still running, you can either wait it finish or click `stop` under the `kernel` to exit from the running,pressing `I` twice will also do the trick.
5. cell. `run cell` run step by step. `run all above` to run and check the previous steps of coding.
6. kernel. `kernel` is a tool for interactive input and output all the things you did from the beginning. By clicking`restart`, you can give a variable another value.

## File operation

### write a file

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

Output:

```text
['\ufeffname', 'id', 'gender', 'location', 'phone']
['Chico', '1742', 'M', 'KLN', '3344']
['Ri', '1743', 'F', 'LOS', '5168']
['Ivy', '1655', 'F', 'MK', '7323']
```

**Note:**

* `with open(...) as f` means you give f a definition, which stands for opening the file. In the example,`f` can be changed by any words you like. It just means you rename the step of the opening. It's equal to `f = open('chapter4-example-name_list.csv',mode='r')`.
* `open()` means open the file. If there is no such file, it will create a new one. If there is a existing one, writer function will clear all the previous content and then write the new content.
* You can see that in the beginning of the output, there is an encoding issue. `U+FEFF` is the byte order mark, or BOM, and is used to tell the difference between big- and little-endian UTF-16 encoding. To omit BOM, just add a encoding line in the `with....open` command, as `with open('chapter4-example-name_list.csv',encoding='utf-8-sig') as f:`. Further reading about this [issue](https://stackoverflow.com/questions/17912307/u-ufeff-in-python-string).

### csv.writer

Return a writer object responsible for converting the user’s data into delimited strings. CSV file can be any object with a write() method. If CSV file is a file object, it should be opened with `newline=''`. If `newline=''` is not specified, newlines embedded inside quoted fields will not be interpreted correctly, It should always be safe to specify newline='', since the csv module does its own (universal) newline handling.

Example 2: How to write a CSV file?

#### writerow

```python
import csv
with open('name.csv','w',newline='') as f:
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

#### writerows

**Method 1:**

```python
import csv
mylist=[['KLN',1742,3344],['Los',1743,5168]]  
with open('location.csv','w',newline='') as f:
    mywriter=csv.writer(f)
    mywriter.writerows(mylist) #if there are sub-list in the list
```

Output:
![write rows m1](/assets/csv-writer-writerows-m1.png)

**Method 2:**

```python
import csv
number_list = [11,22,33,44,55,66]
with open('number.csv','w',newline='') as f:
    mywriter=csv.writer(f)
    mywriter.writerows([[number] for number in number_list]) # equal to a for loop
```

Output:

![write rows m2](/assets/csv-writer-writerows-m2.png)

**Method 3:**

```python
student_list = ['Chico','Ri','Ken','Aaliyah','Voodoo']
with open('student.csv','w',newline='') as f:
    writer=csv.writer(f)
    for i in range(0,len(student_list)):
        writer.writerow(student_list[i])
```

Output:

![write rows m3](/assets/csv-writer-writerows-m3.png)

**Note:** I guess you already find what's wrong here.  `writerows()` means write all the rows in one time. It writes every item of the list into a row. Like we said, csv.writerow function treat a row as a list, for which it will regard the first row 'Chico' as a list of items with 5 characters, or 5 strings. Then it is put in 5 cells. So how to avoid spilt characters of a string into different cells?

Try change `writer=csv.writer(f)` to `writer=csv.writer(f,delimiter=' ')`, see what will happen.

### Exercise

1. Writerow ['hello','python'] in A1 in the CSV file

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

Example 5: load a JSON file, you can find it [here](assets/chapter4-json_test.json).

```python
import json
with open("chapter4-json_test.json","r") as f:
     result=json.load(f)
result
```

Output:

```python
{'dataset': {'test': {'data_set': 'test',
   'layout_x': 'tensor',
   'type': 'mnist'},
  'train': {'data_set': 'train', 'layout_x': 'tensor', 'type': 'mnist'}}}
```

If you try to check the JSON decoded data, it is often difficult to know its structure by simple printing, especially when the data is nested deeply or contains a large number of fields. To solve this problem, you can use the `pprint()` function instead of the normal `print()` function. After you understand its structure, you can use `class['key']` to access the items.

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

<!-- TODO: a high level restructure: use json.loads/ json.dumps for primary examples. This is to convert between Python internal data structure and "JSON string". If one wants to output the JSON string to a file, he simply write() the string with an open()-ed file. You can note that json.load/ json.dump are corresponding shortcuts -->

## Requests

Requests are the primary module we use to crawl website and get the content.

### Make a Request

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

If you want to return JSON, use `r.json`

If you want to return pictures and files, use `r.content`, it will return the binary data.

## API

Application Program Interfaces, or APIs, are commonly used to retrieve data from remote websites. Sites like Twitter, Douban and even government websites all offer certain data through their APIs. To use an API, you make a request to a remote web server, and retrieve the data you need.

### Why use api

Compared with other ways like download directly, APIs are useful in the following cases:

* The data is changing quickly. It doesn't need you to re-download it every minute - this will take a lot of bandwidth, and be pretty slow, the data we get through api is always up to date (unless you specify).
* Usually, the data sets return from APIs are usually can be directly convert to CSV or JSON, which is more structural and clean, you don't need to spend a lot of time to clean and find the data compared with request from `.html`.
* You can filter the data you want instead of download a large of data set.

Generally, different websites have different APIs methods to request the data. For example, the APIs of [USGS](https://earthquake.usgs.gov/fdsnws/event/1/) and [Douban](https://developers.douban.com/wiki/?title=api_v2) is a url, and you can change some parameters in the url to get the different data. While, the twitter api is a set of tokens and keys, you can call different functions to get different data.

### Use API via HTTP request/ response

So, in the following example, we'll be querying a simple API to retrieve data about the last 100 years' earthquakes that happen in Taiwan.

Step 1: Find it's API, and read it's documentation

API link : https://earthquake.usgs.gov/fdsnws/event/1/

Step 2: Set arguments and functions we want use

Functions:

* `query?`
* `count?`

Arguments:

* Start time: 1918-08-24
* End time: 2018-08-24
* Minlatitude: 21.890
* Minlongitude: 119.300
* Maxlatitude: 25.320
* Maxlongitude: 122.030

You can get 4 location parameters from [worldatlas](https://www.worldatlas.com/as/tw/where-is-taiwan.html)

Step 3: Create the API We want

```python
import requests
import csv

api_url = 'https://earthquake.usgs.gov/fdsnws/event/1/'
api_method = 'query?'
api_method_2 = 'count?'
api_format = 'format=geojson'
api_starttime = '1918-02-21'
api_endtime = '2018-02-21'
api_minlatitude = '21.890'
api_minlongitude = '119.300'
api_maxlatitude = '25.320'
api_maxlongitude = '122.030'

url = api_url + api_method + api_format + '&' + 'starttime=' + api_starttime + '&' + 'endtime=' + api_endtime + '&' + 'minlatitude=' + api_minlatitude + '&' + 'maxlatitude=' + api_maxlatitude +  '&' +'minlongitude=' + api_minlongitude + '&' + 'maxlongitude=' + api_maxlongitude
#prepare for calling query function

url_2 = api_url + api_method_2 + api_format + '&' + 'starttime=' + api_starttime + '&' + 'endtime=' + api_endtime + '&' + 'minlatitude=' + api_minlatitude + '&' + 'maxlatitude=' + api_maxlatitude +  '&' +'minlongitude=' + api_minlongitude + '&' + 'maxlongitude=' + api_maxlongitude
#prepare for calling count function
```

Step 4: Requests content

```python
response = requests.get(url)
response_2 = requests.get(url_2)

data = response.json() #convert to JSON
count = response_2.json()
print(count) #print count results
print(data) # print all data
```

Step 5:  Select the key values we want

```python
place = []
mag = []
time = []
for i in range(0,len(data['features'])):
    mag.append(data['features'][i]['properties']['mag']) # find magnitude of the earthquake
    place.append(data['features'][i]['properties']['place']) # find location
    time.append(data['features'][i]['properties']['time']) # find time
```

Step 6: Write data into CSV file

``` python
with open('taiwan_earthquake.csv','w',newline='') as f:
    writer = csv.writer(f)
    header = ['place','mag','time']
    writer.writerow(header)
    writer.writerows(zip(place,mag,time))
```

### Use API via function calls to other modules/ packages

<!-- TODO: The Python twitter example -->

## Exercises and Challenges

<!-- TODO: one exercise one subsection; try to describe some concrete tasks based on the API -->

* Taiwan had an earthquake in early Feb. Let's discuss this issue:
  * Search for the earthquake instances around Taiwan in recent 100 years and analyse the occurrences of earthquakes. You can refer to the same database used [here](https://dnnsociety.org/2017/09/02/map-of-sichuan-earthquake-in-d3/). Checkout the [API description](https://earthquake.usgs.gov/fdsnws/event/1/). The `count` and `query` API are useful.
  * Search on Twitter and collect user's discussions about this topic. See if there is any findings. You can approach from the human interface [here](https://twitter.com/search?q=%23台湾地震) \(hard mode\) or use [python-twitter](https://github.com/bear/python-twitter) module \(need to register developer and obtain API key\).
* Retrieve and analyse the recent movie. Douban's API will be helpful here.
  * [API sample for Recent movies](https://api.douban.com/v2/movie/in_theaters)
  * [API sample for movie details](https://api.douban.com/v2/movie/subject/26942674)
* Use Google Map API to retrieve geo-locaitons and canonical names: e.g. [Get the location of HKBU](https://maps.googleapis.com/maps/api/geocode/json?address=hong%20kong%20baptist%20university)
* Lookup real estate properties on HK gov open data portal. e.g. the [dataset page](https://data.gov.hk/en-data/dataset/centaline-centanetod-ccipropertyinfo/resource/4d3d7289-9d84-4f31-bf7e-a515d00d5328), the [API result](https://api.data.gov.hk/v1/filter?q=%7B%22resource%22%3A%22http%3A%2F%2Fhk.centanet.com%2Fopendata%2FCCI%2520Estate%2520for%2520Opendata.csv%22%2C%22section%22%3A1%2C%22format%22%3A%22json%22%2C%22sorts%22%3A%5B%5B9%2C%22desc%22%5D%5D%7D)
* blockchain.info provides a set of [API](https://www.blockchain.com/api) for one to retrieve information related with bitcoin transactions. Pick one wallet address, check its UTXO sets and sum up the values to get the total balance in this wallet.
* [A free crypocurrency API](https://min-api.cryptocompare.com/) for you to retrieve and study historical exchange rates.
* Implement a basic version of first automated writer - QuakeBot from LA Times
  * Get data from USGS API
  * Print a story to the screen using string templating/ string interpolation
  * See [here](https://gizmodo.com/quakebot-an-algorithm-that-writes-the-news-about-earth-1547182732) for an introduction of the bot. See [here](https://www.theregister.co.uk/2017/06/22/la_times_bot_spreads_fake_news/) for an incident and think how to avoid it?

  