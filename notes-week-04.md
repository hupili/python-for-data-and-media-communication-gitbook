# Week 04: Data Structure

<div id="toc">

<!-- TOC -->

- [Week 04: Data Structure](#week-04-data-structure)
    - [Composite data types (collection)](#composite-data-types-collection)
        - [List []](#list-)
            - [Common features of list](#common-features-of-list)
            - [List functions](#list-functions)
            - [List methods](#list-methods)
            - [in operator on list](#in-operator-on-list)
            - [List slicing](#list-slicing)
        - [Dict {}](#dict-)
            - [Common features of dict](#common-features-of-dict)
            - [Dict functions](#dict-functions)
            - [Dict methods](#dict-methods)
            - [in operator in dict](#in-operator-in-dict)
        - [Tuple ()](#tuple-)
        - [Bonus: Copy collection objects](#bonus-copy-collection-objects)
    - [Bonus: Class and objects](#bonus-class-and-objects)
        - [Create a class, the init() function](#create-a-class-the-init-function)
        - [Bonus: Class inheritance](#bonus-class-inheritance)
    - [Exercises and Challenges](#exercises-and-challenges)
        - [Divide HW1 groups randomly: (case contribution)](#divide-hw1-groups-randomly-case-contribution)
            - [Hint for group assignment challenge](#hint-for-group-assignment-challenge)
        - [Simple word frequency](#simple-word-frequency)
            - [Bonus: pretty print in ordered format](#bonus-pretty-print-in-ordered-format)
            - [Bonus: Use the Counter class](#bonus-use-the-counter-class)
        - [Convert Hong Kong district names into a convenient data structure](#convert-hong-kong-district-names-into-a-convenient-data-structure)
        - [Conversion between simplified Chinese and traditional Chinese](#conversion-between-simplified-chinese-and-traditional-chinese)

<!-- /TOC -->

</div>

## Composite data types (collection)

Here are some common composite data types:

| Type   | Values                                     | Python Implementation |
|--------|--------------------------------------------|-----------------------|
| Array  | Mutable object containing other values     | list or []            |
| Union  | Contains values that can be multiple types | dict or {}            |
| Record | Immutable object containing other values   | tuple or ()           |

### List []

List is an ordered sequence of items. It is one of the most used datatype in Python and is very flexible. All the items in a list do not need to be of the same type.

Declaring a list is pretty simple. Items separated by commas are enclosed within brackets `[]`.

Example 5:

```python
>>> a = [0, 6.6, 'python']
```

#### Common features of list

1. Each element in the sequence is ordered and can be indexed. The first index is 0 and the second index is 1
2. Lists can be added and multiplied
3. One can add or remove elements into list
4. One can check whether one elements is in the list
5. One can slice the list

**Note:** We talk about `index` in chapter 2, for those who forget how it works, please refer to [here](/notes-week-02.md#about-index-in-data-types)

Example 6:

```python
>>> test_list = ['Hello', 'Python', 2018, 814]
>>> test_list2 = [1, 2, 3, 4, 5, 6, 7 ]
>>> print ("test_list[0]: ", test_list[0]) #index[0] in test_list
test_list[0]:  Hello
>>> print ("test_list2[1:5]: ", test_list2[1:5]) #index[1] to index[5] but does not include index5 value.
test_list2[1:5]:  [2, 3, 4, 5]
>>> test_list + test_list2  
['Hello', 'Python', 2018, 814, 1, 2, 3, 4, 5, 6, 7]
>>> test_list*2  #duplicate
['Hello', 'Python', 2018, 814, 'Hello', 'Python', 2018, 814]
>>> 2018 in test_list  #check whether 2018 is in test_list
true
```

#### List functions

| Functions | Description                           |
|-----------|---------------------------------------|
| len(list) | Number of list elements               |
| max(list) | The maximum value in the list         |
| min(list) | The minimum value in the list element |

Example 7:

```python
>>> test_list2 = [1, 2, 3, 4, 5, 6, 7 ]
>>> len(test_list2)
7
>>> max(test_list2)
7
>>> min(test_list2)
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

Example 8: All examples are corresponding to the list methods stated above.

```python
>>> test_list = ['Hello', 'Python', 2018, 814]
>>> test_list.append(2049) #append() takes exactly one argument
>>> print(test_list)
['Hello', 'Python', 2018, 814, 2049]
```

```python
>>> test_list2 = [23, 2018, 814, 2049,2018]
>>> test_list2.count(2018) #count numbers of 2018
2
```

```python
>>> test_list.extend(test_list2) #add test_list2 into test_list
>>> print("Extended List : ", test_list)
Extended List : ['Hello', 'Python', 2018, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> print("Index for python : ", test_list.index('Python'))
1 #index value 'Python'
>>> print("Index for 2018 : ", test_list.index(2018)) #find the first position of the indexed value
2
```

```python
>>> test_list = ['Hello', 'Python', 2018, 814, 23, 2018, 814, 2049, 2018]
>>> test_list.insert(3, 2009) #list.insert(index, object),insert value 2009 in the index3
>>> print("New List : ", test_list)
New List :  ['Hello', 'Python', 2018, 2009, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> test_list = ['Hello', 'Python', 2018, 2009, 814, 23, 2018, 814, 2049, 2018]
>>> test_list.pop(2) #delete index2 value and return this value
>>> print('List now : ',test_list)
List now :  ['Hello', 'Python', 2009, 814, 23, 2018, 814, 2049, 2018]
>>> test_list.remove('Hello') #remove certain value
>>> print('List now : ',test_list)
List now :  ['Python', 2009, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> test_list = ['Python', 2009, 814, 23, 2018, 814, 2049, 2018]
>>> test_list.reverse() #reverse list
>>> print('reverse list : ',test_list)
reverse test_list :  [2018, 2049, 814, 2018, 23, 814, 2009, 'Python']
```

```python
>>> vowels = ['e', 'a', 'u', 'o', 'i']
>>> vowels.sort() #reverse = True(descending), reverse = False(ascending, if no parameters in(), they will return default value, ascending)
>>> vowels
['a', 'e', 'i', 'o', 'u']
>>> vowels = ['e', 'a', 'u', 'o', 'i']
>>> print('vowels ascending : ',vowels) # sort by ascending
vowels ascending :  ['a', 'e', 'i', 'o', 'u']
>>> vowels.sort(reverse = True)
>>> print('vowels descending : ',vowels) # sort by descending
vowels descending :  ['u', 'o', 'i', 'e', 'a']
```

#### in operator on list

`in` operator in list is useful for checking if there is a member in the list or a collection. For example:

```python
>>> my_list = ['chico', 419, 'Ri', 52, 0]
>>> 'Ri' in my_list
True
>>> 55 in my_list
False
```

#### List slicing

In short, We use the colon `:` to slice the list. The following are the common usages:

```python
# a is a list
a[3:10] # items start from index3 to index10
a[3:]   # items start from index3 to the end
a[:10]  # items starts from the beginning to index10
a[:]    # a copy of the whole list
a[-1]    # last item in the list
a[-2:]   # last two items in the list
a[:-2]   # everything except the last two items
```

Apart from increasing or decreasing by integer 1, we can also and step in list slicing.

Syntax:

```python
sliceable_list[start:stop:step]
```

The start and stop is already explained in the above example. For step - the amount by which the index increases, defaults to 1. If it's negative, you're slicing over the iterable in reverse. For example:

```bash
>>> r=[1,2,3,4,5,6]
>>>r[::2] #iterate whole list, increased by step 2
[1, 3, 5]
>>> r[2::2] #iterate from index2 to the end, increased by step 2
[3, 5]
>>> r[::-2] #iterate in reverse, decreased by step 2
[6, 4, 2]
```

### Dict {}

A dictionary is a collection which is disordered, changeable and indexed. In Python dictionaries are written with curly brackets`{}`, and they have keys and values, like `d = {key1 : value1, key2 : value2}`.

Example 9:

```python
>>> my_dict = {
...  "apple": "green",
...  "banana": "yellow",
...  "cherry": "red"
...}
>>> print(my_dict)
{'apple': 'green', 'banana': 'yellow', 'cherry': 'red'}
```

#### Common features of dict

1. One can Access the values in the dict by `key`
2. Change dictionary by adding/deleting/updating key and values

Example 10:

```python
>>> person_dict = {'Chico': 24, 'Ivy': 20, 'Ri': 29}
>>> print('Chico : ',person_dict['Chico']) #access values
Chico :  24
>>> person_dict['Ri'] = 19
>>> print('Ri : ',person_dict['Ri'])
Ri :  19
>>> person_dict['Frank'] = 31 #update value
>>> print('Frank : ',person_dict['Frank'])
Frank :  31
>>> del person_dict['Ivy'] #delete key
>>> print('New_dict :',person_dict)
New_dict : {'Chico': 24, 'Ri': 19, 'Frank': 31}
```

#### Dict functions

| Functions | Description                           |
|-----------|---------------------------------------|
| len(dict) | Number of dict elements,which is the total number of keys               |
| str(dict) | Output dictionary as a string         |

Example 11:

```python
>>> person_dict = {'Chico': 24, 'Ri': 19, 'Frank': 31}
>>> len(person_dict)
3
>>> print("To String : %s" % str(person_dict))
To String : {'Chico': 24, 'Ri': 19, 'Frank': 31} #it's a string, not the same as original dict
```

#### Dict methods

| Methods    | Description                                               |
|------------|-----------------------------------------------------------|
| fromkeys() | creates dictionary from given sequence                    |
| get()      | Returns value of the key, default=None                               |
| items()    | Returns view of dictionary's (key, value) pair            |
| keys()     | Returns view object of all keys                           |
| contains(key) | Return bool value by checking whether the key is in dict  |
| pop()      | Returns & removes element having given key                |
| values()   | Returns view of all values in dictionary                  |
| update()   | Updates the Dictionary                                    |

Example 12: All examples are corresponding to the list methods stated above.

```python
>>> seq = ['Chico', 'Ivy', 'Ri']
>>> p_dict = dict.fromkeys(seq)  #get/create keys from the list
>>> print("New_dict : %s" % str(p_dict))
New_dict : {'Chico': None, 'Ivy': None, 'Ri': None}
>>> p_dict = dict.fromkeys(seq, 'A+') #give all keys value A+
>>> print("New_dict : %s" % str(p_dict))
New_dict : {'Chico': 'A+', 'Ivy': 'A+', 'Ri': 'A+'}
```

```python
>>> p_dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("Age : %s" % p_dict.get('Age')) #get key value
Age : 23
>>> print("Gender : %s" % p_dict.get('Gender'))
Gender : Male #if you get a wrong key, it will return None
```

```python
>>> p_dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("dict_values : %s" % p_dict.items()) #view dict's items
dict_values : dict_items([('Name', 'Chico'), ('Gender', 'Male'), ('Age', '23')]) #return a tuple
```

```python
>>> p_dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("dict_keys : %s" % p_dict.keys()) #view all keys
dict_keys : dict_keys(['Name', 'Gender', 'Age'])
>>> p_dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("has_key : %s" % p_dict.__contains__('Age')) #two '_', check out keys
has_key : True
>>> print("has_key : %s" % p_dict.__contains__('School'))
has_key : False
>>> p_dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> pop_value = p_dict.pop('Gender') #drop out key
>>> print(pop_value)
Male
>>> print(p_dict)
{'Name': 'Chico', 'Age': '23'}
```

```python
>>> p_dict = {'Name': 'Chico', 'Age': '23'}
>>> print("Value : %s" % p_dict.values()) #get all values
Value : dict_values(['Chico', '23'])
>>> my_dict = {'Name': 'Chico', 'Age': '23'}
>>> new_dict = {'Gender':'Male'}
```

```python
>>> my_dict.update(new_dict) #update new_dict in my_dict
>>> print('new_dict : %s' % my_dict)
new_dict : {'Name': 'Chico', 'Age': '23', 'Gender': 'Male'}
```

#### in operator in dict

Likewise, one can us `in` operator to check whether there is certain key in the dict. For example:

```python
>>> my_dict = {'Name': 'Chico', 'Gender': 'Male', 'Age': 23}
>>> 23 in my_dict
True
```

In dict, we can use `in` operator to do more, for example, we can build a dict to calculate the words frequency of an article(s), and store the value in the dict. You can refer to [this challenge](#simple-word-frequency) for further information.

### Tuple ()

A tuple is similar to a list, except that the elements of the tuple cannot be modified. The function and method of a tuple is similar to list, therefore we are not discussing more.

Example 13:

```python
>>> tup = (1, 2, 3, 4, 5 )
>>> print("tup[0]: ", tup[0])
tup[0]:  1
```

### Bonus: Copy collection objects

The assignment from one object to another object is essentially an assignment of "pointer". You can understand it as a reference to the object. This design is for efficiency purpose. Some non-intuitive behaviour to new learners may arise due to this design.

We first try the simple object (data type):

```python
>>> a = 1
>>> b = a # The key line of assignment
>>> a
1
>>> b
1
>>> b = 'fffff'
>>> b
'fffff'
>>> a # a is not changed
1
```

Now let's test the `list` collection type:

```python
>>> a = [1, 2, 3]
>>> b = a  # The key line of assignment
>>> b
[1, 2, 3]
>>> b[2] = 'ffff'
>>> b # b is changed as expected
[1, 2, 'ffff']  
>>> a # a is also changed
[1, 2, 'ffff']
```

The solution is to use `copy.deepcopy` to create a copy, not just a reference.

```python
>>> import copy
>>> a = [1, 2, 3]
>>> a
[1, 2, 3]
>>> b = copy.deepcopy(a)
>>> b
[1, 2, 3]
>>> b[2] = 'ffff'
>>> b
[1, 2, 'ffff']
>>> a
[1, 2, 3]
```

## Bonus: Class and objects

Class is an abstraction that describes certain objects with the same properties and methods. It defines the properties and methods that are common to every object in the collection. An object is an instance of a class. The process creating an object from a class is called "instantiation" and is usually invoked by the "construct function" of a class. In Python, this function is called `__init__()`. The higher level concept is called "[Object Oriented Programming](https://en.wikipedia.org/wiki/Object-oriented_programming)", which appears in nearly all modern programming languages. Think of it as a way to model our real world. We will discuss OOP a bit later. This section is a quick peek into the basics -- `class` and `object`.

### Create a class, the init() function

All classes have a function called `__init__()`, which is always executed when the class is being initiated. Therefore the `__init__()` function is used to assign values to object properties, or other operations that are necessary to do when the object is being created.

Example 28: Create a animal class.

```python
class Animal(): #class + class name to give a statement
    def __init__(self, name): #self refer to class itself, its default.
        self.name = name  #all objects in this class has name

a = Animal("dog")  #give a new object, an animal named dog
print(a.name)
```

Output:

```text
dog
```

Example 29: Create a person class and give new object

```python
class Person():  #build a person class
    def __init__(self,name,age): #those objects has name and age
        self.name,self.age = name,age  
    def __str__(self):  # def a certain return
        return 'My name is {self.name}, and I\'m {self.age} years old'.format(self=self) #review the format.() function

str(Person('xyc',18)) #call the function by passing parameters in the function
```

Output:

```text
My name is xyc, and I'm 18 years old
```

**Note:** In the example above,
`return 'My name is {self.name}, and I\'m {self.age} years old'.format(self=self)`

is equal to

`return 'My name is {0}, and I‘m {1} years old'.format(self.name,self.age)`

So, what does this(self=self) means?

```python
def __str__(self):
        return 'My name is {self.name}, and I\'m {self.age} years old'.format(self=self)
```

The first self in self=self refers to what the format function will change in your string. For example, it could also be

```python
def __str__(self):
    return 'My name is {obj.name}, and I\'m {obj.age} years old'.format(obj=self)
```

The right-hand side self in self=self refers to the actual value that will be input. In this case, the object passed as argument. In other words, it could be written as

```python
def __str__(obj):
        return 'My name is {self.name}, and I\'m {self.age} years old'.format(self=obj)
```

**Now why to use self?**

It is just a convention used in python programming. Python passes to its instance methods automatically an object that is a pointer to itself. Can also check [this question](https://stackoverflow.com/questions/2709821/what-is-the-purpose-of-self) for further info.

Example 30:

```python
class Account:
    def __init__(self, number, name):
        self.number = number
        self.name = name
        self.balance = 0

    def deposit(self, amount):  
        if amount <= 0:
            raise ValueError('must be positive')
        self.balance += amount

    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
        else:
            raise RuntimeError('balance not enough')

acct1 = Account('123–456–789', 'Chico') #open an account
acct1.deposit(500)
acct1.withdraw(100)
print(acct1.balance)
```

Output:

```text
400
```

### Bonus: Class inheritance

"Class" is more than a group of common features, i.e. member variable and member functions. The real power of class comes when you get into the OOP world. The first step is to understand [class inheritance](https://docs.python.org/3/tutorial/classes.html#inheritance).

Now that you have the keyword, please try to search online to understand the syntax and grammar. Then follow some concrete examples to see how class inheritance can be used in real project. Our class does not emphasize OOP, so details are omitted here. Our core objective is to master the basics of Python and use it to collect, analyse and visualise data, in order to tell good stories. Most of the programs you will need to write during the class look "flat", i.e. we do not expect many layers of modules/ functions/ classes. However, when you build a large project, the OOP design patterns can make one more efficient, less error prone and easier to collaborate.

## Exercises and Challenges

### Divide HW1 groups randomly: (case contribution)

1. You can get the students' IDs from the file [chapter3-exercise-student-list.csv](assets/chapter3-exercise-student-list.csv) and cases from the file [chapter3-exercise-case-list.csv](assets/chapter3-exercise-case-list.csv).
2. Generate the grouping randomly, each team has 5 students and need be randomly distributed one case from 10 over all.

Sample input (part of your initial `.py` script):

```python
    student_list =[
    18421111,
    18421112,
    18421113,
    18421114,
    18421115,
    18421116,
    18421117,
    18421118,
    18421119,
    18421120,
    18421121,
    18421122,
    ...
    18421160
    ]
    case_list =[
    'case1 - build a calculator to evaluate your business model',
    'case2 - build a automatic earthquake robot to broadcast the new earthquake',
    'case3 - evaluate social media performance of a luxury brand',
    'case4 - study movie blockbuster \'Dying to Survive\'',
    'case5 - invest your money like the Internet giant, Tencent',
    'case6 - where are the 200,000 inferior vaccines flowing?',
    'case7 - study classics, Who control the discourse power in \'Dream of the Red Chamber\'',
    'case8 - research about Didi-driver crimes in China',
    'case9 - \'Me too\' analysis',
    'case10 - what is hip-hop in china?'
    ]

# Write your code here
```

Sample output (`print` to the screen):

```text
Group 1
Student ID ID1
Student ID ID2
Student ID ID3
Student ID ID4
Student ID ID5
Assigned case n
===============
Group 2
...
```

#### Hint for group assignment challenge

Following hints can help you think the algorithm but you do not have to use all the hints at the same time:

- Consider a multiple loop
- `random.shuffle()` or `random.choice()` can be useful
- This is essentially a "mapping problem" and one powerful data structure designed for this type of problem is `dict`. You can use case as key and `list` of students as value.
- Always watch out for boundary conditions in programming: does your code still work when the number of students can not be divided by number of cases? Say 10 students, 3 cases.


### Simple word frequency

Word frequency is a common routine used in text analysis. Given a piece of English text, you can perform word frequency analysis in following steps:

1. Use `str.split()` to get a `list` of blank space separated words.
2. Use a `dict()` in this structure: `{word: frequency}`, where key is the word and value is an integer.
3. Loop over the `list` obtained in step 1 and use the accumulator in step 2 to count the frequencies.

In the end, the `dict` is our answer.

**HINT**: Before you accumulate in a dict like `ans[key] += 1`, you may want to check if the `key` actually exists in the `dict` by `key in ans` or `ans.contains(key)`.

**QUIZ**: Does this procedure work with Chinese? If so, please give the code or pseudo code. If not, in which step it fails?

#### Bonus: pretty print in ordered format

The default print of `dict` has unreadable special chars like `{,},:`. Can you print the result in a ascii table like what we did in the mortgage schedule? Please rank the table from highest frequency to lowest frequency.

#### Bonus: Use the Counter class

```python
>>> from collections import Counter
>>> c = Counter()
>>> c
Counter()
>>> type(c)
<class 'collections.Counter'>
>>> isinstance(c, dict)
True
```

### Convert Hong Kong district names into a convenient data structure

Suppose we are building the profile information for Hong Kong's 18 districts. The data can be found on [wikipedia](https://en.wikipedia.org/wiki/Districts_of_Hong_Kong). It is in HTML's table format (or available as mediawiki notation). Both format is not easy for program to further process. Before we learn scraping in week-05 and week-06, we can still do some simple processing here. We copy and paste the table into our source code to generate a tab-separated-values (TSV). With a bit string processing, we can process this raw string of data into list-of-dict structure or dict-of-dict structure.

You can start with the following code snippet:

```python
a = '''
Central and Western	中西區	244,600	12.44	19,983.92	Hong Kong Island
Eastern	東區	574,500	18.56	31,217.67	Hong Kong Island
Southern	南區	269,200	38.85	6,962.68	Hong Kong Island
Wan Chai	灣仔區	150,900	9.83	15,300.10	Hong Kong Island
Sham Shui Po	深水埗區	390,600	9.35	41,529.41	Kowloon
Kowloon City	九龍城區	405,400	10.02	40,194.70	Kowloon
Kwun Tong	觀塘區	641,100	11.27	56,779.05	Kowloon
Wong Tai Sin	黃大仙區	426,200	9.30	45,645.16	Kowloon
Yau Tsim Mong	油尖旺區	318,100	6.99	44,864.09	Kowloon
Islands	離島區	146,900	175.12	825.14	New Territories
Kwai Tsing	葵青區	507,100	23.34	21,503.86	New Territories
North	北區	310,800	136.61	2,220.19	New Territories
Sai Kung	西貢區	448,600	129.65	3,460.08	New Territories
Sha Tin	沙田區	648,200	68.71	9,433.85	New Territories
Tai Po	大埔區	307,100	136.15	2,220.35	New Territories
Tsuen Wan	荃灣區	303,600	61.71	4,887.38	New Territories
Tuen Mun	屯門區	495,900	82.89	5,889.38	New Territories
Yuen Long	元朗區	607,200	138.46	4,297.99	New Territories
'''
```

Please try to workout a variable `d` for our future lookup. Given the english name as `name`, we can get the district's Chinese name via `d[name]['Chinese']` and population by `d[name]['Population']`.


### Conversion between simplified Chinese and traditional Chinese

Write a function:

* Input: `str` -- simplified Chinese
* Output `str` -- traditional Chinese

You can use a `dict` to maintain the mapping and use `for` loop to process every part of the paragraph.

**TIP**: You can not build a complete converter, but you can still try and build part of it.
