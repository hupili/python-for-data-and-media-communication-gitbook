Python 2 and Python 3 are mostly the same during our discussions. However there are some differences if you explore further. During this semester, we base our discussions and exercises on Python 3. We highlight some main differences here for your reference. To read further, you can click [here](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html#the-print-function)

## pip and pip3

If you want to install modules for Python3, please use `pip3` . To install in user mode, you can use

```
pip3 install --user {name-of-the-module}
```

## syntax of print

Python 2’s print statement has been replaced by the`print()`function, meaning that we have to wrap the object that we want to print in parantheses.

Python 2 doesn’t have a problem with additional parantheses, but in contrast, Python 3 would raise a`SyntaxError`if we called the print function the Python 2-way without the parentheses.

However, if we have multiple objects inside the parantheses, we will create a tuple, since`print`is a “statement” in Python 2, not a function call.

## str, bytes, encoding and decoding

Python 2 has ASCII`str()`types, separate`unicode()`, but no`byte`type.

Now, in Python 3, we finally have Unicode \(utf-8\)`str`ings, and 2 byte classes:`byte`and`bytearray`s.

## How to set up Python 2.7 and Python 3 at the same time on your Mac OSX?

You can follow the steps in this[ Link](https://stringpiggy.hpd.io/mac-osx-python3-dual-install/#step1) to set up both of them. 

