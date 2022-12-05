### Shell I/0 Redirection

Input/Output redirections use some special notations to redirect the output of many commands to files, devices, and even to the input of other commands.

#### Standard Output
Most command lines use the standard output to display their results. In it's default state the standard output directs results to display. We can redirect standard output to a file using `>` character.

`[me@linuxbox me]$ ls > file_list.txt`
The above code executes the `ls` command and records the results in the file named `file_list.txt`. If this command is used again the results in the `file_list.txt` will be overwritten. To append results at the end of the file we use `>>` character.
Both of these charcaters will not display the results.
If the file does not exist when we attempt to append the redirected output, the file will be created.

#### Standard Input
By default, standard input gets its contents from the keyboard, but like standard output, it can be redirected.
We use `<` to redirect standard input from a file instead of using the keyboard.

`[me@linuxbox me]$ sort < file_list.txt`
Here we use the `sort` command to process the contents of `file_list.txt`.
The results will be output on display since there is no redirection to standard output.
We could redirect to standard output like this

`[me@linuxbox me]$ sort < file_list.txt > sorted_file_list.txt`

**NB** We can redirect both input and output at the same time. The order does not matter but the characters `<` `>` must appear after the other options and arguments in the command.

#### Pipelines
Multiple commands that are connected together are called pipelines.
With pipelines, the standard output of one command is fed into the standard input of another.

**eg**
`[me@linuxbox me]$ ls -l | less`
In this example, the output of the `ls` command is fed into `less`. By using this `| less` trick, we can make any command have scrolling output.

Other examples
| **Command** | **Function** |
| ----------- | ----------- |
| `ls-lt `|` `head` | Displays the 10 newest files in the current directory. |
| `du `|` `sort-nr` | Displays a list of directories and how much space they consume, sorted from the largest to the smallest. |
| `find . -type f -print `|` `wc -l` | Displays the total number of files in the current working directory and all of its subdirectories. |

#### Filters
This the most frequently used program in pipelines. Filters take standard input and process it and then sends the results to standard output.
Common programs that double as filters.

| **Command** | **Function** |
| ----------- | ----------- |
| `head` | Outputs the first few lines of its input. Useful for getting the header of a file. |
| `tail` | Outputs the last few lines of its input. Useful for things like getting the most recent entries from a log file. |
| `find` | Search for files in a directory hierarchy |
| `wc` | Prints newline, word, and byte counts for each file |
| `sort` | Sorts standard input then outputs the sorted result on standard output. |
| `uniq` | Given a sorted stream of data from standard input, it removes duplicate lines of data (i.e., it makes sure that every line is unique). |
| `grep` | Examines each line of data it receives from standard input and outputs every line that contains a specified pattern of characters. |
| `tr` | Translates characters. Can be used to perform tasks such as upper/lowercase conversions or changing line termination characters from one type to another (for example, converting DOS text files into Unix style text files). |
| `echo` | Outputs the strings that are passed to it as arguments |
| `cat` | Prints the content of a file onto the standard output stream. |
| `rev` | Is used to reverse the lines characterwise |
| `cut` |  A command-line utility that allows you to cut out sections of a specified file or piped data and print the result to standard output. |
| `passwd (5)` | Is used to change the user account passwords. |

#### What is the `/etc/passwd` file and what is its format
Traditionally, the /etc/passwd file is used to keep track of every registered user that has access to a system.

The /etc/passwd file is a colon-separated file that contains the following information:
 
 - Username: Is used when user logs in. It should be between 1 to 32 characters in length.
 - Encrypted password: An x character indicates that encrypted password is stored in `/etc/shadow` file. Please note that you need to use the `passwd` command to computes the hash of a password typed at the CLI or to store/update the hash of the password in `/etc/shadow` file.
 - User ID number (UID): Each user must be assigned a user ID (UID). UID 0 (zero) is reserved for root and UIDs 1-99 are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups.
 - User's group ID number (GID): The primary group ID (stored in /etc/group file)
 - Full name of the user (GECOS): The comment field. It allow you to add extra information about the users such as user’s full name, phone number etc. This field use by finger command.
 - User home directory: The absolute path to the directory the user will be in when they log in. If this directory does not exists then users directory becomes `/`
 - Login shell: The absolute path of a command or shell (`/bin/bash`). Typically, this is a shell. Please note that it does not have to be a shell.

![Format for `/etc/passwd`](https://www.cyberciti.biz/media/ssb.images/uploaded_images/passwd-file-791527.png)

```
root:!:0:0::/:/usr/bin/ksh
daemon:!:1:1::/etc:
bin:!:2:2::/bin:
sys:!:3:3::/usr/sys: 
adm:!:4:4::/var/adm:
uucp:!:5:5::/usr/lib/uucp: 
guest:!:100:100::/home/guest:
nobody:!:4294967294:4294967294::/:
lpd:!:9:4294967294::/:
lp:*:11:11::/var/spool/lp:/bin/false 
invscout:*:200:1::/var/adm/invscout:/usr/bin/ksh
nuucp:*:6:5:uucp login user:/var/spool/uucppublic:/usr/sbin/uucp/uucico
paul:!:201:1::/home/paul:/usr/bin/ksh
jdoe:*:202:1:John Doe:/home/jdoe:/usr/bin/ksh 
```
#### What is the `/etc/shadow` file and what is its format
Is a text-based password file.

The `/etc/shadow` file stores secure user account information. All fields are separated by a colon (`:`) symbol. It contains one entry per line for each user listed in `/etc/passwd file`.

![Format Image](https://www.cyberciti.biz/faqs/uploaded_images/shadow-file-718705.png)

The `/etc/shadow` contains the following informations.

 - Username : A valid account name, which exist on the system.
 - Password : Your encrypted password is in hash format. The password should be minimum 15-20 characters long including special characters, digits, lower case alphabetic and more. Usually password format is set to `$id$salt$hashed`, The `$id` is the algorithm used On GNU/Linux as follows:
  - `$1$` is MD5
  - `$2a$` is Blowfish
  - `$2y$` is Blowfish
  - `$5$` is SHA-256
  - `$6$` is SHA-512
 - Last password change (lastchanged) : The date of the last password change, expressed as the number of days since Jan 1, 1970 (Unix time). The value `0` has a special meaning, which is that the user should change her password the next time she will log in the system. An empty field means that password aging features are disabled.
 - Minimum : The minimum number of days required between password changes i.e. the number of days left before the user is allowed to change her password again. An empty field and value 0 mean that there are no minimum password age.
 - Maximum : The maximum number of days the password is valid, after that user is forced to change her password again.
 - Warn : The number of days before password is to expire that user is warned that his/her password must be changed
 - Inactive : The number of days after password expires that account is disabled.
 - Expire : The date of expiration of the account, expressed as the number of days since Jan 1, 1970.

### Special Characters
Some characters are evaluated by Bash to have a non-literal meaning. Instead, these characters carry out a special instruction, or have an alternate meaning; they are called "special characters", or "meta-characters".

#### Description

| **Special Character** | **How it works** |
| ----------- | ----------- |
| `" "` | Whitespace — this is a tab, newline, vertical tab, form feed, carriage return, or space. Bash uses whitespace to determine where words begin and end. The first word is the command name and additional words become arguments to that command. |
| `$` | Expansion — introduces various types of expansion: parameter expansion (e.g. $var or ${var}), command substitution (e.g. $(command)), or arithmetic expansion (e.g. $((expression))). More on expansions later. |
| `''` | Single quotes — protect the text inside them so that it has a literal meaning. With them, generally any kind of interpretation by Bash is ignored: special characters are passed over and multiple words are prevented from being split. |
| `""` | Double quotes — protect the text inside them from being split into multiple words or arguments, yet allow substitutions to occur; the meaning of most other special characters is usually prevented. |
| `\` | Escape — (backslash) prevents the next character from being interpreted as a special character. This works outside of quoting, inside double quotes, and generally ignored in single quotes. |
| `#` | Comment — the # character begins a commentary that extends to the end of the line. Comments are notes of explanation and are not processed by the shell. |
| `=` | Assignment -- assign a value to a variable (e.g. logdir=/var/log/myprog). Whitespace is not allowed on either side of the = character.|
| `[[ ]]` | Test — an evaluation of a conditional expression to determine whether it is "true" or "false". Tests are used in Bash to compare strings, check the existence of a file, etc. More of this will be covered later. |
| `!` | Negate — used to negate or reverse a test or exit status. For example: ! grep text file; exit $?. |
| `>`, `>>`, `<` | Redirection — redirect a command's output or input to a file. Redirections will be covered later. |
| `|` | Pipe — send the output from one command to the input of another command. This is a method of chaining commands together. Example: echo "Hello beautiful." | grep -o beautiful. |
| `;` | Command separator — used to separate multiple commands that are on the same line. |
| `{ }` | Inline group — commands inside the curly braces are treated as if they were one command. It is convenient to use these when Bash syntax requires only one command and a function doesn't feel warranted. |
| `( )` | Subshell group — similar to the above but where commands within are executed in a subshell (a new process). Used much like a sandbox, if a command causes side effects (like changing variables), it will have no effect on the current shell. |
| `(( ))` | Arithmetic expression — with an arithmetic expression, characters such as `+`, `-`, `*`, and `/` are mathematical operators used for calculations. They can be used for variable assignments like (( a = 1 + 4 )) as well as tests like if (( a < b )). More on this later. |
| `$(( ))` | Arithmetic expansion — Comparable to the above, but the expression is replaced with the result of its arithmetic evaluation. Example: echo "The average is $(( (a+b)/2 ))". |
| `*`, `?` | Globs -- "wildcard" characters which match parts of filenames (e.g. ls `*.txt`). |
| `~` | Home directory — the tilde is a representation of a home directory. When alone or followed by a `/`, it means the current user's home directory; otherwise, a username must be specified (e.g. `ls ~/Documents`; `cp ~john/.bashrc .`). |
| `&` | Background -- when used at the end of a command, run the command in the background (do not wait for it to complete). |
