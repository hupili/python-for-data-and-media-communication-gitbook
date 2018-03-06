# Week 06 1-D and 2-D analysis

### 1. Preperations Before Data Analysis

**Notes:**

* Before learning, we will use jupyter notebook here, please enter venv environment first and enter into jupyter notebook.
* install pandas, seaborn, matplotlib, requests, csv
  ```
  pip install pandas
  ```

  ```
  pip install seaborn
  ```

  ```
  pip install matplotlib
  ```

### 2. Use "Pandas" to do Data Analysis

> Example: Today, We will use the data from Openrice as an example and do the restaurant analysis. Assuming that we have already got certain amount of data from Openrice and saved it into csv file.

**Step1: Save csv file**

* Here is the link of csv life and the csv needs to be downloaded here.

  https://github.com/hupili/python-for-data-and-media-communication/tree/master/w6-pandas
  ![](/assets/Screen Shot 2018-03-06 at 11.58.50 PM.png)
  
* Click "raw" on the right upper corner.
  ![](/assets/Screen Shot 2018-03-07 at 12.04.02 AM.png)
  
* You can see the raw csv file as below. 
  ![](/assets/Screen Shot 2018-03-07 at 12.05.46 AM.png)   
  
* Click right and choose "save as"
  ![](/assets/Screen Shot 2018-03-07 at 12.07.17 AM.png)
  
* Then the csv file can be saved as csv(comma-separated values).
  ![](/assets/Screen Shot 2018-03-07 at 12.07.40 AM.png)
  
** Step2: Read csv file**
* Put csv file into the same folder with venv.
* `import pandas`
* Read csv file 
  `pandas.read_csv('openrice.csv')`
* The output will be as below:
  ![](/assets/Screen Shot 2018-03-05 at 2.27.28 AM.png)
* If there is no header in the csv file.We can use `Pandas` as below to add proper headers for a form.
  ```
  df = pandas.read_csv('openrice.csv', header=None, names=['name', 'location', 'price', 'style', 'type', 'likes'])
  ```

  then the output will be like this:
  ![](/assets/Screen Shot 2018-03-05 at 2.38.15 AM.png)
  ** Notes:**
* `df`is short for "dataframe", is used in as return value in pandas.

**Step3: Select data from csv**

* If you want to the first 10 data from the csv file. then you can use

  ```
  df.head(10)
  ```

  the output will be as blow:
  ![](/assets/Screen Shot 2018-03-05 at 10.49.58 PM.png)

* If you want to select one column. You can use dataframe as a dictionary, use a key to refer to certain value. For example, you want all the restaurant locations.You can type:

  ```
  df['location']
  ```

  Then the output will be as below \(the picture do not show all the locations due to the limited space\):  
  ![](/assets/Screen Shot 2018-03-05 at 11.01.01 PM.png)

** Step4: Analysis just one dimension**

* One dimension is one column in a form.
* You can use   
  `df['location'].value_counts()`  
  then the output will be as below, showing you how many likes each restaurant have got.  
  ![](/assets/Screen Shot 2018-03-05 at 11.26.59 PM.png)
* Then you may need to calculate certain dimension. For example, how many likes that each restaurant have got. First, you will get all "likes" column data as follow:  
  ![](/assets/Screen Shot 2018-03-05 at 11.42.25 PM.png)  
  then, you need to to know the mean, media, percentile, min,max number of this dimension as below:  
  ![](/assets/Screen Shot 2018-03-05 at 11.49.50 PM.png)

* If you want to know how many restaurants having likes is 558, or less than 60, then you can use filter function:  
  `df[df['likes'] == 558]`  
  `df[df['likes'] < 60]`

  the output will be as below:  
  ![](/assets/Screen Shot 2018-03-05 at 11.57.14 PM.png)

* then you can put these filter data into a distribution, using  
  `df['likes'].hist()`  
  and you can get a distribution like below:  
  ![](/assets/Screen Shot 2018-03-06 at 12.08.05 AM.png)

* if you want to see change parameter, you can use  
  `df['likes'].hist(bins=20)`  
  ![](/assets/Screen Shot 2018-03-06 at 12.11.42 AM.png)

**Step5: How to describe distribution **

* After you get the distribution, you can do some analysis. Compare the distribution with mean, media numbers.
 ![](/assets/Screen Shot 2018-03-06 at 12.29.17 AM.png)
* If you need to compare price which is a interval.You need to pay special attention on numbers. Python recognize '$101-200'&lt;'$51-100' because Python only compare the   
  numbers in sequence of each interval.

  You need to convert each interval string into numbers, which means you need to choose a number to represent each interval to do comparison.  
  Here, we use "mapping" function

  ```
  mapping = {
    '$101-200': 200,
    '$201-400': 400,
    '$51-100': 100,
    '$401-800': 800,
    '$50以下': 50
  }
  ```

* Now, you can use:

  ```
    original_string = '$60以下'
    mapping.get(orignal_string, 0)
    def cleaning(e):
    return mapping.get(e, 0)
    cleaning('$50以下')
  ```

 ![](/assets/Screen Shot 2018-03-06 at 12.48.49 AM.png)

* Then you can use the coding below to transfer intervals into numbers.

  `df['price_num'].apply(cleaning)`

  ![](/assets/Screen Shot 2018-03-06 at 12.57.04 AM.png)

* If you want to select location of Mongkok.

  ```
    df1[
       df1['location'] == '旺角'
      ]
  ```

  the output will be:  
  ![](/assets/Screen Shot 2018-03-06 at 1.03.11 AM.png)

* If you want to select the seafood restaurants with price number less than 100.  
  ![](/assets/Screen Shot 2018-03-06 at 1.05.35 AM.png)

* If you want to sort price from high to low.
  ```
    df.sort_values(by='price_num', ascending=False)
  ```

  the output will be
  ![](/assets/Screen Shot 2018-03-06 at 1.10.13 AM.png)











