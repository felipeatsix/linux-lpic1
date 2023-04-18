# What is shell?

Interface between the user and the operating system resources

# How the system finds and executes commands

Commands run in the command line are executables, in order for these executables to work as recognized commands by the terminal, they need to be part of locations found in the environment variable `$PATH`

If a command is not located in any of the locations in `$PATH`, the user must then reference the full path of it.

# Unzip tgz files
```bash
    tar -xf <file name>
```

# Quotting

 "" = Escape all special characters except for: $ (dollar) ` (backtick) / (slash)

 '' = Escape all special characters

 # Escaping single character

 \ = Escape the next character
 ```bash
    FELIPE=felipe
    echo $FELIPE
    echo \$FELIPE
 ```

# Environment Variables

- How to define a local environment variable

```bash
    VARIABLE_NAME=value
    echo $VARIABLE_NAME
```

- To make environment variable global, use `export` command
```bash
    export VARIABLE_NAME
```

- Print all declared variables
```bash
    set
```

- Print global variables
```bash
    env
```

- Print all directories found in $PATH variable on separated lines
> `tr` is a command that replaces one character by another
```bash
    echo $PATH | tr ':' '\n'
```

> Use command `type` with `set` and `env` and notice how "set" is a builtin command and "env" is an external command.

- How to remove environment variable
```bash
    unset VAR_NAME
```

- Some important environment variables

```bash
    HISTFFILE # Stores the file location of the history command line execution)

    HISTFILESIZE

    LOGNAME # Logged user in the current session)

    PATH # Stores external binaries locations so that they can be recognized by the command line without having to use absolute path

    PWD # Current directory

    OLDPWD # Previous directory

    SHELL # Shell type being used

    TERM # Defines the terminal type

    USER # Current user name

    DISPLAY

    PS1 # Shell prompt appearence
```
> Use `echo` to see environment variables values, e.g: echo $USER

- Dynamic variables
```bash
    $$ # Returns current process PID

    $! # Returns the last process executed in background

    #? # Returns the last process exit code

    ~ # Returns current user home

    ~<username> # Returns username's home
```

- Executing multiple commands

    Using `&&` (and) operator
    It only executes the second command when the first is successful

    Using `||` (or) operator
    It only executes the second command when the first is failed.

- Executing commands from the history output

    Using `!!` executes the last used command.
    Using `!<number>` executes the command in history by its number identifier.
    Using `!<string>` executes the last command with the passed string.

- Cleaning history
```bash
    history -c
```

- Searching for commands in history
```bash
    ctrl + R
```

- List auto completion
```bash
    Press TAB key twice
```

- Command help

Print command documentation
```bash
    man <command_name>
```
> For Built-in commands, use man bash

Find commands using a keyword or phrase found in their short description
```bash
    man -k <keyword || phrase>
```

Find commands using a keyword or phrase found in their short AND long descriptions
```bash
    apropos <keyword || phrase>
```

Returns the description of a given command
```bash
    whatis cp
```

Return system information
```bash
    uname
```

Creating aliases
```bash
    alias lt='ls /tmp'
```

List all defined aliases
```bash
    alias
```

Return file location of items found in the PATH variable
```bash
    which echo
```

# Text file commands

Return text file content
```bash
    cat <file name>

    # Returns content with numbered lines
    cat -n <file name>

    # Does not enumerate blank lines
    cat -b <file name>

    # Merge multiple blank lines into only one blank line
    cat -s <file name>

    # Shows hidden characters (tab, end of lines, etc...)
    cat -A <file name>
```
> The command "nl" does the same thing as "cat -b"

Return text file content in inverse order
```bash
    tac <file name>
```
> Note how "tac" is "cat" in inverse way

Returns a portion of the file content
```bash
    head <file name>

    # Returns only two first lines
    head -2 <file name>
```
> By default it returns first 10 lines

Returns a portion of the file in the inverse order
```bash
    tail <file name>

    # Return the last lines and keep watching it
    tail -f <file name>
```
> tail -f is a useful command for live logging

Returns paginated content
```bash
    less <file name>
```

While you're navigating through the document you have some navigation options
```bash
    # Type "/ <keyword>" to search for keyword in the text file
    # Type "n" for next keyword ocurrence
    # Type "N" (capital) for previous keyword ocurrence
    # Type "spacebar" to jump to next page
    # "Ctrl + G" shows the file status and details
    # Type "q" to exit
```

Read the quantity of lines
```bash
    wc <file name>
    # returns in number = [lines] [words] [characters]
```

Optionally you can return only lines or words or characters
```bash
    wc -l # Only lines
    wc -w # Only words
    wc -c # Only characters
```

Sorting files
```bash
    sort <file name> # Sort file alphabetically
    sort -k2 <file name> # Sort by the second field(e.g: last name)
    sort -t ':' -k 2 # Sort by the second field when delimiter is ':'
    sort -t ':' -k 2n # Sort by the second field when delimiter is ':' and numeric

```

Returns non duplicated lines from a file
```bash
    cat <file name> | uniq
```

Returns only what's duplicated in the file
```bash
    cat <file name> | uniq -d
```

Enumerates how many ocurrences the same line content has in the file
```bash
    cat <file name> | uniq -c
```

Returns content in octal dump format
```bash
    od <file name>
```

Combine two files using an index
```bash
    # Consider the files content

    ## Names ##
    # 1 Felipe
    # 2 Cicely

    ## Height ##
    # 1 1,75
    # 2 1,63

    join <names.txt> <height.txt>

    # output
    # 1 Felipe 1,75
    # 2 Cicely 1,63
```

Combine two files lines
```bash
    paste <file name>
```

Divide a file into more files
```bash
    split -l20 <file name> <new file name> # Creates new files by each 20 lines
```

Replace or delete characters using `tr` command
```bash
    cat <file name> | tr a-z A-Z # make all upper case Using letter range
    cat <file name> | tr [:upper:] [:lowercase] # Same as above
    cat <file name> | tr A E # Replace A by E
    cat <file name> | tr -d A # Delete all upper case A characters
    cat <file name> | tr -d [:blank:] # Delete all blank spaces
    echo "feliiiipe" | tr -s i # Squeeze character "i", e.g: returns "Felipe"
    cat <file name> | tr ei EI # Every e character will be replace by upper case "E" and every i character will be replaced by upper case "I".
```

Converting line termination from Windows (CRLF) to Unix (LF) using `tr` command
```bash
    tr -d "\r" < filename.txt > newfile.txt
    #or
    cat filename | tr -d "\r" > newfile.txt
```

Cut portions of text using the `cut` command
```bash
    cut -c1-5 <file name> # Returns the first 5 characters of each line
    cut -c-5 <file name> # Do the same as above.
    cut -c5- <file name> # Returns characters starting from index 5 of each line
    cut -c1,2,5 <file name> # Returns index 1, 2 and 5 of each line
    cut -d" " -f1 <file name> # Set delimiter as "blank space" and return "field 1" of each line
```

Using `sed` command for editing text
```bash
    sed 's/oldName/newName/' <file name> # Replaces every first ocurrence of 'oldName' in each line

    sed 's/oldName/newName/g' <file name> # Using /g tells the command to change all ocurrences of 'oldName' on each line.

    sed '3,5 d' <file name> # Deletes lines from 3 to line 5

    sed '/name/d' <file name> # Deletes the whole line that contains the word 'name'
```

Reading compressed files with variantes of the `cat` command

```bash
    xzcat file.txt.xz
    bzcat file.txt.bz2
    zcat file.txt.gz
```

How to verify file integrity (checksum)
```bash
    # <Filename> can be a .txt file that must contain a relation of hash and file name which coincides with the filename being verified that must exist on same folder of the operation.
    md5sum -c <filename>
    sha256sum -c <filename>
    sha512sum -c <filename>
```


# Basic file management - cd, ls, file

## Command cd

Move to another directory
```bash
    cd <directory name>
```

Move one directory before
```bash
    cd ..
```

Move to previous directory
```bash
    cd -
```

Move to home of current login
```bash
    cd ~
```

## Command ls

List files
```bash
    ls
```

List files including hidden files
```bash
    ls -a
```

List files with byte size information
```bash
    ls -lh
```

List files recursively
```bash
    ls -lr
```

List files using a wildcard
```bash
    ls <string>*
```

List files using interrogation mark to replace any character on search
```bash
    ls fe?ipe # returns a file or a directory called "felipe" if exists.
```

List files using a character list
```bash
    ls folder[123] # It returns folder1, folder2, folder3, if exists.
    ls folder[!123] # It won't return folder1, folder2 and folder 3.
    ls folder[1-3] # Same as the first one, but specifying a range.
```

List files using string matching
```bash
    ls {F,f}older # It will return folder called "folder" or "Folder" if exists.
```

## Command file

Show file type
```bash
    file <file name>
```