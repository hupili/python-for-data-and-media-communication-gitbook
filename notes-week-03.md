# Week 3 Python for anything

<div id="toc">

<!-- TOC -->

- [Week 3 Python for anything](#week-3-python-for-anything)
    - [Objective](#objective)
    - [Use "Help" more to learn by yourself](#use-help-more-to-learn-by-yourself)
    - [Bool and comparisons](#bool-and-comparisons)
        - [Logic operators](#logic-operators)
        - [Comparison operators](#comparison-operators)
        - [Str comparison](#str-comparison)
        - [Int comparison](#int-comparison)
    - [Composite data types](#composite-data-types)
        - [List []](#list-)
            - [Common features](#common-features)
            - [List functions](#list-functions)
            - [List methods](#list-methods)
        - [Dict {}](#dict-)
            - [Common features](#common-features-1)
            - [Dict functions](#dict-functions)
            - [Dict methods](#dict-methods)
        - [Tuple ()](#tuple-)
    - [Control flows](#control-flows)
        - [If-else Statement](#if-else-statement)
        - [Python loop](#python-loop)
            - [Difference between for loops and while loops](#difference-between-for-loops-and-while-loops)
            - [While loop](#while-loop)
            - [For loop](#for-loop)
                - [Use for statement to pick up values](#use-for-statement-to-pick-up-values)
                - [Use for loop to calculate](#use-for-loop-to-calculate)
                - [Use for and if statement together](#use-for-and-if-statement-together)
        - [Break and Continue statement](#break-and-continue-statement)
            - [Break statement](#break-statement)
            - [Continue statement](#continue-statement)
        - [Def function](#def-function)
    - [Errors and Exceptions](#errors-and-exceptions)
        - [Try and except](#try-and-except)
        - [Raising errors](#raising-errors)
        - [Exception error types](#exception-error-types)
    - [Class and objects](#class-and-objects)
        - [Create a class, the init() function](#create-a-class-the-init-function)
    - [Challenges](#challenges)
    - [References](#references)

<!-- /TOC -->

</div>

Previously, We learn Python basics including data types, arithmetic, functions and several commonly used modules, with which help, you can build a calculator to do some simple case analysis. This week, we will step further to learn composite data types, the function and method of how to use them. Meanwhile, we will touch hands on the basic control flows to better understand the logic behind the coding works. After that, you can create some functions by your own so that you can use Python to do more.

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

Example 1: If you want to know how to use 'numpy'. Type `help(numpy)` to learn more, you can get the information as follow:

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
    ...
```

## Bool and comparisons

### Logic operators

The logical operators in Python (`and`, `or`, `not`) are often used in the if, if…else, and if…elif statements. They enable you to make multiple comparisons inside a single statement, such as to determine whether a value is within a certain range.

| Operators | What it means                 | What it looks like  |
|-----------|-------------------------------|---------|
| and       |True if both are true          | x and y |
| or        |True if at least one is true   | x or y  |
| not       |True only if false             | not x   |

Example 2:

```python
>>> print((6 > 5) and (2 < 4))  # Its true when both expressions are True
True
>>> print((8 == 8) or (6 != 6)) # Its true when one expression is True
True
>>> print(not(3 <= 1))          # Its true when the original expression is False
True
```

### Comparison operators

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

Example 3:

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

Example 4:

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

Example 5:

```python
>>> a = [0, 6.6, 'python']
```

#### Common features

1. Each element in the sequence is ordered and can be indexed. The first index is 0 and the second index is 1
2. Lists can be added and multiplied
3. One can add or remove elements into list
4. One can check whether one elements is in the list
5. One can slice the list

**Note:** We talk about `index` in chapter 2, for those who forget how it works, please refer to [here](/notes-week-02.md#about-index-in-data-types)

Example 6:

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

Example 7:

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

Example 8: All examples are corresponding to the list methods stated above.

```python
>>> list1 = ['Hello', 'Python', 2018, 814]
>>> list1.append(2049) #append() takes exactly one argument
>>> print(list1)
['Hello', 'Python', 2018, 814, 2049]
```

```python
>>> list2 = [23, 2018, 814, 2049,2018]
>>> list2.count(2018) #count numbers of 2018
>>> print(list2)
2
```

```python
>>> list1.extend(list2) #add list2 into list1
>>> print("Extended List : ", list1)
Extended List : ['Hello', 'Python', 2018, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> print("Index for python : ", list1.index('Python'))
1 #index value 'Python'
>>> print("Index for 2018 : ", list1.index(2018)) #find the first position of the indexed value
2
```

```python
>>> list = ['Hello', 'Python', 2018, 814, 23, 2018, 814, 2049, 2018]
>>> list.insert(3, 2009) #list.insert(index, object),insert value 2009 in the index3
>>> print("New List : ", list)
New List :  ['Hello', 'Python', 2018, 2009, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> list = ['Hello', 'Python', 2018, 2009, 814, 23, 2018, 814, 2049, 2018]
>>> list.pop(2) #delete index2 value and return this value
>>> print('List now : ',list)
List now :  ['Hello', 'Python', 2009, 814, 23, 2018, 814, 2049, 2018]
>>> list.remove('Hello') #remove certain value
>>> print('List now : ',list)
List now :  ['Python', 2009, 814, 23, 2018, 814, 2049, 2018]
```

```python
>>> list = ['Python', 2009, 814, 23, 2018, 814, 2049, 2018]
>>> list.reverse() #reverse list
>>> print('reverse list : ',list)
reverse list :  [2018, 2049, 814, 2018, 23, 814, 2009, 'Python']
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

### Dict {}

A dictionary is a collection which is disordered, changeable and indexed. In Python dictionaries are written with curly brackets`{}`, and they have keys and values, like `d = {key1 : value1, key2 : value2 }`.

Example 9:

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
>>> dict = dict.fromkeys(seq)  #get/create keys from the list
>>> print("New_dict : %s" % str(dict))
New_dict : {'Chico': None, 'Ivy': None, 'Ri': None}
>>> dict = dict.fromkeys(seq, 'A+') #give all keys value A+
>>> print("New_dict : %s" % str(dict))
New_dict : {'Chico': 'A+', 'Ivy': 'A+', 'Ri': 'A+'}
```

```python
>>> dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("Age : %s" % dict.get('Age')) #get key value
Age : 23
>>> print("Gender : %s" % dict.get('Gender'))
Gender : Male #if you get a wrong key, it will return None
```

```python
>>> dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("dict_values : %s" % dict.items()) #view dict's items
dict_values : dict_items([('Name', 'Chico'), ('Gender', 'Male'), ('Age', '23')]) #return a tuple
```

```python
>>> dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("dict_keys : %s" % dict.keys()) #view all keys
dict_keys : dict_keys(['Name', 'Gender', 'Age'])
>>> dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> print("has_key : %s" % dict.__contains__('Age')) #two '_', check out keys
has_key : True
>>> print("has_key : %s" % dict.__contains__('School'))
has_key : False
>>> dict = {'Name':'Chico','Gender':'Male','Age':'23'}
>>> pop_value = dict.pop('Gender') #drop out key
>>> print(pop_value)
Male
>>> print(dict)
{'Name': 'Chico', 'Age': '23'}
```

```python
>>> dict = {'Name': 'Chico', 'Age': '23'}
>>> print("Value : %s" % dict.values()) #get all values
Value : dict_values(['Chico', '23'])
>>> dict1 = {'Name': 'Chico', 'Age': '23'}
>>> dict2 = {'Gender':'Male'}
```

```python
>>> dict1.update(dict2) #update dict2 in dict1
>>> print('new_dict : %s' % dict1)
new_dict : {'Name': 'Chico', 'Age': '23', 'Gender': 'Male'}
```

### Tuple ()

A tuple is similar to a list, except that the elements of the tuple cannot be modified. The function and method of a tuple is similar to list, therefore we are not discussing more.

Example 13:

```python
>>> tup = (1, 2, 3, 4, 5 )
>>> print("tup[0]: ", tup[0])
tup[0]:  1
```

## Control flows

A control flow is a block of programming that analyses variables and chooses a direction in which to go based on given parameters. In python, all codes and statements are faithfully executed in exact top-down order. But what if you want to change the flow?

For example, you want the program to take some decisions and do different things depending on different situations, such as printing 'True' or 'False' depending on the different comparison and test?

Under such circumstances, using control flow statements will help you manipulate data better. There are several control flow statements we will learn in this chapter.

**NOTE:** In `control flows` chapter, we will encounter a lot of `indentations` when handling if/for/while/def/class. It is hard and inconvenient to type in Python shell, so please write down the codes in text editor and save it as a `.py` file, so that you can just execute the file once to get the answer. If you forget how to do this, please refer to [chapter 2](/notes-week-02.md#python-has-two-basic-modes-script-and-interactive).

### If-else Statement

`If-else statement` is used to conditionally execute a statement or a block of statements. Conditions can be true or false, execute one thing when the condition is true, something else when the condition is false.

```python
if ...:   #close with an ':'
    print(sth)  #indented
elif ...: # elif = else if
    print(sth)
else:
    print(sth)
```

**Note:** All function definitions or condition comparisons should end with a `:`, and all the content in those functions and conditions need to be indented. you can just indent with clicking `tab`.

Take the case that we talk about chapter 2 as an example. (The full version of the case is [here](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/)

> Example 14: We want to know how much is the cost with the number of users we have.  When the number is less than 50,000, the cost will be 10,000. If the number is not less than 50,000, then cost=10000+0.1×(number_of_users -50000）. The actual number of users we have now is 100,000. The if-else statement will be as fellow:

```python
number_of_users = 100000
if number_of_users <= 50000:
    cost = 10000
else: # number_of_users > 50000
    cost = 10000 + 0.1 * (number_of_users - 50000)
print (cost)
```

```
Answer: 15000.0
```

> Example 15: If there is two charge plans when the number of users is more than 50,000.
>1. when  50,000≤the number of user≤100,000, the cost= 10000+0.1×(number_of_users -50,000);
>2. when the number of user ≥100,000, the cost=10,000 + 0.1×(100,000 -50,000) + 0.2 * (number_of_users - 100,000).
>3. The actual number of users we have now is 120,000. 

The if-else statement will be as fellow:

```python
number_of_users = 120000
if number_of_users <= 50000:
    cost = 10000
elif number_of_users <= 100000: # 500000 <= number_of_users <= 100000
    cost=10000+0.1*(number_of_users-50000)
else: # number_of_users > 100000
    cost = 10000 + 0.1*(number_of_users-50000) + 0.2 * (number_of_users - 100000)
print(cost)
```

```
Answer:21000.0
```

### Python loop

Python has two primitive loop commands:  

1. `while loops`
2. `for loops`

#### Difference between for loops and while loops

1. While Loops allow you put a condition in it, like `while i<10`, and it will stop when the condition no longer being meet( i >= 10). you can also substitute in a boolean(true/false) for 10 as well as many other types of variables.

2. For Loops allow you to run through the loop many times you'd like it to run through the problem such as `for i in range(0,100)`, this will continually increase i until that condition returns false(>100), you can replace 10 with other numbers and variables, like `for name in name_list`, means that you want to loop the whole name_list to run through the problem. And it will quit once the condition is no longer being met.

3. Generally speaking, if you want to use loop to do conditional comparison, `while` loops is work for you, if you want to loop every elements of a whole list, `for` is better.

#### While loop

We can execute a set of statements in while loop as long as a condition is true.

**Syntax**

```python
while ...:   #close with an ':'
    print(sth)  #indented
    if ...: # you can insert `if` in `while`
        print(sth)
```

Example 16:

```python
i = 1
while i < 6:
    i = i + 1
    print(i)
```

```
Answer:
2
3
4
5
6
```

Example 17:

```python
i = 1
while i < 6:
    print(i)
    i = i + 1
    if i == 3:
        break #we will talk this later
```

```
Answer:
1
2
```

#### For loop

For loop(For Statement) has the ability to iterate over the items of any sequence, such as a list or a string.

**Syntax** 

```python
for x in y:   #close with an ':'
    print(sth)  #indented
    if ...: # you can insert `if` in `for` loop
        print(sth)
```

##### Use for statement to pick up values

Example 18: List every integer from 1 to 10.

```python
for i in range(1,11):
    print(i)
```

```
Answer: '1,2,3,4,5,6,7,8,9,10'
```

**Note**: The `range()` function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default).`(1,11)` means values from 1 to 10 (not including 11)

Example 19: Square of every integer from 1 to 10.

```python
for i in range(1,11):
    print(i**2) #or i*i
```

```
Answer: '1,4,9,16,25,36,49,64,81,100'
```

##### Use for loop to calculate

Example 20: Calculate the number of pulsing from 1 to 100.

```python
total = 0
    for i in range(1, 101): # numbers which are >=1 and <101
        total = total + i
print (total)
```

```
Answer: 5050
```

##### Use for and if statement together

Example 21:

 Like the [example](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/) we used before. Find that break-even point of subscribed users to make profit.

```python
# coding: utf-8

Fixed_Cost = 30000
Content_Cost = 70000

member_ff = 15
convert_rate = 0.1
ad_revenue_each_person = 1

num = float(input('please input your estimate number of subscribers:')) #input a estimated number
for i in range(0,int(num)):
    if i < 50000:
        Total_Cost = Fixed_Cost + Content_Cost
    else:
        Total_Cost = Fixed_Cost + Content_Cost + 0.1 * (i - 50000)

    Revenue = (1*i) + (0.1*15*i)
    Net_Income = Revenue - Total_Cost

    if Net_Income >= 0:
        print('subscribers= ',i)
        break

if Net_Income < 0:
    print('Net_Income=', Net_Income) #the max value return by your in
```

```
Answer: subscribers= 40000
```

### Break and Continue statement

#### Break statement

Stop the loop even if the while condition is true.

Example 22:

```python
i = 1
while i < 9:
    print(i)
    if i == 5:
        break
        i = i + 1
```

```
Answer:
1
2
3
4
5 #stop the loop
```

#### Continue statement

Stop the current iteration, skip certain value, and continue with the next.

Example 23:

```python
i = 1
while i < 9:
    i = i + 1
    if i == 5:
        continue
    print(i)
```

```
Answer:
2
3
4 #number 5 is missing, while the loop continues
6
7
8
9
```

### Def function

A function is a block of code which only runs when it is called. You can call this function by passing parameters into a function. Then the function can return data as a result.

```python
def function_name(parameters): #define function
    control flow #use control flow
    return  #return to default or specified value

function_name("parameter1") #call the function
```

**How `def` function works**

* Keyword `def` (means definite) marks the start of function header.
* A function name to uniquely identify it.
* Parameters (arguments) are optional, through which we pass values to a function.
* A colon `:` to mark the end of function header.
* Describe what the function does.
* Statements must have same indentation level (usually click `tab` on your keyboard to indent).
* An optional `return` statement to return a value from the function.
* when you find you are using a function again and again. you can use "def statement"to duplicate the logic.  
* Type "Tab“to move the section rightwards. Type"tab"+"Shift" to move the section leftwards.

> Example 24: based on the example we talk about above.  Build a def function to calculate the profits when you give different number of users.
>1. when  50,000≤the number of user≤100,000, the cost= 10000+0.1×(number_of_users -50,000);
>2. when the number of user ≥100,000, the cost=10,000 + 0.1×(100,000 -50,000) + 0.2 * (number_of_users - 100,000).

```python
def calculate_profit(number_of_users):
    if number_of_users < 50000:
        cost = 10000
    elif number_of_users <= 100000: # 500000 <= number_of_users <= 100000
        cost=10000+0.1*(number_of_users-50000)
    else: # number_of_users > 100000
        cost = 10000 + 0.1*(number_of_users-50000) + 0.2 * (number_of_users - 100000)
    revenue = 0.1 * number_of_users
    profit = revenue - cost
    return profit

print(calculate_profit(100))
```

```
Answer: -9990.0
```

The advantage of using "def" is that you can recall the function again and again. Just change the parameter. For example:

```python
print(calculate_profit(100))
print(calculate_profit(1000))
print(calculate_profit(10000))
print(calculate_profit(100000))
```

```
Answers:
-9990.0
-9900.0
-9000.0
-5000.0
```

## Errors and Exceptions

### Try and except

For most errors, the Python interpreter will issue an exception. In fact, in many cases, we need to control the code that may generate exceptions. In python, error and exception handling allows us to continue our program if an exception occurs.

The try statement works as follows.

1. the try statement between the try and except (keywords) is executed.
2. If no exception occurs, the except clause is skipped and execution of the try statement is finished.
3. If an exception occurs during execution of the try clause, and its type matches the exception named after the except keyword, the except clause will be executed, **and the execution continues after the try statement.**
4. If an exception occurs which does not match the exception named in the except clause, it is passed on to outer try statements; if no handler is found, it is an unhandled exception and execution stops.

Example 25:

```python
try:
        print("Hello World")
except:
        print("This is an error message!")
```

Example 26:

```python
while True:
    try:
        x = int(input("Please enter a number: ")) #input a int and non-int to test
        break
    except ValueError:
        print("Oops!  That was no valid number.  Try again...")
```

### Raising errors

The `raise` statement allows you to force a specified exception to occur. It can be used in following `try` and `if`.

Example 27:

```python
inputValue = input("please input a int :")
if type(inputValue)!=type(1): # '!=' means not equal
    raise ValueError
else:
    print inputValue
#you can input a 2 and 2.2 to test.
```

### Exception error types

There are several common exception errors:

* IOError. If the file cannot be opened.

* ImportError. If python cannot find the module

* ValueError. Raised when a operation or function receives an argument that has the right type but an inappropriate value

* KeyboardInterrupt. Raised when the user hits the interrupt key (normally Control-C or Delete)

## Class and objects

Class is a collection used to describe objects with the same properties and methods. It defines the properties and methods that are common to every object in the collection. An object is an instance of a class.

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

```
Answer: dog
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

```
Answer: My name is xyc, and I'm 18 years old
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

```
Answer: 400
```

## Challenges

* Distances among cities:
    1. Calculate the "straight line" distance on earth surface from several source cities to Hong Kong. The source cities: New York, Vancouver, Stockholm, Buenos Aires, Perth. For each source city, print one line containing the name of the city and distance. "Great-circle distance" is the academic name you use to search for the formula.
    2. Use list and for loop to handle multiple cities  
    3. Use function to increase the reusability

* Divide HW1 groups randomly: (case contribution).
    1. Get the list of student IDs from the lecturer.
    2. Generate the grouping randomly

* Solve the "media business model" calculator.

## References

* Chapter 4, 5, 6, 8, 9 of official Python 3 [tutorial](https://docs.python.org/3/tutorial/)
* Another [tutorial](http://www.runoob.com/python/python-object.html) with many examples (Chinese)
