# bash quick reference

ctrl-l  clear console

## shell command structure
A simple shell command such as echo a b c consists of the command itself followed by arguments, separated by spaces.

More complex shell commands are composed of simple commands arranged together in a variety of ways: 
- in a pipeline in which the output of one command becomes the input of a second
- in a loop or conditional construct
- in some other grouping 

| command | definition |
| --- | --- |
| pwd | print working directory |
| cd     | change working directory |
| cd /   | change directory to root |
| mkdir  | create a new directory, with current directory as parent directory ie mkdir directoryname |
| ls     | print list of files and subdirectories |
| rm     | delete a specific file ie rm filename |
| rm -r  | delete a directory and all subdirectories it contains ie rm -r directoryname |
| -r     | recurse command through a ist of all files and subdirectories within parent directory |
| cp     | copy a specific file to a new directory ie cp filename directoryname |
| cp -r  | copy a directory and its contents ie cp -r directorynametocopy directorynamedestination |
| touch  | create a new empty file ie touch filename.txt |
| g++    | compile .c or .cpp files but they will be treated as c++ files only |
| gcc    | compile any .c or .cpp files but they will be treated as C and C++ respectively |
| -p     | changes the output format to that specified by POSIX |
| time   | causes timing statistics to be printed for the pipeline when it finishes |

control operator
A token that performs a control function. It is a newline or one of the following: 
‘||’, ‘&&’, ‘&’, ‘;’, ‘;;’, ‘;&’, ‘;;&’, ‘|’, ‘|&’, ‘(’, or ‘)’.

## pipelines
A pipeline is a sequence of one or more commands separated by one of the control operators ‘|’ or ‘|&’.
The format for a pipeline is:
```
    [time [-p]] [!] command1 [ | or |& command2 ] …
```
The output of each command in the pipeline is connected to the input of the next command.
If ‘|&’ is used, command1's standard error in addition to its standard output is connected to command2's standard input through the pipe.

A list is a sequence of one or more pipelines separated by one of the operators ; & && or || , and optionally terminated by one of : & or a newline.

- AND list command1 && command2 executed if and only if command1 returns zero (true/success)
- OR list  command1 || command2 executed if and only if command1 returns non-zero exit status

## compound commands
Compound commands are the shell programming language constructs. Each begins with a reserved word or control operator and is terminated by a corresponding reserved word or operator.

| Looping Constructs: | |
| --------------------|---|
   | until |  until test-commands; do consequent-commands; done |
   | while | while test-commands; do consequent-commands; done |
   | for   |  for name [ [in [words …] ] ; ] do commands; done |
   
   ```
            for (( expr1 ; expr2 ; expr3 )) ; do commands ; done
```
Break and continue may be used to control loop execution.

Conditional Constructs:
```
    if      if test-commands; then
                consequent-commands;
            [elif more-test-commands; then
                more-consequents;]
            [else alternate-consequents;]
                fi
    case    case word in
                [ [(] pattern [| pattern]…) command-list ;;]…
            esac
```
### metacharacter
A character that, when unquoted, separates words. A space, tab, newline, or one of the following characters: 
‘|’, ‘&’, ‘;’, ‘(’, ‘)’, ‘<’, or ‘>’.

### escape character
A non-quoted backslash ‘\’ is the Bash escape character. Words of the for $'string' are treated specially. Backslash escape sequences are decoded as follows:

| | |
| -- | -- |
| \a | alert (bell) |
| \b | backspace |
| \e | |
| \E | an escape character (not ANSI C) |
| \f | form feed |
| \n | newline |
| \r | carriage return |
| \t | horizontal tab |
| \v | vertical tab |
| \\ | backslash |
| \' | single quote |
| \" | double quote |
| \? | question mark |
| \nnn |   the eight-bit character whose value is the octal value nnn (one to three octal digits) |
| \xHH |   the eight-bit character whose value is the hex value HH (one or two hex digits) |
| \uHHHH | the Unicode (ISO/IEC 10646) character whose value is the hex value HHHH (one to four hex digits) |
| \UHHHHHHHH | the Unicode (ISO/IEC 10646) character whose value is the hex value HHHHHHHH (one to eight hex digits) |
| \cx | a control-x character |

The expanded result is single-quoted, as if the dollar sign had not been present.

# sources
https://www.gnu.org/software/bash/manual/bash.html (left off at 3.2.5.2)
