# Shell

<!-- TOC -->

- [Shell](#shell)
    - [Permission denied](#permission-denied)
    - [Command not found](#command-not-found)
    - [Difference between Terminal and Shell](#difference-between-terminal-and-shell)
    - [Different shell commands in Win and Mac](#different-shell-commands-in-win-and-mac)
    - [Verify your current working folder](#verify-your-current-working-folder)

<!-- /TOC -->

## Permission denied

Sometimes a command that is not existing will induce this error.

For example, I have a variable abc = 3 and I am trying to write it to a file \(which doesn't exist and I assume python will create it on its own\), then PERMISSION DENIED will present in your shell.

## Command not found

The first hurdle is that we need to tell the shell where to find the program. If we don't put any directory indication, computer can only run executable files located in the executable search path described by the `PATH` environment variables. The current directory may not in the search path unless you put it there.

## Difference between Terminal and Shell

Terminal is the (graphical) "window" you can see on your computer. It is the bridge between the user and shell. Shell is the tool that gets input from user (via Terminal), executes programs and sends output to the Terminal (for user consumption). Shell itself is a program and is usually shipped with the operating system by default, especially in the [UNIX-like](https://en.wikipedia.org/wiki/Unix-like) families (including MAX OS X).

## Different shell commands in Win and Mac

please see [here](https://carolhsu.gitbooks.io/django-girls-tutorial-traditional-chiness/content/intro_to_command_line/README.html)

## Verify your current working folder

Most of the path related errors are caused by wrong current working folder. One need to run the following two commands before starting other commands to verify the current working folder:

- `pwd` -- prints the working directory. You can check the path name.
- `ls` -- list directory. This shows the files in the current directory for your double check.