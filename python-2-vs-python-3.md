# FAQ: Python 2 and Python 3

## Difference between python 2 and 3

Python 2 and Python 3 are mostly the same during our discussions. However there are some differences if you explore further. During this semester, we base our discussions and exercises on Python 3. We highlight some main differences here for your reference. To read further, you can click [here](http://sebastianraschka.com/Articles/2014_python_2_3_key_diff.html#the-print-function)

### syntax of print

> Python 2’s print statement has been replaced by the`print()`function, meaning that we have to wrap the object that we want to print in parantheses. Python 2 doesn’t have a problem with additional parantheses, but in contrast, Python 3 would raise a`SyntaxError`if we called the print function the Python 2-way without the parentheses. However, if we have multiple objects inside the parantheses, we will create a tuple, since`print`is a “statement” in Python 2, not a function call.

### str, bytes, encoding and decoding

> Python 2 has ASCII`str()`types, separate`unicode()`, but no`byte`type. Now, in Python 3, we finally have Unicode \(utf-8\)`str`ings, and 2 byte classes:`byte`and`bytearray`s.

Sometimes you need to convert between `bytes` and `str` (unicode string). You can use `bytes.decode()` or `str.encode()` for the conversion. Read more on the [official unicode support doc](https://docs.python.org/3.3/howto/unicode.html#python-s-unicode-support).

### Division

Python 2 interprets `/` as integer division, whereas Python 3 interprets it as decimal division. Here's the mapping:

|                         | Python 2     | Python 3 |
|-------------------------|--------------|----------|
| Floating point division | `float(a)/b` | `a / b`  |
| Integer division        | `a / b`      | `a // b` |
| Division for remainder  | `%`          | `%`      |

### Return iterable instead of list

When you read tutorials online, one frequent confusion is your code returns iterable but the sample code returns a list. You need to call `next()` on a iterable to find the next element. This is an efficiency oriented design in Python3. Given the small amount of data we are handling in this course, you can use the "brute force" way to convert valid Python2 code into Python3. The common trick is to wrap previous codes by `list()`. For example, if `a = map(...)` works in Python2, you simply write `a = list(map(...))` and that works in Python3. Having another layer of list won't harm (in terms of grammar correctness).

### Rounding to closest even number

Python 3 rounds to the closest even number. This causes little difference in most of your program.

```python
%python3
>>> round(16.5)
16
>>> round(17.5)
18
>>> round(15.5)
16

%python2
>>> round(16.5)
17.0
>>> round(17.5)
18.0
>>> round(15.5)
16.0
```

## How to set up Python 2.7 and Python 3 at the same time on your Mac OSX?

You can follow the steps in this[Link](https://stringpiggy.hpd.io/mac-osx-python3-dual-install/#step1) to set up both of them.

## Install modules in Python3

If you want to install modules for Python3, please use `pip3` (not `pip`). To install a module in user mode, you can use

```bash
pip3 install --user {name-of-the-module}
```

**NOTE**: Some online tutorials instruct you to install python module with `sudo` prefix, e.g. `sudo pip3 install pandas`. Don't do that unless other methods do not work. It is better practice to enter virtual env and run `pip install ...` (or `pip3 install`) in shell or `!pip install xxx` in notebook. In this way, the modules and other environment updates only happen within `venv`. Using `sudo xxx` is usually a quick solution but not recommended. `sudo` basically gives the followup command super user privilege which makes the system vulnerable to malicious software. One convention is to refrain from `sudo` whenever possible because -- with great power comes great responsibility -- `sudo` has too much power that is not always needed. If you are not in virtualenv, or if you want to install a module in larger scope, not only for the current project, you can use the `--user` mode as shown above. This installs the module in a sub foder under your user home directory (`echo $HOME`).