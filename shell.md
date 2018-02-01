# Shell

## Permission denied

Sometimes a command that is not existing will induce this error.

For example, I have a variable abc = 3 and I am trying to write it to a file \(which doesn't exist and I assume python will create it on its own\), then PERMISSION DENIED will present in your shell.

## Command not found

The first hurdle is that we need to tell the shell where to find the program. If we don't put any directory indication, computer can only run executable files located in the executable search path described by the`PATH`environment variables. The current directory may not in the search path unless you put it there.







