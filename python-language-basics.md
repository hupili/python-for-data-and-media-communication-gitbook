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