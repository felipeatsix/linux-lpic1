# Basic file management - cd, ls, file

## cd
```bash
    # Move to another directory
    cd <directory name>

    # Move one directory before
    cd ..

    # Move to previous directory
    cd -

    # Move to home of current login
    cd ~
```

## ls
```bash
    # List files
    ls

    # List files including hidden files
    ls -a

    # List files with byte size information
    ls -lh

    # List files recursively
    ls -lr

    # List files using a wildcard
    ls <string>*

    # returns a file or a directory called "felipe" if exists.
    ls fe?ipe

    # It returns folder1, folder2, folder3, if exists.
    ls folder[123]

    # It won't return folder1, folder2 and folder 3.
    ls folder[!123]

    # Same as the first one, but specifying a range.
    ls folder[1-3]

    # It will return folder called "folder" or "Folder" if exists.
    ls {F,f}older
```

## file
Show file type
```bash
    file <file name>
```