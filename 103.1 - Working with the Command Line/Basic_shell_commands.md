# What is shell?

Interface between the user and the operating system resources

# How the system finds and executes commands

Commands run in the command line are executables, in order for these executables to work as recognized commands by the terminal, they need to be part of locations found in the environment variable `$PATH`

If a command is not located in any of the locations in `$PATH`, the user must then reference the full path of it.

# Basic commands

- date
- echo
- type
- cat
- exit
- unset

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

> NOTE:
    Use command `type` with `set` and `env` and notice how "set" is a builtin command and "env" is an external command.

- How to remove environment variable
```bash
    unset VAR_NAME
```

- Some important environment variables

```
    HISTFFILE = Stores the file location of the history command line execution.

    LOGNAME = Logged user in the current session.

    PATH = Stores external binaries locations so that they can be recognized by the command line without having to use absolute path.

    PWD = Current directory

    SHELL = Shell type being used

    TERM = Defines the terminal type

    USER = Current user name
```
> Note
    Use `echo` to see environment variables values, e.g: echo $USER

- Dynamic variables
```
    $$ = Returns current process PID

    $! = Returns the last process executed in background

    #? = Returns the last process exit code
```