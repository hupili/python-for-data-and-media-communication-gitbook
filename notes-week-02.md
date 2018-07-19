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
> You will get a = 3, b = 1, c =1000.

### Exercise 1: Caculate a mortgage

Question: Caculate mortgage based on the following formula: (Assign "i" "P" "n" specific numbers by yourself.)

![](https://www.myamortizationchart.com/img/amortization-formula.jpg)<br>
*[formula from wikipedia](https://en.wikipedia.org/wiki/Mortgage_loan) , you can check out what each variable represents*

Example:

```
i=0.05
n=20
P=5000000
A=i*P*(1+i)**n/((1+i)**n-1)
print "A=",A
```
> Answer:262500

## 4. Modules and functions

There are diverse modules on the Internet,like math, geopy, numpy, scipy and so on.
Differnt modules contains different functions relating to modules' features.

### Import a module and choose a function to use

`import` means import a module from the Internet. you can import modules by writing `import`+ module name on terminal. And there are many modules out there, commonly used modules like [numpy](https://docs.scipy.org/doc/numpy/user/quickstart.html),[scipy](http://scipy.github.io/devdocs/tutorial/index.html), *click to check out more details*

eg: `import numpy` to import a module called numpy. (Generally, "import" is always written on the top to indicate readers what kind of module and functions you will use.)

There are many functions in a module, *module name +`.`+function name* means we choose a specific functions in a module. eg:

```
import numpy
print numpy.pi
```
It means choose a function called "pi" from the module "numpy".You will get pi as 3.1415927. Therefore, whenever you want to use a function, you should check out which modules contain this function, then you use `.` notation to reference to the function, and input the parameter into `()`  after the function, after excuting this command, you can get the results you want.eg:
```
import numpy
print(numpy.sin(numpy.pi/6))
```
![](https://github.com/hupili/python-for-data-and-media-communication-gitbook/blob/master/assets/week2-1.jpg)
> 0.5


### Exercise 2: Caculate the area of a round

* Q: Caculate the area of a round
Assign specific radius by yourself.

* Example:
```
import numpy
r=5
area=r**2*numpy.pi
print "area=", area
```
> Answer: area=78.53981633974483

### Exercise 3: Test sin\(\) function

* Q: Caculate sin pi/3

* Example:
```
import numpy
a=numpy.sin(numpy.pi/3)
print "a=",a
```
> Answer: a=0.8660254037844386

### Exercise 4: Test random
*If you don't know `random`, you can google this module and look at their documentation to learn several different functions* 

* Q: Randomly select a number from 1 to 10

* Example:
```
import random
print random.randrange(1,11)
```
> Answer should be one of int numbers in 1 to 10


## Challenge
* Build a mortgage calculator - given principal P, interest rate r and load period n, calculated the amortised monthly payment A
* Calculate the area of a circle given its radius r
* Given the length of hypotenuse of a right triangle, calculate the length of its legs. You may want to get values like $$\sin(\frac{\pi}{6})$$ via numpy.pi and numpy.sin
* Generate 10 random numbers. (it is OK to run your script 10 times)

## References
* [Chapter 1, 2, 3 of official Python 2 tutorial](https://docs.python.org/2/tutorial/)
* [Python format string](https://pyformat.info/)
