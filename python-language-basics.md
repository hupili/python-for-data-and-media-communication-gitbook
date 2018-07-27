# Python Language Basics

## Syntax

### Blanks?

code "print \(\)", then exeut

### Double quotes and single quotes

double quotes equal to single quotes

### \[\] does not work to specify precedence in formula

\(\) is used to specify precedence in formula rather than \[\]

For example, \(\(1+r\)\*n-1\) can be executed, but \[\(1+r\)\*n-1\] can not be executed.

\[\] have other function, like `range\[1:50\]`

### Multiplication operator `*` can not be omitted in formula

Take an example:

when we exercise the mortgage calculator: `A=P*r*(1+r)`  
is different from `A=Pr\(1+r\)`, the latter one can not be executed.

### Where need to be bracket? Where need to be quotation mark?

Bracket is a function quote \(e.g print \(\) \); quotation mark is used to quote the string

### Small p is different from capital P

```
p = 1
print(P)
```

You will see the error message `NameError: name 'P' is not defined` . That is because Python is **case-sensitive. **The lowercase `p` and uppercase `P` mean different variables.

### \(\) close to the range in the left, open the range in the right

```
For i in range(1,10):
print (i)
```

You will see the outcome: 1,2,3,4,5,6,7,8,9 without 10, because the left range is included, while the right range is excluded.

## Self learning resources

> //TODO: study the following pointers and add comments
>
> 这个不错，一一对应，清楚明白。 [https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro\_to\_command\_line/README.html](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html) 不过这篇有一个地方补充一下： Windows进入command line的方法是： 开始菜单 — 在搜索栏打入“cmd” 。 （这篇是台湾的系统吧， 什么“命令提示字元”.\[Dizzy\].）



