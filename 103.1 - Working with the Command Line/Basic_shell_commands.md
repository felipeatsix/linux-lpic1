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



# Demonstration

`echo $SHELL`
This command shows what shell type it is being used.

`type echo`
It tells if "echo" is a built-in or external (to bash). When type is "hashed" it means it is external and it is cached in memory for being used often.