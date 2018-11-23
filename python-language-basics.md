# Python Language Basics

<div id="toc">

<!-- TOC -->

- [Python Language Basics](#python-language-basics)
    - [Syntax](#syntax)
        - [Blanks](#blanks)
        - [Double quotes and single quotes](#double-quotes-and-single-quotes)
        - [\[\] does not work to specify precedence in formula](#\\-does-not-work-to-specify-precedence-in-formula)
        - [Multiplication operator `*` can not be omitted in formula](#multiplication-operator--can-not-be-omitted-in-formula)
        - [Letter case difference](#letter-case-difference)
        - [List range pattern](#list-range-pattern)
        - [== and =](#-and-)
        - [Append VS Extend](#append-vs-extend)
        - [For loop range](#for-loop-range)
    - [Name clash with reserved word](#name-clash-with-reserved-word)

<!-- /TOC -->
</div>

## Syntax

### Blanks

code "print \(\)", then execute

### Double quotes and single quotes

Double quotes equal to single quotes

### \[\] does not work to specify precedence in formula

\(\) is used to specify precedence in formula rather than \[\]

For example, \(\(1+r\)\*n-1\) can be executed, but \[\(1+r\)\*n-1\] can not be executed.

\[\] have other function, like `range\[1:50\]`

### Multiplication operator `*` can not be omitted in formula

Take an example:

when we exercise the mortgage calculator: `A=P*r*(1+r)`  
is different from `A=Pr\(1+r\)`, the latter one can not be executed.

### Letter case difference

```bash
p = 1
print(P)
```

You will see the error message `NameError: name 'P' is not defined` . That is because Python is **case-sensitive. **The lowercase `p` and uppercase `P` mean different variables.

### List range pattern

in range `(a,b)`, it's close to the range in the left, open the range in the right.

```python
For i in range(1,10):
    print (i)
```

You will see the outcome: 1,2,3,4,5,6,7,8,9 without 10, because the left range is included, while the right range is excluded.

### == and =

In python, notation `==` represents making a judgment / comparison. Notation `=` means assign values.

For example:

```python
df['location'] == '旺角'
#this means Iterate all elements in location column to compare whether its equal to 旺角
df['location'] = '旺角'
#this means assign 旺角 to every element in the column location
```

### Append VS Extend

when a list of elements `append` to another list, the list passing into the function `()` will be treated as an whole element.

```python
x = ['a','b']
y = [0,2,4,8]
x.append(y)
x
```

Output:

```text
['a', 'b', [0, 2, 4, 8]]
```

`extend` method extract every single items of one list and add those items one by one into the new list.

```python
x = ['a','b']
y = [0,2,4,8]
x.extend(y)
x
```

Output:

```text
['a', 'b', 0, 2, 4, 8]
```

### For loop range

Function 'Range' has 3 parameters. From XX to XX with the step size XX. The 3rd parameter is the step size. If you don't input the 3rd one, it will take 1 in default.

```python
for i in range(5,10):
    print(i)
#5
#6
#7
#8
#9
```

```python
for i in range(5,10,2):
    print(i)
#5
#7
#9
```

The parameters can be negative. At the same time, you need adjust the positions of the first and second parameters.

```python
for i in range(5,10,-1):
    print(i)
#10
#9
#8
#7
#6
```

## Name clash with reserved word

We find the following error very common when students start to work on bigger projects, especially in Jupyter notebook.

```python
TypeError: 'str' object is not callable
```

or 

```python
TypeError: 'list' object is not callable
```

In the first example, you are like to get following result when checking the type of `str`:

```python
type(str)
# str
```

This is an indicator that `str` is reassigned to some other value before. Check if you have `str=xxx` statement earlier on. `str` is a built-in function. The variable assignment changes it to another object. That is why Python complains "'str' object is not callable".

The same issue goes with `list`. Students may use `list = []` and then `list.append(xxx)` later to collect data entries. The name is intuitive but the assignment pollutes the built-in function.

Even if you change that line of assignment, Python still gives the same complaint. The reason is that Jupyter notebook has a continuously running Python engine (called "kernel") in the back. The assignment is already effective and will keep being effective in the whole session. You need to "restart kernerl" after fixing the code.

One needs to keep off reserved word like `list`, `dict`, `str`, etc. Except for that, you also want to keep away from the modules/ classes you import. One useful trick for beginner is to add `my` to your own variables when you are not sure if the variable name might clash with existing object or not.

Related issues:

- [#97](https://github.com/hupili/python-for-data-and-media-communication-gitbook/issues/97#issuecomment-441145772)