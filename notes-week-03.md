# Week 3 Python for anything


## Objective

* Master the composite data type [] and {} in Python
* Master the control logics in Python, especially if and for
* Further understand the different roles of text editor and interpreter. Be comfortable writing batch codes in .py file and execute in Shell environment.
* [O] Understand Python engineering

## Use "Help" more to learn by yourself

In the Terminal of your computer, use `help` for any instruction for using Python functions.  

**Note**

* Type 'q' to quit help;
* Type 'j' to view up;
* Type 'k' to view down

Example 1: If you want to know how to use 'numpy'. Type`>>>help()`  and then type `numpy` , then you can get the information about numpy as follow:

```python
>>> import(numpy)
>>> help(numpy)
Help on package numpy:

NAME
    numpy

FILE
    /Library/Python/2.7/site-packages/numpy-override/numpy/__init__.py

DESCRIPTION
    NumPy
    =====

    Provides
        1. An array object of arbitrary homogeneous items
        2. Fast mathematical operations over arrays
        3. Linear Algebra, Fourier Transforms, Random Number Generation

    How to use the documentation
    ----------------------------
    Documentation is available in two forms: docstrings provided
    with the code, and a loose standing reference guide, available from
    `the NumPy homepage <http://www.scipy.org>`_.

:
```

## Bool and comparisons

### Comparison Operators

In programming, comparison operators are used to compare values and evaluate down to a single Boolean value of either True or False. The following are the common comparison operators:

| Operators| Meaning                  |
|----------|--------------------------|
| `==`     | Equal to                 |
| `!=`     | Not equal to             |
| `<`      | Less than                |
| `>`      | Greater than             |
| `<=`     | Less than or equal to    |
| `>=`     | Greater than or equal to |

### Str comparison

Strings can also be used with Boolean operators. They are case-sensitive. And you can use `str.()`functions to convert to upper- or lower-case letters.

Example 2:

```python
>>> Name1 = 'YUCAN'
>>> Name2 = 'yucan'
>>> Name3 = Name2.upper()
>>> print("Name1 == Name2: ", Name1 == Name2)
('Name1 == Name2: ', False)
>>> print("Name1 == Name3: ", Name1 == Name3)
('Name1 == Name3: ', True)
```

### Int comparison

Example 3:

```python
>>> x = 4
>>> y = 6

>>> print("x == y:", x == y)
('x == y:', False)
>>> print("x != y:", x != y)
('x != y:', True)
>>> print("x < y:", x < y)
('x < y:', True)
>>> print("x > y:", x > y)
('x > y:', False)
>>> print("x <= y:", x <= y)
('x <= y:', True)
>>> print("x >= y:", x >= y)
('x >= y:', False)
```

## Composite data types

Here are some common composite data types:

| Type   | Values                                     | Python Implementation |
|--------|--------------------------------------------|-----------------------|
| Array  | Mutable object containing other values     | list or []            |
| Union  | Contains values that can be multiple types | dict or {}            |
| Record | Immutable object containing other values   | tuple or ()           |

### List []

List is an ordered sequence of items. It is one of the most used datatype in Python and is very flexible. All the items in a list do not need to be of the same type.

Declaring a list is pretty simple. Items separated by commas are enclosed within brackets `[]`.

Example 4:

```python
>>> a = [0, 6.6, 'python']
```

#### Common features

1. Each element in the sequence is ordered and can be indexed. The first index is 0 and the second index is 1
2. Lists can be added and multiplied
3. One can add or remove elements into list
4. One can check whether one elements is in the list
5. One can slice the list

Example 5:

```python
>>> list1 = ['Hello', 'Python', 2018, 814]
>>> list2 = [1, 2, 3, 4, 5, 6, 7 ]
>>> print "list1[0]: ", list1[0] #first value in list1
list1[0]:  Hello
>>> print "list2[1:5]: ", list2[1:5] #second value to sixth value
list2[1:5]:  [2, 3, 4, 5]
>>> list1 + list2  
['Hello', 'Python', 2018, 814, 1, 2, 3, 4, 5, 6, 7]
>>> list1*2  #duplicate
['Hello', 'Python', 2018, 814, 'Hello', 'Python', 2018, 814]
>>> 2018 in list1  #check whether 2018 is in list1
true
>>> list2[3:] #slice list2 from index3 value to last value
[4, 5, 6, 7]
>>> list2[:2] #slice list2 from 1st to second value
[1, 2]
```

#### List functions

| Functions | Description                           |
|-----------|---------------------------------------|
| len(list) | Number of list elements               |
| max(list) | The maximum value in the list         |
| min(list) | The minimum value in the list element |

Example 6:

```python
>>> list2 = [1, 2, 3, 4, 5, 6, 7 ]
>>> len(list2)
7
>>> max(list2)
7
>>> min(list2)
1
```

#### List methods

| Methods   | Description                                                                  |
|-----------|------------------------------------------------------------------------------|
| append()  | Adds an element at the end of the list                                       |
| count()   | Returns the number of elements with the specified value                      |
| extend()  | Add the elements of a list (or any iterable), to the end of the current list |
| index()   | Returns the index of the first element with the specified value              |
| insert()  | Adds an element at the specified position                                    |
| pop()     | Removes the element at the specified position                                |
| remove()  | Removes the first item with the specified value                              |
| reverse() | Reverses the order of the list                                               |
| sort()    | Sorts the list                                                               |

Example 7:

```python
>>> list1 = ['Hello', 'Python', 2018, 814]
>>> list1.append(2049) #append() takes exactly one argument
>>> print(list1)
['Hello', 'Python', 2018, 814, 2049]
>>> list2 = [23, 2018, 814, 2049,2018]
>>> list2.count(2018)
>>> print(list2)
2
>>> list1.extend(list2)
>>> print("Extended List : ", list1)
Extended List : ['Hello', 'Python', 2018, 814, 2049, 23, 2018, 814, 2049, 2018]
>>> print("Index for python : ", list1.index('Python'))
1
>>> print("Index for 2018 : ", list1.index(2018)) #find the first position of the indexed value
2
>>> list1.insert(3, 2009) #list.insert(index, obj),insert value 2009 in the index3
>>> print("New List : ", list1)
New List :  ['Hello', 'Python', 2018, 814, 2049, 23, 2018, 814, 2049, 2018]
>>> list1.pop(2) #delete index2 value and return this value
>>> print('List now : ',list1)
List now :  ['Hello', 'Python', 814, 2049, 23, 2018, 814, 2049, 2018]
>>> list1.remove('Hello') #remove certain value
>>> print('List now : ',list1)
List now :  ['Python', 814, 2049, 23, 2018, 814, 2049, 2018]
>>> list1.reverse()
>>> print('reverse list : ',list1)
reverse list :  [2018, 2049, 814, 2018, 23, 2049, 814, 'Python']
>>> vowels = ['e', 'a', 'u', 'o', 'i']
>>> vowels.sort() #reverse = True(descending), reverse = False(ascending, if no parameters in(), they will return default value, ascending)
>>> print('vowels ascending : ',vowels)
vowels ascending :  ['a', 'e', 'i', 'o', 'u']
>>> vowels.sort(reverse = True)
>>> print('vowels descending : ',vowels)
vowels descending :  ['u', 'o', 'i', 'e', 'a']
```

### Dict {}

A dictionary is a collection which is unordered, changeable and indexed. In Python dictionaries are written with curly brackets`{}`, and they have keys and values, like `d = {key1 : value1, key2 : value2 }`.

Example 8:

```python
>>> dict1 = {
...  "apple": "green",
...  "banana": "yellow",
...  "cherry": "red"
...}
>>> print(dict1)
{'apple': 'green', 'banana': 'yellow', 'cherry': 'red'}
```

#### Common features

1. One can Access the values in the dict by `key`
2. Change dictionary by adding/deleting/updating key and values

Example 9:

```python
>>> person_dict = {'Chico': 24, 'Ivy': 20, 'Ri': 29}
>>> print('Chico : ',person_dict['Chico'])
Chico :  24
>>> person_dict['Ri'] = 19
>>> print('Ri : ',person_dict['Ri'])
Ri :  19
>>> person_dict['Frank'] = 31
>>> print('Frank : ',person_dict['Frank'])
Frank :  31
>>> del person_dict['Ivy'] #delete
>>> print('New_dict :',person_dict)
New_dict : {'Chico': 24, 'Ri': 19, 'Frank': 31}
```

#### Dict functions

| Functions | Description                           |
|-----------|---------------------------------------|
| len(dict) | Number of dict elements,which is the total number of keys               |
| str(dict) | Output dictionary as a string         |

Example 10:

```python
>>> person_dict = {'Chico': 24, 'Ri': 19, 'Frank': 31}
>>> len(person_dict)
3
>>> print("To String : %s" % str(person_dict))
To String : {'Chico': 24, 'Ri': 19, 'Frank': 31}
```

#### Dict methods

| Methods    | Description                                               |
|------------|-----------------------------------------------------------|
| fromkeys() | creates dictionary from given sequence                    |
| get()      | Returns value of the key                                  |
| items()    | Returns view of dictionary's (key, value) pair            |
| keys()     | Returns view object of all keys                           |
| get(key)   | Return the key value you get, default=None                |
| has_key()  | Return bool value by checking whether the key is in dict  |
| popitem()  | Returns & removes element from dictionary                 |
| pop()      | Returns & removes element having given key                |
| values()   | Returns view of all values in dictionary                  |
| update()   | Updates the Dictionary                                    |

## 2. Use "If-else Statement"

_**If-else statement**_ is used to conditionally execute a statement or a block of statements. Conditions can be true or false, execute one thing when the condition is true, something else when the condition is false. Take the case that group1 made as an example. \(The full version of the case is here：[https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/?from=timeline](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/?from=timeline］）) ）

> _Example_ _1:_  We want to know how much is the cost with the number of users we have.  When the number is less than 50,000, the cost will be 10,000. If the number is not less than 50,000, then cost=1000+0.1×（number\_of\_users -10000）. The actual number of users we have now is 100,000. The if-else statement will be as fellow:

```
number_of_users = 100000
if number_of_users < 50000:
    cost = 10000
else: # number_of_users >= 50000
    cost = 10000 + 0.1 * (number_of_users - 10000)
print (cost)
```

then you will get the cost in the terminal as `19000.0`

> _Example_ 2: If we add one condition. when the number of users is less than 50,000, cost is 10，000.  If then number is equal to or more than 50,000. Then there are other two situations:1. when  50,000≤the number of user&lt;100,000, the cost= 10000+0.1×\(number\_of\_\_\_users -10000\); 2. when the number of user ≥10,000,  cost=10000 + 5000 + 0.1 \* \(number\_of\_users - 10000\). The actual number of users we have now is 90,000. The if-else statement will be as fellow:

```
number_of_users = 90000
if number_of_users < 50000:
    cost = 10000
else: # number_of_users >= 50000
   if number_of_users<100000:
       cost=10000+0.1*(number_of_users-10000)
   else:
       cost = 10000 + 5000+ 0.1 * (number_of_users - 10000)
print (cost)
```

it will print `18000.0`

### 3. Use "For loop"/ "For Statement"

_**For loops\(For Statement\)**_ has the ability to iterate over the items of any sequence, such as a list or a string.

**1. Use "for statement" to pick up string/number from a list.**

> \_Example1: \_you want to list every integer from 1 to 10.

```
for i in range(1,10):
    print(i)
```

It will print `1,2,3,4,5,6,7,8,9`

> \_Example2: \_you want to list the square of every integer from 1 to 10.
>
> ```
> for i in range(1,10):
>     print(i**2)
> ```

it will print`1,4,9,16,25,36,49,64,81`

> \_Example3: \_you want to list number from numbers and string.

```
for number in [1, 5, 2, 'fun']: #(a list)
    print(number)
```

it will print `1,5,2`

**2. Use for loop to calculate.**

> \_Example1: \_you want to calculate the number of plussing from 1 to 100.
>
> ```
> total = 0
> for i in range(1, 101): # numbers which are >=1 and <101 
>     total = total + i
> print (total)
> ```
>
> it will print`5050`

### 4. Use "for statement" and "if-else statement" together

> _Example1: _ Like the example we used before. If we want to know the breakeven point of number of users, and we find that breakeven point of subscribed users is among 110,000 and 210,000, when the actual number of users we have is 190,000.

```
number_of_users = 190000
for number_of_users in range(110000, 210000):
    if number_of_users < 50000:
        cost = 10000
    else: # number_of_users >= 50000
        if number_of_users < 100000:
            cost = 10000 + 0.1 * (number_of_users - 50000)
        else: 
            cost = 10000 + 5000 + 0.05 * (number_of_users - 100000)
    revenue = 0.1 * number_of_users
    profit = revenue - cost
    if profit >= 0:
        break
print(profit)
print(number_of_users)
```

it will print `0.0` and `200000`

### 5. Use "Def function"

**Notes:**

* Keyword `def`\(means definite\) marks the start of function header.
* A function name to uniquely identify it.
* Parameters \(arguments\) through which we pass values to a function. They are optional.
* A colon \(:\) to mark the end of function header.
* Describe what the function does.
* Statements must have same indentation level \(usually 4 spaces\).
* An optional `return` statement to return a value from the function.

* Use when you find you are using a function again and again. you can use "def statement"to duplicate the logic.  
  Type "Tab“to move the section rightwards. Type"tab"+"Shift" to move the section leftwards.

> _Example1: _ If we want to calculate the profits, the cost is 10,000 when user is less than 50,000, or when the number is not less than 50000 and also less than 100,000, the cost=10000+0.1×\(number of users -50000\), or the cost= 10000 + 5000 + 0.05×\(number\_of\_users - 100000\) When the numbers of users are 100,1000 and 10,000 respectively.

```
def calculate_profit(number_of_users):
    if number_of_users < 50000:
        cost = 10000
    else: # number_of_users >= 50000
        if number_of_users < 100000:
            cost = 10000 + 0.1 * (number_of_users - 50000)
        else: 
            cost = 10000 + 5000 + 0.05 * (number_of_users - 100000)
    revenue = 0.1 * number_of_users
    profit = revenue - cost
    return profit
print(calculate_profit(100))
```

it will print `-9990.0`

The advantage of using "def" is that you can recall the function again and again.

```
def calculate_profit(number_of_users):
    if number_of_users < 50000:
        cost = 10000
    else: # number_of_users >= 50000
        if number_of_users < 100000:
            cost = 10000 + 0.1 * (number_of_users - 50000)
        else: 
            cost = 10000 + 5000 + 0.05 * (number_of_users - 100000)
    revenue = 0.1 * number_of_users
    profit = revenue - cost
    return profit
    print(calculate_profit(100))
```

it will print `-9990.0`

```
def calculate_profit(number_of_users):
    if number_of_users < 50000:
        cost = 10000
    else: # number_of_users >= 50000
        if number_of_users < 100000:
            cost = 10000 + 0.1 * (number_of_users - 50000)
        else: 
            cost = 10000 + 5000 + 0.05 * (number_of_users - 100000)
    revenue = 0.1 * number_of_users
    profit = revenue - cost
    return profit

print(calculate_profit(100))
print(calculate_profit(1000))
print(calculate_profit(10000))
print(calculate_profit(100000))
```

It will print `-9990`,`-9900`,`-9000`,`-5000` at a time.

### 6. Use "Import Statement"

**Notes:**

* To use any package in your code, you must first make it accessible. You have to import it. You can't use anything in Python before it is defined.

> _Example1:_ You want to pick up students randomly from a list named 1 to 6.

```
import random
students = [1, 2, 3 ,4, 5, 6] # l=[ , , ,]
print (students)
random.shuffle(students)
print (students)
```

it will print

```
[1, 2, 3, 4, 5, 6]
[2, 4, 1, 3, 5, 6]
```

## Exercise

**Q: Distances among cities:**

Calculate the "straight line" distance on earth surface from several source cities to Hong Kong. The source cities: New York, Vancouver, Stockholm, Buenos Aires, Perth. For each source city, print one line containing the name of the city and distance.

* "Great-circle distance" is the academic name you use to search for the formula.  
* Use list and for loop to handle multiple cities  
* Use function to increase the reusability

** A:** \(One possible solution\)

```
# -*- coding: utf-8 -*-

import math

cities = [
    { 'lat': 40.785091, 'lon': -73.968285, 'name': 'New York' },
    { 'lat': -123.12073750000002, 'lon': 49.2827291, 'name': 'Vancouver' },
    { 'lat': 59.336559, 'lon': 18.062660, 'name': 'Stockholm' },
    { 'lat': -34.603722, 'lon': -58.381592, 'name': 'Buenos Aires' },
    { 'lat': -31.953512, 'lon': 115.857048, 'name': 'Perth' }
]

def distance(lat1, lon1, lat2, lon2):
    r = 6371.009

    lat1 = math.radians(lat1)
    lon1 = math.radians(lon1)
    lat2 = math.radians(lat2)
    lon2 = math.radians(lon2)
    londelta = lon2 - lon1

    a = math.pow(math.cos(lat2) * math.sin(londelta), 2) + math.pow(math.cos(lat1) * math.sin(lat2) - math.sin(lat1) * math.cos(lat2) * math.cos(londelta), 2)
    b = math.sin(lat1) * math.sin(lat2) + math.cos(lat1) * math.cos(lat2) * math.cos(londelta)
    angle = math.atan2(math.sqrt(a), b)

    return angle * r

def distanceToHK(city):
    hk = { 'lat': 22.286394, 'lon': 114.149139 }
    di = distance(city['lat'], city['lon'], hk['lat'], hk['lon'])
    print ("Distance from %s to Hong Kong is %f KM." % (city['name'], di))

if __name__ == '__main__':
    for city in cities:
        distanceToHK(city)
```

it will print

```
Distance from New York to Hong Kong is 12951.815192 KM.
Distance from Vancouver to Hong Kong is 13584.132126 KM.
Distance from Stockholm to Hong Kong is 8224.867416 KM.
Distance from Buenos Aires to Hong Kong is 18464.264219 KM.
Distance from Perth to Hong Kong is 6033.948760 KM.
```



