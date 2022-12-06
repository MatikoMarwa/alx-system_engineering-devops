# Expansions
- Each time we type a command line and press the enter key, bash performs several processes upon the text before it carries out our command. The process that makes this happen is called expansion. With expansion, we type something and it is expanded into something else before the shell acts upon it.

## Pathname Expansion
- The mechanism by which wildcards work is called pathname expansion.

## Tilde Expansion
- When used at the beginning of a word, it expands into the name of the home directory of the named user, or if no user is named, the home directory of the current user

## Arithmetic Expansion
- The shell allows arithmetic to be performed by expansion. This allow us to use the shell prompt as a calculator.
- Arithmetic expansion uses the form: `$((expression))` where expression is an arithmetic expression consisting of values and arithmetic operators.

## Brace Expansion
- With it, we can create multiple text strings from a pattern containing braces.
```[me@linuxbox me]$ echo Front-{A,B,C}-Back
Front-A-Back Front-B-Back Front-C-Back
```
- Patterns to be brace expanded may contain a leading portion called a preamble and a trailing portion called a postscript. The brace expression itself may contain either a comma-separated list of strings, or a range of integers or single characters. The pattern may not contain embedded whitespace. Here is an example using a range of integers:
```
[me@linuxbox me]$ echo Number_{1..5}
Number_1 Number_2 Number_3 Number_4 Number_5
```

## Parameter Expansion
- Many of its capabilities have to do with the system's ability to store small chunks of data and to give each chunk a name. Many such chunks, more properly called variables, are available for our examination. For example, the variable named “USER” contains our user name. To invoke parameter expansion and reveal the contents of USER we would do this:
```
[me@linuxbox me]$ echo $USER
me
```

## Command substitution 
- Command substitution allows us to use the output of a command as an expansion:
```
[me@linuxbox me]$ echo $(ls)
Desktop Documents ls-output.txt Music Pictures Public Templates Videos
```

## Quoting
- The shell provides a mechanism called quoting to selectively suppress unwanted expansions.

### Double Quoting
- The first type of quoting we will look at is double quotes. If we place text inside double quotes, all the special characters used by the shell lose their special meaning and are treated as ordinary characters. The exceptions are “$”, “\” (backslash), and “`” (back- quote). This means that word-splitting, pathname expansion, tilde expansion, and brace expansion are suppressed, but parameter expansion, arithmetic expansion, and command substitution are still carried out.
- emember, parameter expansion, arithmetic expansion, and command substitution still take place within double quotes:
```
[me@linuxbox me]$ echo "$USER $((2+2)) $(cal)"
me 4
February 2020
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29
```

### Single Quoting
When we need to suppress all expansions, we use single quotes.

# [Shell Arithmetic](https://www.gnu.org/software/bash/manual/html_node/Shell-Arithmetic.html)

# [Variables](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html)

# Shell Initialization Files

# [The alias Command](http://www.linfo.org/alias.html)
- Syntax is alias `name="value"`
