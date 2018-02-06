# Week 3 Python for anything

### 1. Use "Help"

In the Terminal of your computer. You can type `>>> help` for any instruction for using Python functions.  
** Notes:**

* Type 'Q' to quit help; 
* Type 'J' to view up; 
* Type 'K' to view down

> _Example1_: If you want to know how to use 'numpy'. Type`>>>help()`  and then type `numpy` , then you can get the information about numpy as follow:

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

### 

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
`[1, 2, 3, 4, 5, 6]`  
`[2, 4, 1, 3, 5, 6]`

## 

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



