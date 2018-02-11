# Week 2: Use Python as a daily tool

By writing python languages in the editor, we can get what we want on terminal.
There are many rules in python language.

### 1. Variables

Variables means changable. It can be a character or a word, which is not defined in python language. You should give it a definition.


```
a=1+2
print a
```

"a" is variable, so you give it a definition that a equals 1+2, and you will get 3 in terminal.

```
fruit1=apple
print fruit1
```
It means you define fruit1 as apple, so you will get apple in terminal.

```red=0
print red
```
red is a variables, and you define it as 0,so it will print 0 in terminal.

```
red=0
print "red"
```
You will get red in terminal, as **"red"** is different from **red**. (Quotation marks are important.)

### 2. Basic data types

In fact,there are so many different kinds of data you can use to define the variables. Different data types are totally different.
Following are some basic data types.

##### 1. int

`int` means integer, like 7, 8, 9 and so on. those numbers are integer.eg:

```
a=int(7.9)
print a
```
int\(\) is a function, which converts the number in \(\) to an integer. You have defined "a" equals "int\(7.9\)" , so it will print 7.

##### 2. float

`float` means a number with decimal, like2.1, 3.8, 5.6 and so on. eg:

```
b= float(7)
print b
```

It will print `7.0`.

##### 3. str

* `str` means string, a sequence of characters, like quiet, asdf, HK\_NY and so on.
* If you **" "** something, python will regard it as strings, or characters.So you `print "red"`, you will get red in terminal.

### 3. Arithmetic

##### 1. Basic rules

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

##### 2. Exercise: Caculate a mortgage

Question: Caculate mortgage based on the following formula: (Assign "i" "P" "n" specific numbers by yourself.)

![](https://www.myamortizationchart.com/img/amortization-formula.jpg)

Answer:

```i=0.05
n=20
P=5000000
A=i*P*(1+i)**n/((1+i)**n-1)
print "A=",A
```
### 4. Modules and functions

There are diverse modules on the Internet,like math, geopy, numpy, scipy and so on.
Differnt modules contains different functions relating to modules' features.

##### 1. Import a module and choose a function to use

`import` means import a module from the Internet. eg: `import numpy` to import a module called numpy. ("import" is always written on the top to indicate readers what kind of module and functions you will use.)

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

You will get pi as 3.1415927.(It means both "numpy" and "scipi" contain the pi variable.)

`()`means you should input something in the function. Otherwise, it will automatically input default numbers.

##### 2. Exercise: Caculate the area of a round

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




