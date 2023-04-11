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

Sort file alphabetically
```bash
    sort <file name>
```

Sort by the second field(e.g: last name)
```bash
    sort -k2 <file name>
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

    ## File 1 ##
    # 1 Felipe
    # 2 Cicely

    ## File 2 ##
    # 1 1,75
    # 2 1,63

    join <names.txt> <height.txt>

    # output
    # 1 Felipe 1,75
    # 2 Cicely 1,63
```