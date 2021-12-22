---
title: "🤷‍♂️ CLI (noob notes)"
date: 2021-05-22T12:00:00+01:00
draft: true
showtoc: true
tags: ["noob notes", "Terminal", "CLI"]
---

## About

There are a few commands I end up googling over and over again. Instead of looking up the same stackoverflow question, I decided to keep a record of commands I find helfpul.

## Cheat Sheet

I borrowed a few commands from [0nn0/terminal-mac-cheatsheet/README.markdown](https://github.com/0nn0/terminal-mac-cheatsheet)


### Create directory: `mkdir`

```bash
# Example:
mkdir a_test_folder
```

### Navigate to directory: `cd`

```bash
# Example anywhere:
cd /Users/USERNAME/FOLDER/FOLDER/
# Example within folder:
cd [folder]
```

### Full path to working directory: `pwd`

```bash
# Example:
pwd .
```

### Short listing: `ls`

```bash
# Example:
ls .
```

### Home directory: `~`

```bash
# Example:
cd ~
```

### Previous directory: `-`

```bash
# Example:
cd -
```

### Current folder: `.`

```bash
# Example:
ls .
```

### Parent directory: `..`

```bash
# Example:
ls ..
```

### Move up 2 levels

```bash
cd ../../
```

### Create new file: `touch`

```bash
# Example:
touch an_algorithm.py
```

### Remove file: `rm`

```bash
rm an_algorithm.py
```

### Rename folder: `mv`

```bash
mv old_name new_name
```

Only if `new_name` **is not** already a folder.

### Move folder: `mv`

```bash
mv old_location new_location
# mv home/user/desktop/folderA home/user/documents/github/folderX
```

Only if `new_location` **is** already a folder.

### Delete a directory and its contents: `rm -r [dir]`

### Show head of a file: `head [file].[extension]`