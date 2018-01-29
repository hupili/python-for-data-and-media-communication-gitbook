# Course Outline

## Week 1 - Hands-on the Terminal

**Objective:**

> * Able to navigate file system in Terminal, using shell
> * Create the first python script and execute it

MAC:

* `Cmd+space` to open Spotlight; search “Terminal” to open terminal

Shell commands:

* `cd` to switch working folder
  * Path separated by `/`
  * Special paths: `.`,`..`,`-`,`~`
* `ls`to list files/ folders in current folder
* `pwd` to check current working folder
* `ls`/`pwd` is your friend; type often to make sure where you are
* `touch` to create empty new file; mkdir to create new directory
* `python` to execute python scripts \(usually in `.py` but not necessary\)
* Format of shell commands: 
  * `<command-name> <arg1> <arg2>..` \(space separated arguments\)

Challenge:

1. Write a Python script to output "Good evening" in the Terminal.

## Week 2 - Use Python as a daily tool

**Objective**:

> * Can use Python as a daily tool -- at least a powerful calculator

Python language introduction:

* Variables and assignment
* Basic data types: int, float, str
* Arithmetic:
  * `+`, `-`, `*`, `/`, `//`, `%`, `**`
  * `math` , `numpy` \(may need `pip`\)
* Use functions and modules: `import`; `.` notation; `()` notation.
* Common modules
  * `sys`
  * `numpy`, `scipy`
  * `str.*` functions
  * `random`

Challenge:

1. Build a mortgage calculator - given principal `P`, interest rate `r` and load period `n`, calculated the amortised monthly payment `A`
2. Calculate the `area` of a circle given its radius `r`
3. Given the length of hypotenuse of a right triangle, calculate the length of its legs. You may want to get values like $$\sin(\frac{\pi}{6})$$ via `numpy.pi` and `numpy.sin` 
4. Generate 10 random numbers. \(it is OK to run your script 10 times\)

## Week 3 - Python for anything

**Objective**:

> * Master the control logics in Python
> * Understand Python engineering

Python language:

* `help`
* Composite data types: `list` `[]`, `dict` `{}`
* Control flow:
  * `for`, `while`
  * `if`
  * `try..except`
* Function, class, module:
  * `def`
  * `class`
  * `*.py`; `from`, `import`



