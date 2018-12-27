# Week 03 - Control Flow

<div id="toc">

<!-- TOC -->

- [Week 03 - Control Flow](#week-03---control-flow)
    - [Objective](#objective)
    - [Use "Help" more to learn by yourself](#use-help-more-to-learn-by-yourself)
    - [Bool and comparisons](#bool-and-comparisons)
        - [Logic operators](#logic-operators)
        - [Comparison operators](#comparison-operators)
        - [Str comparison](#str-comparison)
        - [Int comparison](#int-comparison)
    - [Control flows](#control-flows)
        - [Execute code selectively: If-else Statement](#execute-code-selectively-if-else-statement)
        - [Repeat similar operations: loop](#repeat-similar-operations-loop)
            - [For loop](#for-loop)
                - [Use for statement to pick up values](#use-for-statement-to-pick-up-values)
                - [Use for loop to calculate](#use-for-loop-to-calculate)
            - [While loop](#while-loop)
            - [Difference between for loops and while loops](#difference-between-for-loops-and-while-loops)
        - [Break and Continue statement](#break-and-continue-statement)
            - [Break statement](#break-statement)
            - [Continue statement](#continue-statement)
        - [Integrated example: for and if](#integrated-example-for-and-if)
            - [Bonus: alternatives and more efficient calculation](#bonus-alternatives-and-more-efficient-calculation)
    - [Function](#function)
        - [Function definition (def)](#function-definition-def)
        - [Bonus: Scope of variables in function](#bonus-scope-of-variables-in-function)
    - [Errors and Exceptions](#errors-and-exceptions)
        - [Try and except](#try-and-except)
        - [Raising errors](#raising-errors)
        - [Exception error types](#exception-error-types)
    - [Common coding patterns](#common-coding-patterns)
        - [Representing a dataset](#representing-a-dataset)
        - [Handle repeated works](#handle-repeated-works)
        - [Infinite loop (daemon)](#infinite-loop-daemon)
        - [REPL](#repl)
        - [if..else; OR try..except](#ifelse-or-tryexcept)
        - [Multiple loop](#multiple-loop)
        - [Try sub-tasks and regroup success/ fail cases](#try-sub-tasks-and-regroup-success-fail-cases)
        - [Test and batch execution for repeated tasks](#test-and-batch-execution-for-repeated-tasks)
    - [Exercises and Challenges](#exercises-and-challenges)
        - [Generate detailed mortgage schedule](#generate-detailed-mortgage-schedule)
            - [Hint on table formatting](#hint-on-table-formatting)
            - [Hint on math formula](#hint-on-math-formula)
        - [Automatic writer for financial report](#automatic-writer-for-financial-report)
    - [References](#references)

<!-- /TOC -->

</div>

Previously, We learn Python basics including data types, arithmetic, functions and several commonly used modules, with which help, you can build a calculator to do some simple case analysis. This week, we will step further to learn composite data types, the function and method of how to use them. Meanwhile, we will touch hands on the basic control flows to better understand the logic behind the coding works. After that, you can create some functions by your own so that you can use Python to do more.

## Objective

* Master the composite data type [] and {} in Python
* Master the control logics in Python, especially if and for
* Further understand the different roles of text editor and interpreter. Be comfortable writing batch codes in .py file and execute in Shell environment.
* Bonus: Understand Python engineering

## Use "Help" more to learn by yourself

In the Terminal of your computer, use `help` for any instruction for using Python functions.  

**Note**

* Type 'q' to quit help;
* Type 'j' to scroll down;
* Type 'k' to scroll up.

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
x == y: False
>>> print("x != y:", x != y)
x != y: True
>>> print("x < y:", x < y)
x < y: True
>>> print("x > y:", x > y)
x > y: False
>>> print("x <= y:", x <= y)
x <= y: True
>>> print("x >= y:", x >= y)
x >= y: False
```



## Control flows

A control flow is a block of programming that analyses variables and chooses a direction in which to go based on given parameters. In python, all codes and statements are faithfully executed in exact top-down order. But what if you want to change the flow?

For example, you want the program to take some decisions and do different things depending on different situations, such as printing 'True' or 'False' depending on the different comparison and test?

Under such circumstances, using control flow statements will help you manipulate data better. There are several control flow statements we will learn in this chapter.

**NOTE:** In `control flows` chapter, we will encounter a lot of `indentations` when handling if/for/while/def/class. It is hard and inconvenient to type in Python shell, so please write down the codes in text editor and save it as a `.py` file, so that you can just execute the file once to get the answer. If you forget how to do this, please refer to [chapter 2](/notes-week-02.md#python-has-two-basic-modes-script-and-interactive).

### Execute code selectively: If-else Statement

`if...else` statement is used to conditionally execute a statement or a block of statements. Conditions can be true or false, execute one thing when the condition is true, something else when the condition is false.

```python
if ...:   #close with an ':'
    print(sth)  #indented
elif ...: # elif = else if
    print(sth)
else:
    print(sth)
```

**Note:** All function definitions or condition comparisons should end with a `:`, and all the content in those functions and conditions need to be indented. you can just indent with clicking `tab`.

Take the case that we talk about chapter 2 as an example. (The full version of the case is [here](https://dnnsociety.org/2018/02/01/calculate-marketing-objective-for-your-media-startup/))

> Example 14: We want to know how much is the cost with the number of users we have.  When the number is less than 50,000, the cost will be 10,000. If the number is not less than 50,000, then cost=10000+0.1×(number_of_users -50000）. The actual number of users we have now is 100,000. The if-else statement will be as fellow:

```python
number_of_users = 100000
if number_of_users <= 50000:
    cost = 10000
else: # number_of_users > 50000
    cost = 10000 + 0.1 * (number_of_users - 50000)
print (cost)
```

Output:

```text
15000.0
```

> Example 15: If there is two charge plans when the number of users is more than 50,000.
>1. when  50,000≤the number of user≤100,000, the cost= 10000+0.1×(number_of_users -50,000);
>2. when the number of user ≥100,000, the cost=10,000 + 0.1×(100,000 -50,000) + 0.2 * (number_of_users - 100,000).
>3. The actual number of users we have now is 120,000. 

The if-else statement will be as follows:

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

Output:

```text
21000.0
```

### Repeat similar operations: loop

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

Output:

```text
1
2
3
4
5
6
7
8
9
10
```

**Note**: The `range()` function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default).`(1,11)` means values from 1 to 10 (not including 11)

Example 19: Square of every integer from 1 to 10.

```python
for i in range(1,11):
    print(i**2) #or i*i
```

Output:

```text
1,4,9,16,25,36,49,64,81,100
```

##### Use for loop to calculate

Example 20: Calculate the summation from 1 to 100.

```python
total = 0
for i in range(1, 101): # numbers which are >=1 and <101
    total = total + i
print(total)
```

Output:

```text
5050
```

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

Output:

```text
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

Output:

```text
1
2
```

#### Difference between for loops and while loops

1. While Loops allow you put a condition in it, like `while i<10`, and it will stop when the condition no longer being meet( i >= 10). you can also substitute in a boolean(true/false) for 10 as well as many other types of variables.

2. For Loops allow you to run through the loop many times you'd like it to run through the problem such as `for i in range(0,100)`, this will continually increase i until that condition returns false(>100), you can replace 10 with other numbers and variables, like `for name in name_list`, means that you want to loop the whole name_list to run through the problem. And it will quit once the condition is no longer being met.

3. Generally speaking, if you want to use loop to do conditional comparison, `while` loops is work for you, if you want to loop every elements of a whole list, `for` is better.

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

Output:

```text
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

Output:

```text
2
3
4 #number 5 is missing, while the loop continues
6
7
8
9
```

### Integrated example: for and if

Example 21: Calculate the break-even point of the simple business model.

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

Output:

```text
subscribers= 40000
```

#### Bonus: alternatives and more efficient calculation

Here is a challenge upon last example: Try to scale up the parameters by a uniform factor and test the efficiency of your program. For example, let `Fixed_Cost = 3000000` and `Content_Cost = 7000000`, the resulting number of subscribers will scale up by the same factor. However, it takes much more time for your program to run because the loop executes for more iterations. Can your program scale up 1000x, or 1000000x? If it takes very long to get the result, how do you think you can improve?

The basic idea is to "jump" somehow, instead of increasing the number of subscribers by only `1` every time. You can jump by `100` or `1000` depending on the problem scale. A more efficient solution is the [bisection method](https://en.wikipedia.org/wiki/Bisection_method). See the discussions from our students on [Issue #34](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/34).

## Function

### Function definition (def)

A function is a block of code which only runs when it is called. You can call this function by passing parameters into a function. Then the function can return data as a result.

```python
def function_name(parameters): #define function
    control flow #use control flow
    return  #return to default or specified value

function_name("parameter1") #call the function
```

**How `def` works**

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

Output:

```text
-9990.0
```

The advantage of using "def" is that you can recall the function again and again. Just change the parameter. For example:

```python
print(calculate_profit(100))
print(calculate_profit(1000))
print(calculate_profit(10000))
print(calculate_profit(100000))
```

Output:

```text
-9990.0
-9900.0
-9000.0
-5000.0
```

### Bonus: Scope of variables in function

Try the following test program:

```python
a = 1
print('(outside) a=', a)

def change():
    a = 2
    print('(in change) a=', a)
change()

print('(outside) a=', a)
```

The result is:

```shell
%python3 test.py
(outside) a= 1
(in change) a= 2
(outside) a= 1
```

One can see that the "same" variable `a` has different value inside and outside a function. The operation inside a function does not affect the outer variable `a`. This is a matter of "scope". Every variable, function, or more generally "token"/ "symbol" in Python has its scope of effectiveness. The inner function definition of `a` masks the definition outside `a`. In order to make the operation inside one function able to operate the variables outside, one can use `global` and `non-local` keywords. Please see more details from [this blog post](https://www.datacamp.com/community/tutorials/scope-of-variables-python). However, using global variable is not recommended because it makes the program hard to maintain when the size becomes large. There are many ways to work around. In the above example, we can use simply pass `a` into the function via argument list and use return statement to return the changed value:

```python
a = 1
print('(outside) a=', a)

def increase(a):
    a = a + 1
    print('(increase) a=', a)
    return a

a = increase(a)
print('(outside) a=', a)

a = increase(a)
print('(outside) a=', a)
```

We change the simple assignment to addition to show the result of multiple execution. The output is:

```python
%python test.py
(outside) a= 1
(increase) a= 2
(outside) a= 2
(increase) a= 3
(outside) a= 3
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
x = 5
if x < 10:
    raise ValueError('x should not be less than 10!')
```

### Exception error types

There are several common exception errors:

* `IOError`. If the file cannot be opened
* `ImportError`. If python cannot find the module
* `ValueError`. Raised when a operation or function receives an argument that has the right type but an inappropriate value
* `KeyboardInterrupt`. Raised when the user hits the interrupt key (normally Control-C or Delete)

Note that "Exception" is in fact `class` in Python. Python has many built-in exceptions that are grouped in a hierarchy known as inheritance/ derivation. The benefit is that, the outmost layer of codes can catch a broader exception while inner layer of codes can raise a narrower/ more specific exception at the same time. For the full list of built-in exceptions, please see the official documentation on [exceptions](https://docs.python.org/3/library/exceptions.html).

## Common coding patterns

### Representing a dataset

A usual dataset can be think of as a table composed of rows and columns. One row is one **data point**/ sample/ response/ observation/ record/ entry/ object. One column is one **feature**/ variable/ property/ dimension. You may see different terms from different literature and problem domain. In our discussion the **strong** term will be used but other terms are also used interchangeably sometimes, especially when discussing with external references.

There are several common ways to represent a dataset:

- List-of-list/ 2D array/ Matrix

  ```python
  dataset = [
      [f_11, f_12, ... f_1m], # 1st data point
      [f_21, f_22, ... f_2m], # 2nd data point
      ...
      [f_n1, f_n2, ... f_nm]  # nth data point
  ]
  ```

  One advantage of this notation is its compact representation of a lot of data. Another advantage is its natural fit into scientific computation, especially machine learning routines, because many such routines rely on a matrix structure. The disadvantage is the lack of "variable names", or "headers" in a table representation. You need to maintain such information outside this matrix structure.
  
- List-of-dict/ list of records/ records

  ```python
  dataset = [
      {
          "feature1": value_11,
          "feature2": value_12,
          ...
          "featurem": value_1m,
      }, # 1st data point
      {
          "feature1": value_21,
          "feature2": value_22,
          ...
          "featurem": value_2m,
      }, # 2nd data point
      ...
      {
          "feature1": value_n1,
          "feature2": value_n2,
          ...
          "featurem": value_nm,
      }, # nth data point
  ]
  ```

  One can readily see the advantage of this representation compared with the previous one is its high readability. Although Python's grammar is flexible, there are certain meaning implied by list and dict. For a **list**, the elements should be of the same nature. Or say, they are the same category of objects. You can put "apple" and "orange" in the same list if the list intends to hold a series of fruits. A counter-example, which looks unnatural, is `["apple", "orange", 2018, "Sept", "University"]`. As to a **dict**, the keys are usually of different nature. One key usually describes certain aspect of an element; All the keys when put together completely describe one element. Once you understand the nature of list and dict, you feel the second way of dataset representation straightforward: Every element of outer layer list is one data point; Every key of inner dict is one variable; The value of variable `v` and data point `i` can be referenced by `dataset[i]["v"]`.

  This way of data representation is most commonly found in many data APIs (See chapter 4). The advantage is that we do not need another structure to store table header. However, this is also the disadvantage -- the table header/ dict keys are repeated as many times as number of data points, making data transfer rather inefficient.

- Dict-of-list/ series/ column-first representation

  ```python
  dataset = {
      "feature1": [value_11, value_12, ... value_1m],
      "feature2": [value_21, value_22, ... value_2m],
      ...
      "featurem": [value_n1, value_n2, ... value_nm],
  }
  ```

  This representation gives a good trade-off between the previous two representations. The format also has a famous name called "column-based representation", which is common in numeric computation software/ statistics software like MATLAB and R. You will also find this representation an easy fit into visualisation libraries. For example, `matplotlib.pyplot.plot(dataset["feature1"], dataset["feature2"])` works smoothly.
- Dict-of-dict
  
  This format is seen less frequently but one has no problem understand it. Note that `dict` can be thought of a powerful version of `list`, by assigning index to keys and elements to values. You will find the syntax to refer the same element from original list and this new dict the same. The minor difference is that the keys of `dict` is not ordered but the indices of a `list` are ordered. Without bothering with details, one can convert list into dict with this shortcut: `dict(zip(range(len(mylist)), mylist))`.

### Handle repeated works

As a beginner, the best approach to problem solving is "bottom-up". We will show you a lot of this approach during lectures and class demos. You need to pay attention how the instructor solves a problem, instead of focusing on the final code block that solves the problem. That is, **process is more important than result**. In this quasi text book, we note a common pattern here.

You will meet a lot of repeated works in programming. For example, downloading all the PDFs from a website, add the scores of selected students by 1, change the format of a whole dataset. Saving repeat manual work is one core advantage of programming. However, before you try to touch all the input elements, you need to solve the case for one element. Make sure you test different scenarios and find it work before proceed. Then you can wrap the logics into a function and invoke following pattern.

```python
def select(element):
    if condition: # change "condition" to True if you want to select every element
        return True
    else:
        return False

def handle(element):
    # Do something with element
    result = ...
    return result

input_list = [...] # Put the repeated problems into this list
output_list = [] # output list is empty at the beginning

for element in input_list:
    if select(input):
        result = handle(element)
        output_list.append(result)
```

`for` loop is your best friend to handle repeated works where the problem size is predefined.

You can further structure your code in this way.

```python
for element in input_list:
    if not select(input):
        continue
    result = handle(element)
    output_list.append(result)
```

**QUIZ**: What are the pros and cons of those two different writing styles?

### Infinite loop (daemon)

Sometimes, you want your program to work infinitely: wait for certain input; take action and wait again. This is a common pattern in system design. For example, a web server constantly takes "HTTP request" from client software (e.g. web browser) and send "HTTP response" to the client. You don't want the server to stop just after serving one HTTP request. Similarly, imaging you are going to write a Python script that monitors No. 8 Typhoon signal and post a Twitter when [HKO](http://www.hko.gov.hk/detail.htm) issues the warning (Ah! "Artificial Intelligence"! Robot!). You don't want the program to exit after posting one message. Instead you want to program to keep working until you terminate it/ interrupt it. A common pattern is as follows.

```python
import time
i = 0
while True:
    print('Entering a new round of loop')

    # Do something useful here
    print('Working hard! This is the %d-th time' % i)
    ...

    print('Leaving a new round of loop')
    i = i + 1 # Count the number iterations
    time.sleep(1000) # to avoid too frequent poll of external resources
```

Once you execute this script, a lot of messages will be output to the screen non-stop. You can terminate the script, or technical "interrupt" the script by pressing `control+c` if you are in a Terminal/ shell environment. Always keep this hotkey in your mind. It is life saving sometime when you go deeper into the journey. For example, your web scraper may have bug and consumes extremely large amount of network data when you execute the script. You don't have to wait till the end of scraping. Just use `control+c` to end the program. Note:

- It is a convention for shell environment, so you can also terminate other Unix/ Linux commands in this way.
- You can also terminate a for-loop using the same method.
- You can also terminate a function call that does not respond after a while using the same method.

### REPL

Read-Evaluation-Print-Loop (REPL) is a common pattern similar to the daemon pattern above. Actually, you have already see several times such pattern in action. One is the system shell (inside Terminal), another is the Python shell (Python interactive environment). The shell environment allows you to continuously input commands; It then evaluate your input to calculate the result; then it goes back to get another line of input, a.k.a. "loop". A REPL in Python looks like this:

```python
while True:
    user_input = input('Prompt message:')
    if user_input == 'exit':
        break
    else:
        output = evaluate(user_input)
        print(output)
```

### if..else; OR try..except

Consider a common problem in programming: given number of students as `n` and number of books as `m`, calculate how many books each student can get. The answer seems straightforward: `m / n`.

However, there is a glitch: `n` can be `0` and the mathematical meaning of division is undefined in this case. We need to determine whether `n` is equal to `0` before the calculation. If so, we simply output a warning message like "can not divide books among 0 students". Here are two ways to implement this:

if..else pattern:

```python
if n > 0:
    result = m / n
    print(result)
else:
    print("can not divide books among 0 students")
```

try..except pattern:

```python
try:
    result = m / n
    print(result)
except ZeroDivisionError:
    print("can not divide books among 0 students")
```

Some advocates of `try..except` in Python community tend to abuse `try` in all places where `if` was used. The code is usually shorter with the help of `try..except` structure, especially when you are in a large project with many layers of function calls. The downside is that, it is difficult to find which `except` finally handles the error, because 1) `except` selects certain `Exception` it is interested in; 2) `except` can further `raise` the `Exception` if it can not handle it. In order to make the error handling explicit, you resort to the `if..else` pattern but tend to write longer ("verbose" in programming jargon) codes, especially when there are many layers of function calls.

### Multiple loop

Suppose you are a matchmaker and want every PR firm to get in touch with every journalist. Following constructs are given:

```python
def touch(PR, journalist):
    # .... this function simply let a single `PR` firm get in touch with a single `journalist`
    pass

PR_list = [
    #...
]

journalist_list = [
    #...
]
```

Now you can use a multiple loop to call each possible pair of combinations:

```python
for p in PR_list:
    for j in journalist_list:
        touch(p, j)
```

Python is flexible. Codes are organised into "blocks" seen as a chunk of codes with the same indentation level. We already see expressions that creates code blocks like `for`, `if`, `def` and `with`. Blocks can be nested into larger blocks so that one can built more complex logics.

### Try sub-tasks and regroup success/ fail cases

When you further dive into the programming journey, you will find codes easily raise errors. You can use `try...except` to catch the errors and treat them separately. A common pattern is to divide your task into many smaller sub-tasks, `try` each one and assemble the results. For example, when you scrape a list of webpages, some may succeed and some may fail. You don't want the whole program to crash upon one fail case. Following structure may help:

```python
tasks = [] # store all the components

success = []
fail = []
for task in tasks:
    try:
        # do something with task
        result = do_something_with(task)
        success.append((task, result))
    except Exception as e:
        fail.append((task, e))

for (task, result) in success:
    # maybe you want to assemble the `result`s from successful tasks
    pass

for (task, e) in fail:
    # analyse and handle the failed tasks
    pass
```

In our web scraping example, `tasks` can be a list of URLs to scrape and `do_something_with` is the single page scraping function that takes a URL as input and return the scraped data items if successful. How to implement this `do_something_with` function is the topic of [notes-week-07.md](notes-week-07.md) but it is good to learn the basic idea here.

### Test and batch execution for repeated tasks

Suppose you can handle all the tasks by:

```python
...
for t in tasks:
    o = handle(t)
...
```

The size of `tasks` may be very large which takes days or months to run. Sometimes, you want to do some pilot testing before setting it at full scale. Or, you risk running into errors after some heavy computation. In Python, we can use the list slicing syntax to cut down the task size and do not break the overall structure of the code. For example, if we want to test for the first 10 entries, we can:

```python
for t in tasks[:10]:
    o = handle(t)
```

When we finish testing, we can comment out the list slicing part:

```python
for t in tasks: #[:10]:
    o = handle(t)
```

Suppose you have 10 machines and 1000 tasks in `tasks`. You can copy the same code to all the machines and slice `tasks[i * 100: (i + 1) * 100]` for the i-th machine (i starts from 0).


## Exercises and Challenges

### Generate detailed mortgage schedule

In [notes-week-02.md](notes-week-02.md#exercise-2-calculate-a-mortgage), we made a mortgage calculator using the amortised formula from Wikipedia. Now that we have the monthly instalment number, we can further generate the mortgage schedule that a regular user is highly interested. A mortgage schedule is basically a table in which one row represents the status of a month. One row contains the following information: `month`, `instalment`, `interest in instalment`, `principal in instalment`,  `outstanding principal after this instalment`. The first 12 months are as follows. Try to print this table.

```text
Month	Instalment	Interest	Principal	Outstanding
001	65995.57	41666.67	24328.91	9975671.09
002	65995.57	41565.30	24430.28	9951240.82
003	65995.57	41463.50	24532.07	9926708.74
004	65995.57	41361.29	24634.29	9902074.46
005	65995.57	41258.64	24736.93	9877337.53
006	65995.57	41155.57	24840.00	9852497.53
007	65995.57	41052.07	24943.50	9827554.02
008	65995.57	40948.14	25047.43	9802506.59
009	65995.57	40843.78	25151.80	9777354.80
010	65995.57	40738.98	25256.60	9752098.20
011	65995.57	40633.74	25361.83	9726736.37
012	65995.57	40528.07	25467.51	9701268.86
...
```

#### Hint on table formatting

**Hint:** Use the floating point formatter to limit numbers to two digits. Use `{:03d}` to pad with extra zeros. In order for the table to look aligned, you may want to use `\t` as the delimiter. Actually, `\t` means `table` and is used to align texts to next table marker.

The initial part of the program with parameter settings are as follows:

```python
r = 0.05 / 12
n = 20 * 12
P = 10000000
A = P * (r * (1 + r) ** n) / ((1 + r) ** n - 1)
print(A)
outstanding = P
m = 0
```

#### Hint on math formula

**Hint:** The key of this exercise is about calculating the schedule **all in Python**. Given week02's knowledge, you can calculate and print out the result line by line. After week03, you will be able to use a loop to repeat the procedure and saves some codes. Following is an example of how to calculate the mortgage status of first month.

```python
# Suppose we already have r, n, P, A
# value of A is "instalment" in our natural language

# Initially
outstanding = P

# After the first month
interest_in_instalment = r * outstanding
principal_in_instalment = A - r * outstanding
outstanding = outstanding - principal_in_instalment

# Now try to print in our expected format
print(...)

# After the second month
# Try to continue the process
```

### Automatic writer for financial report

Financial report usually possesses some apparent patterns. We can analyse the patterns and use string templating to perform automatic writing. Actually most of the "AI" based "robotic journalist" is no complex than string templating. After this chapter, you can even use conditional branches to plugin corresponding text. For example, when the value goes up, you say "increases by" and when the value goes down, you say "decreases". People who write this kind of template is called "meta reporter".

You can approach in following ways:

1. Use regular string templating. The `str.format` function can be useful, especially its keyword argument/ dictionary form.

2. Use `jinja2`. It provides a more expressive templating environment. You can even write branching and looping logics in its template. `jinja2` is commonly used in web development but is not limited to that. With the help of `jinja2`, we can separate the concern: 1) frontend developer, or say "meta reporter", focuses on the presentation and language, i.e. how to embed the variables into the right place of the template; 2) backend developer, or say data supplier, focuses on data ingestion and data analysis. The bridge of the two worlds is a spreadsheet.

## References

* Chapter 4, 5, 6, 8, 9 of official Python 3 [tutorial](https://docs.python.org/3/tutorial/)
* Another [tutorial](http://www.runoob.com/python/python-object.html) with many examples (Chinese)

------

If you have any questions, or seek for help troubleshooting, please [create an issue here](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/new)