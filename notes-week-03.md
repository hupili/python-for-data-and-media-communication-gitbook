# Week 3

### 1. Use "Help"

In the Terminal of your computer. You can type `>>> help` for any instruction for using Python functions.

* If you want to know how to use 'numpy'. Type`>>>help()`  and then type`numpy` .

```
Type "help", "copyright", "credits" or "license" for more information.
>>> help
Type help() for interactive help, or help(object) for help about object.
>>> help()
Welcome to Python 2.7!  This is the online help utility.

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at http://docs.python.org/2.7/tutorial/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, or topics, type "modules",
"keywords", or "topics".  Each module also comes with a one-line summary
of what it does; to list the modules whose summaries contain a given word
such as "spam", type "modules spam".

help> numpy

help>
```

and then you can get the information about numpy as follow:

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

* Notes: Type 'Q' to quit help; Type 'J' to view up; Type 'K' to view down

## 2. Use "If-else Statement"

If-else statement is used to conditionally execute a statement or a block of statements. Conditions can be true or false, execute one thing when the condition is true, something else when the condition is false. Take the case that group one made as an example.

\(The full version of the case is here：[https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/?from=timeline](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/?from=timeline］）) ）

```
number_of_users = 100000
if number_of_users < 50000:
    cost = 10000
else: # number_of_users >= 50000
    cost = 10000 + 0.1 * (number_of_users - 10000)
print (cost)
```



