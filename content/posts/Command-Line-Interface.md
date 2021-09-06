---
title: "Command Line Interface"
date: 2021-09-05T23:20:52+01:00
draft: true
---

Here are a few resources and cheat sheets for the Apple Terminal:

[0nn0/terminal-mac-cheatsheet/README.markdown](https://github.com/0nn0/terminal-mac-cheatsheet)

Create directory: `mkdir`

```bash
# Example:
mkdir a_test_folder
```

Navigate to directory: `cd`

```bash
# Example anywhere:
cd /Users/USERNAME/FOLDER/FOLDER/
# Example within folder:
cd [folder]
```

Full path to working directory: `pwd`

```bash
# Example:
pwd .
```

Short listing: `ls`

```bash
# Example:
ls .
```

Home directory: `~`

```bash
# Example:
cd ~
```

Previous directory: `-`

```bash
# Example:
cd -
```

Current folder: `.`

```bash
# Example:
ls .
```

Parent/enclosing directory: `..` 

```bash
# Example:
ls ..
```

Move up 2 levels:

```bash
cd ../../
```

Create new file: `touch`

```bash
# Example:
touch an_algorithm.py
```

Remove file: `rm`

```bash
rm an_algorithm.py
```

Rename folder: `mv`

> Condition: If [newname] is not a folder or it's empty

```bash
mv [oldname] [newname]
```


Move folder: mv [oldname] [newname]

this will rename [oldname] to [newname], if [newname] doesn't exist
this will move [oldname] into [newname], if [newname] exists (/home/user/newname/oldname)

Remove a directory and contents: rm -r [dir]

Clear terminal window (move up): clear (moves the content one page up but still same terminal instance)

Clear terminal window (empty): reset

In contrast to clear, or Ctrl+L, reset will actually completely re-initialise the terminal, instead of just clearing the screen. However, it won't re-instantiate the shell (bash). That means that bash's state is the same as before, just as if you were merely clearing the screen.

Source: StackExchange

Show head of file: head [file].[extension]