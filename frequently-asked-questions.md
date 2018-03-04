## How to exit Python shell if entered accidentally

Exit with a zero exit status: `quit()` or **Control-D** on Unix, **Control-Z** on Windows

## Invalid ASCII character problem when executing a script

Use **unicode\(\)** access to all registered Unicode codecs, then converted with **str\(\)**

## MAC's TextEdit change quotes from ASCII character to unicode character \(smart quotes\)

It is suggested to disable system wide smart quotes and smart dashes function. Read more [here](https://support.apple.com/kb/PH25635?viewlocale=en_GB&locale=en_GB).![](/assets/Screen Shot 2018-01-25 at 10.00.11 PM.png)

![](/assets/Screen Shot 2018-01-24 at 6.57.18 PM.png)

## Declare file encoding other than the default

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

# With or without ".py" extension name?

Without the extension name, Visual Studio Code can not highlight the code:![](/assets/no py..jpeg)After adding to the extension name, the interface become normal:![](/assets/with py..jpeg)

# Check modules before enter PYVENV VENV

PYVENV means setting up a new VENV environment, and it probably erases some modules you installed previously.

So, if you have already entered ‘pyvenv venv’ before and deactivate, next time you use the same computer, you could enter ‘source venv/bin/activate’ to get into VENV environment, and ‘deactivate’ to exit VENV environment.

In the lab, you probably will change the seat and computer, before you enter the ‘VENV’ and use the Jupyter, you could check in the terminal to check whether the module is on the computer:

![](/assets/1.png)

and to check this module again:

![](/assets/2.png)

It means you successfully installed this module.
This situation is same to those modules: ‘requests’, ‘bs4’, etc.

# I already install some module before executing the Jupyter, why is this happen?

![](/assets/3.png)

Maybe you enter ’pyvenv venv’ again before you enter ‘jupyter notebook’, try to enter the ‘venv’ environment by typing ‘source venv/bin/activate’.

If it does not work, you could set up the ‘venv’ environment again by typing ’pyvenv venv’. Then install all the modules you will use before enter the ‘jupyter notebook’. Once you finish your work, use ‘deactivate’ to exit ‘venv’ environment. Do remember that you should use ‘source venv/bin/activate’ next time, not ‘pyvenv venv’.

