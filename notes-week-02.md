# Chapter 2: Use Python as a daily tool
<!-- TOC -->

- [Chapter 2: Use Python as a daily tool](#chapter-2-use-python-as-a-daily-tool)
    - [Objective of this week](#objective-of-this-week)
    - [Familiar with python interactive mode](#familiar-with-python-interactive-mode)
        - [Deference between two modes](#deference-between-two-modes)
        - [Enter and exit interactive mode](#enter-and-exit-interactive-mode)
    - [Variables and assignment](#variables-and-assignment)
    - [Basic data types](#basic-data-types)
        - [Int](#int)
        - [Float](#float)
        - [Str](#str)
        - [Escape character](#escape-character)
    - [Arithmetic](#arithmetic)
        - [Basic rules](#basic-rules)
        - [Exercise 1: Simple calculation](#exercise-1-simple-calculation)
        - [Exercise 2: Calculate a mortgage](#exercise-2-calculate-a-mortgage)
    - [Modules, functions and packages](#modules-functions-and-packages)
        - [Modules](#modules)
        - [Packages](#packages)
        - [Functions](#functions)
        - [How to use modules](#how-to-use-modules)
        - [How to call functions](#how-to-call-functions)
        - [Exercise 3: Calculate the area of a round](#exercise-3-calculate-the-area-of-a-round)
        - [Exercise 4: Test sin() function](#exercise-4-test-sin-function)
        - [Exercise 5: Test random](#exercise-5-test-random)
    - [Challenge](#challenge)
    - [References](#references)

<!-- /TOC -->
In the previous chapter, We introduced the basic knowledge about terminal on Mac and how to navigate file system in Terminal, using shell, creating the first python script and execute it... In this chapter, we want to focus specifically on Python basics, including `variables`, basic `data types`, `arithmetic`, `functions` and several commonly used `modules` you need to know about to get up and going as a python developer. After this chapter, you can use python as your daily tool, at least you can build a calculator to evaluate your business mode or build up your start-up financial plan. You can check out [here](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/) for a reference case study, about `Calculate Marketing Objective for Your Media Startup`. And you can also find more cases in our DNN website.

Tip: search `python` to filter out the cases accomplished by 2017 MA students.

## Objective of this week

* Understand python basics
* Use python interactive environment to do simple tasks
* Can use Python as a daily tool -- at least a powerful calculator

## Familiar with python interactive mode

Python has two basic modes: script and interactive.  
`The script mode` is the normal mode where the scripted and finished .py files are run in the Python interpreter.  
`The interactive mode` is a command line shell which gives immediate feedback for each statement.

### Deference between two modes

* A `.py` file can only be executed in script mode.
* In interactive mode , you can only enter one line and execute one line each time, while in script mode, you can execute all the code in the file at once by running the .py file directly.
* The interactive mode is primarily used to debug the code and testing.

### Enter and exit interactive mode

When you are in script mode, you can type `python` or `python 3` to enter the interactive mode. The notation `>>>` means that you have already entered interactive mode. And type`control + d` to exit from interactive mode.  

## Variables and assignment

Think of a variable as a name attached to a particular object. In Python, variables need not be declared or defined in advance. Therefore you should give it a definition or assign value to it. The equal sign `=` is used to assign values to variables.

e.g.1:

```python
>>> a=1+2
>>> print a
```

"a" is variable, so you give it a definition that a equals 1+2, and print a you will get 3 in terminal.

e.g.2:

```python
>>> fruit1='apple'
>>> print fruit1
apple
```

It means you define fruit1 as apple, so you will get apple in terminal.
**Notes** You should use `''` to hold apple, or the terminal will think apple is another variables. You can't assign variables to other variables.``

e.g.3:

```python
>>> a='hello'
>>> b='world'
>>> c=a+' '+b
>>> print c
hello world
```

a, b, c are all variables, and you can do calculation like normal numbers.

## Basic data types

In fact,there are so many different kinds of data you can use to define the variables. Different data types are totally different.
Following are some basic data types.

### Int

`int` means integer, like 7, 8, 9 and so on. those numbers are integer.

e.g.4:

```python
>>> a=int(7.9)
>>> print a
7
```

`int()` is a function, which converts the number in `()` to an integer.

### Float

`float` means a number with decimal, like 2.1, 3.8, 5.6 and so on.

e.g.5:

```python
>>> b= float(7)
>>> print b
7.0
```

`float()` means you converts the number/integer in `()` to a decimal.

### Str

* `str` means string, a sequence of characters, like quiet, asdf, HK_NY and so on.
* Strings can be created by enclosing characters inside a single quote or double quotes, like `''`,`""`. Even triple quotes can be used in Python but generally used to represent multi-line strings and doc-strings.

**Note**: what if there is a `""` in your line, how do you print this string line?  
e.g.6: please print `Xiao Ming says " I don't feel well today."`.

```python
>>> print "Xiao Ming says \"I don't feel well today\""
Xiao Ming says "I don't feel well today"
```

What does `\"` means?, let's talk about this more.

### Escape character

According to wikipedia, An [escape character](https://en.wikipedia.org/wiki/Escape_character) is a character which invokes an alternative interpretation on subsequent characters in a character sequence.
So basically when you need to use special characters in a string, you should use escape character. Usually, we uses the \ (backslash) as an escape character for. The following are the commonly used examples.

* `\'` means single quote
* `\"` means double quote
* `\\` means backslash
* `\n` means new line
* `\r` means carriage return
* `\t` means tab
* `\b` means backspace
* `\f` means form feed
* `\v` means vertical tab

e.g.7:

```python
>>> print "I don't feel well \ntoday"
I don't feel well
today
```

## Arithmetic

### Basic rules

| Operator          | Description                                                                                                         | Example                                                |
|-------------------|---------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| `+` Addition        | Adds values on either side of the operator.                                                                         | a + b = 30                                             |
| `-` Subtraction     | Subtracts right hand operand from left hand operand.                                                                | a – b = -10                                            |
| `*` Multiplication  | Multiplies values on either side of the operator                                                                    | a * b = 200                                            |
| `/` Division        | Divides left hand operand by right hand operand                                                                     | b / a = 2                                              |
| `%` Modulus         | Divides left hand operand by right hand operand and returns remainder                                               | b % a = 0                                              |
| `**` Exponent       | Performs exponential (power) calculation on operators                                                               | a**3 =1000, a=10                                       |
| `//` Floor Division | The division of operands where the result is the quotient in which the digits after the decimal point are removed.  | 9//2 = 4, 9.0//2.0 = 4.0, -11//3 = -4, -11.0//3 = -4.0 |

### Exercise 1: Simple calculation

a=10//3, b=10%3, c=10**3, print a, b, c.

```python
>>> a=10//3
>>> b=10%3
>>> c=10**3
>>> print "a=",a, "b=",b, "c=",c
a= 3 b= 1 c= 1000
```

### Exercise 2: Calculate a mortgage

Question: Calculate mortgage based on the following formula: (Assign "i" "P" "n" specific numbers by yourself.)

![Mortgage loan formula](assets/mortgage-loan-formula.png)

*[formula from wikipedia](https://en.wikipedia.org/wiki/Mortgage_loan) , you can check out what each variable represents.*

Example:
i=0.05, n=20, P=5000000, A=i*P*(1+i)**n/((1+i)**n-1)
print "A=",A

```python
>>> i=0.05,
>>> n=20,
>>> P=5000000,
>>> A=i*P*(1+i)**n/((1+i)**n-1)
>>> print "A=",A
A= 401212.935953
```

## Modules, functions and packages

### Modules

In programming, a module is a piece of software that has a specific functionality. For example, when playing a chess game, one module would be responsible for the game logic, and another module would be responsible for drawing the game on the screen. Each module is a different file, which can be edited separately. There are diverse modules on the Internet,like [numpy](http://www.numpy.org/), [scipy](https://www.scipy.org/) and [geopy](https://geopy.readthedocs.io/en/stable/) so on.
Different modules contains different functions relating to modules' features.

### Packages

A package is a collection of Python modules, a directory of Python modules containing an additional `__init__.py` file, to distinguish a package from a directory that just happens to contain a bunch of Python scripts. Packages can be nested to any depth, provided that the corresponding directories contain their own `__init__.py` file. For example, you can see that [python twitter](http://python-twitter.readthedocs.io/en/latest/index.html) is a package with a `__init__.py` file.
![Python twitter package](assets/python-twitter-package.png)

### Functions

A function is a block of organized, reusable code that is used to perform a single, related action. Functions provide better modularity for your application and a high degree of code reusing.

As you already know, Python gives you many built-in functions like `print()`, etc. but you can also create your own functions. These functions are called user-defined functions.

Here are simple rules to define a function in Python.

* Function blocks begin with the keyword def followed by the function name and parentheses `()`.

* Any input parameters or arguments should be placed within these parentheses.

* The code block within every function starts with a colon (:) and is indented.

* The statement `return` means exiting a function, optionally passing back an expression to the caller. A return statement with no arguments is the same as return None.

e.g.8:

```python
# Here is the function definition
>>> def printinfo(name, age): #printinfo is function name, name and age are parameters
   >>> print "Name: ", name
   >>> print "Age ", age
   >>> return;
# Now you can call printinfo function
>>> printinfo(age=18, name="yucan")
Name:  yucan
Age  18
```

### How to use modules

In python, we use `import` statements to call a certain modules or functions. `import` means import a module from the library/package you download or install from the internet. You can import modules by writing `import`+ module name on terminal. And there are many modules out there, commonly used modules like [numpy](https://docs.scipy.org/doc/numpy/user/quickstart.html) *click to check out more details.*

There are 3 ways to import a module, usually we use the first method, but you will learn the last two method in the later stage.

* import module
* from module.xx.xx import xx
* from module.xx.xx import xx as rename

For example, `import numpy` is to import a module called numpy. (Generally, "import" is always written on the top to indicate readers what kind of module and functions you will use.) After you import the module, you can use `help(module)` to check out their documentations

e.g.9:

```python
>>> import numpy
>>> help(numpy)
Help on package numpy:

NAME
    numpy

DESCRIPTION
    NumPy
    =====
    
    Provides
      1. An array object of arbitrary homogeneous items
      2. Fast mathematical operations over arrays
      3. Linear Algebra, Fourier Transforms, Random Number Generation
    
    How to use the documentation
    ----------------------------
    ...
```

After you learn what you want in their documentations, you can press `control + z` to exit.

### How to call functions

As you already know from the previous content that there are many functions in a module. We use *module name +`.`+function name* to call the specific functions in a module. If you don't know what are the functions in this module, you can use `help(module)` to search through their documentation or search in google to learn more.

e.g.10:

```python
>>> import numpy
>>> print numpy.pi
3.14159265359
```

This example means you choose a function called "pi" from the module "numpy". You will get pi as 3.1415927. Therefore, whenever you want to call a function, you should check out which modules contain this function, then you use `.` notation to reference to the function, and input the parameter into `()`  after the function, after executing this command, you can get the results you want.

e.g.11: use `sin` and `pi` function from `numpy` module

```python
>>> import numpy
>>> print numpy.sin(numpy.pi/6)
0.5
```

![Call python function](assets/python-call-module-function.jpg)

### Exercise 3: Calculate the area of a round

Q: Calculate the area of a round, and assign specific radius by yourself.

Example:

```python
>>> import numpy
>>> r=5
>>> area=r**2*numpy.pi
>>> print "area=", area
area= 78.5398163397
```

### Exercise 4: Test sin() function

Q: Calculate sin pi/3

Example:

```python
>>> import numpy
>>> a=numpy.sin(numpy.pi/3)
>>> print "a=",a
a=0.8660254037844386
```

### Exercise 5: Test random

*If you don't know `random` module and what functions in there, you can google this module or look at their [documentation](https://docs.python.org/3/library/random.html) to learn several different functions*

Q: Randomly select a number from 1 to 10

Example:

```python
>>> import random
>>> print random.randrange(1,11)
Answer should be one of int numbers in 1 to 10
```

## Challenge

* Build a mortgage calculator - given principal P, interest rate r and load period n, calculated the amortized monthly payment A
* Calculate the area of a circle given its radius r
* Given the length of hypotenuse of a right triangle, calculate the length of its legs. You may want to get values like $$sin(\frac{\pi}{6})$$ via numpy.pi and numpy.sin
* Generate 10 random numbers. (it is OK to run your script 10 times)

## References

* [Chapter 1, 2, 3 of official Python 2 tutorial](https://docs.python.org/2/tutorial/), you can check out the python basics tutorial in chapter 1-3.
* [Python format string](https://pyformat.info/). They introduce some most common use-cases covered by the old and new style string formatting API with practical examples.
* [Python doc modules](https://docs.python.org/3/tutorial/modules.html)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)