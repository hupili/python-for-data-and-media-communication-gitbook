# Chapter 2: Use Python as a daily tool
In the previous chapter, I introduced the basic knowledge about teminal on Mac and how to navigate file system in Terminal, using shell,
creating the first python script and execute it.. But in this chapter, we want to focus specifically on Python, introducing python language. Including Variables, Basic data types, Arithmetic, assignment functions like  `import`,`notation` and several commonly used modules you need to know about to get up and going as a python developer, like `sys` `numpy`, `scipy`...

## Objective of this week
* Can use Python as a daily tool -- at least a powerful calculator

## 1. Variables

Variables means changable. It can be a character or a word, which is not defined in python language. Therefore you should give it a definition or assign value to it.

eg1:
```
a=1+2
print a
```
"a" is variable, so you give it a definition that a equals 1+2, and you will get 3 in terminal.

eg2:
```
fruit1=apple
print fruit1
```
It means you define fruit1 as apple, so you will get apple in terminal.

eg3:
```red=0
print red
```
red is a variables, and you define it as 0,so it will print 0 in terminal.

eg4:
```
red=0
print "red"
```
You will get red in terminal, as **"red"** is different from **red**. (Quotation marks are important.)

## 2. Basic data types

In fact,there are so many different kinds of data you can use to define the variables. Different data types are totally different.
Following are some basic data types.

### int

`int` means integer, like 7, 8, 9 and so on. those numbers are integer.eg:

```
a=int(7.9)
print a
```
int\(\) is a function, which converts the number in \(\) to an integer. You have defined "a" equals "int\(7.9\)" , so it will print 7.

### float

`float` means a number with decimal, like2.1, 3.8, 5.6 and so on. eg:

```
b= float(7)
print b
```
It will print `7.0`.

### str

* `str` means string, a sequence of characters, like quiet, asdf, HK\_NY and so on.
* If you **" "** something, python will regard it as strings, or characters.So you `print "red"`, you will get red in terminal.

## 3. Arithmetic

### Basic rules

* `+` means plus
* `-` means minus
* `*` means multiple
* `/` means divide.
* `//`means int the result of divide.
* `%` means divide and returns remainder.
* `**` means exponent.

eg:
```
a=10//3
b=10%3
c=10**3
print "a =",a,"b=",b,"c=",c
```
You will get a = 3, b = 1, c =1000.

### Exercise: Caculate a mortgage

Question: Caculate mortgage based on the following formula: (Assign "i" "P" "n" specific numbers by yourself.)

![](https://www.myamortizationchart.com/img/amortization-formula.jpg)
*[formula from wikipedia](https://en.wikipedia.org/wiki/Mortgage_loan) you can check out what each variable represents*

Answer:

```i=0.05
n=20
P=5000000
A=i*P*(1+i)**n/((1+i)**n-1)
print "A=",A
```
## 4. Modules and functions

There are diverse modules on the Internet,like math, geopy, numpy, scipy and so on.
Differnt modules contains different functions relating to modules' features.

### Import a module and choose a function to use

`import` means import a module from the Internet. eg: `import numpy` to import a module called numpy. (Generally, "import" is always written on the top to indicate readers what kind of module and functions you will use.)

`.` means we choose one of the functions in a specific module. eg:

```
import numpy
print numpy.pi
```
It means choose a function called "pi" from the module "numpy".You will get pi as 3.1415927.eg:

```
import scipy
print scipy.pi
```

You will get pi as 3.1415927.(Both "numpy" and "scipi" contain the pi function.)

`()`means you should input something in the function. Otherwise, it will automatically input default numbers.

#### 2. Exercise: Caculate the area of a round

* Q: Caculate the area of a round
Assign specific radius by yourself.

* Answer:
```
import numpy
r=5
area=r**2*numpy.pi
print "area=", area
```

##### 3. Exercise: Test sin\(\) function

* Q: Caculate sin pi/6

* Answer:
```
import numppy
a=numpy.sin(numpy.pi/6)
print "a=",a
```

##### 4. Exercise: Test random

* Q: Randomly select a number from 1 to 10

* Answer:
```
import random
print random.randrange(1,11)
```




