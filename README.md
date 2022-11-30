### General
RTFM Stands for read the f**kng manual
A shebang is the character sequence consisting of the characters number sign and exclamation mark (#!) at the beginning of a script.

#### What is the shell
Shell is a program that takes commands from the keyboard and gives them to the operating system to perform.

#### Difference between the shell and the terminal
Shell is a program that takes commands from the keyboard and gives them to the OS to perform while a terminal is a program that opens a window to let you interact with shell

#### What is shell prompt
The shell prompt is where one types in commands.

---

### Navigation
- *cd* is used to change directory
- *pwd* writes the full pathname of the current working directory to the standard output.
- *ls* is used to list computer files and directories

---

### Looking Around
- *ls* is used to list computer files and directories
- *less* is used to show a file contents one page at a time
- *file* is used to determine the type of a file
[A Guided Tour](http://linuxcommand.org/lc3_lts0040.php)

---

### Manipulating Files
- *cp* **is used to copy files and directories
- *mv* is used to move or rename files and directories depending on how it has been used
- *rm* is used to delete files or directorie. rm -r deletes directories with its contents.
- *mkdir* this command is used to create directories and folders

---

### Working with Commands

- *type* **this command displays information about command type
- *which* is used to locate a command
- *help* is used to display reference page for shell builtin
- *man* is used to display an on-line command reference

#### Different kind of commands
**Commands are divided into 4;
- An executable program
- A command built into the shell itself
- A shell function
- An alias 

#### alias
**Alias are commands that we define ourselves, built from other commands.

#### When to use man instead of help
**We use **help** for shell built ins while we use **man** for executable programs

### Keyboard Shorcuts for Bash
- Ctrl+C interrupts or kills the current foreground process running in the terminal
- Ctrl+z suspends the current foreground process running in bash.
- Ctrl+D Close the bash shell
- Ctrl+L Clears the screen
- Ctrl+S Stops all output to the screen
- Ctrl+Q Resume output to the screen after stopping it with Ctrl+S
- Ctrl+A or Home: Go to the beginning of the line.
- Ctrl+E or End: Go to the end of the line.
- Alt+B: Go left (back) one word.
- Ctrl+B: Go left (back) one character.
- Alt+F: Go right (forward) one word.
- Ctrl+F: Go right (forward) one character.
- Ctrl+XX: Move between the beginning of the line and the current position of the cursor.
- Ctrl+D or Delete: Delete the character under the cursor.
- Alt+D: Delete all characters after the cursor on the current line.
- Ctrl+H or Backspace: Delete the character before the cursor.
- Alt+T: Swap the current word with the previous word.
- Ctrl+T: Swap the last two characters before the cursor with each other.
- Ctrl+_ **Undo your last key press. You can repeat this to undo multiple times.
- Ctrl+W: Cut the word before the cursor, adding it to the clipboard.
- Ctrl+K: Cut the part of the line after the cursor, adding it to the clipboard.
- Ctrl+U: Cut the part of the line before the cursor, adding it to the clipboard.
- Ctrl+Y: Paste the last thing you cut from the clipboard. The y here stands for “yank”.
- Alt+U: Capitalize every character from the cursor to the end of the current word, converting the characters to upper case.
- Alt+L: Uncapitalize every character from the cursor to the end of the current word, converting the characters to lower case.
- Alt+C: Capitalize the character under the cursor. Your cursor will move to the end of the current word.
- Tab: Automatically complete the file, directory, or command you’re typing.
- Ctrl+P or Up Arrow: Go to the previous command in the command history.
- Ctrl+N or Down Arrow: Go to the next command in the command history.
- Alt+R: Revert any changes to a command you’ve pulled from your history if you’ve edited it.
- Ctrl+R: Recall the last command matching the characters you provide. Press this shortcut and start typing to search your bash history for a command.
- Ctrl+O: Run a command you found with Ctrl+R.
- Ctrl+G: Leave history searching mode without running a command.

**LTS** stands for Long Term Support.
