## How to exit Python shell if entered accidentally

Exit with a zero exit status: **`quit()`** or **Control-D** on Unix, **Control-Z** on Windows

## Invalid ASCII character problem when executing a script

Use **unicode\(\)** access to all registered Unicode codecs, then converted with **str\(\)**

## MAC's TextEdit change quotes from ASCII character to unicode character

To declare an encoding other than the default one, a special comment line should be added as the first line of the file. the syntax is as follows:

`#-*-coding: encoding -*-`

where encoding is one of the valid codes supported by Python.

For example, to declare that Windows-1252 encoding is to be used, the first line of your source code file should be:

`#-*-coding: cp-1251-*-`

One exception to the first line rule is when the source code starts with a UNIX"shebang" line. In this case, the encoding declaration should be added as the second line of the file. For example:

`#!/user/bin/env python`

`#-*-coding: cp-1251-*-`

# What is Terminal and what is shell

Terminal is a session which can receive and send input and output for command-line program.

Shell is a program which is used for controlling and running programs.

