---
title: "🤓 Python (noob notes)"
date: 2021-12-21T12:00:00+01:00
draft: true
showtoc: true
tags: ["python"]
---

### Strings

#### [`ord(c)`](https://docs.python.org/3/library/functions.html#ord) and [`chr(i)`](https://docs.python.org/3/library/functions.html#chr)

```py
>>> ord('a')
97
>>> chr(97)
'a'
```

`ord(c)`: Given a string representing one **Unicode** character, return an integer representing the Unicode code point of that character. For example, ord('a') returns the integer 97 and ord('€') (Euro sign) returns 8364. This is the inverse of chr().

`chr(i)`: Return the string representing a character whose Unicode code point is the integer i. For example, chr(97) returns the string 'a', while chr(8364) returns the string '€'. This is the inverse of ord().

[List of Unicode characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters#Basic_Latin) (wikipedia):

| Code | Glyph | Decimal  | Octal | Description | # |
|--------|---|-----|------|----------------------|------|
| U+0061 | a | 97  | 0141 | Latin Small Letter A | 0066 |
| U+0062 | b | 98  | 0142 | Latin Small Letter B | 0067 |
| U+0063 | c | 99  | 0143 | Latin Small Letter C | 0068 |
| ... | ...| ... | ... | ... | ... |
| U+007A | z | 122 | 0172 | Latin Small Letter Z | 0091 |




### Sets

The `difference_update()` method removes the items that exist in both sets.

The `difference_update()` method is different from the `difference()` method, because the `difference()` method returns a new set, without the unwanted items, and the `difference_update()` method removes the unwanted items from the original set.

```py
# difference = new set (return type = set)
new = x.difference(s)
# difference_update = update set (return type = None)
x.difference_update(s)
```

Source: [W3School](https://www.w3schools.com/python/ref_set_difference_update.asp)
    
The `update()` method updates the current set, by adding **items** from another set (or any other iterable).

The `add()` method adds an **element** to the set.

```py
# update = same set (return type = None)
x.update(s)
# add = same set (return type = None)
x.add("a")
```

Source: [W3School](https://www.w3schools.com/python/ref_set_update.asp)

### Dictionaries

`d.items()` and `ErrorValue: too many values to unpack (expected 2)`

Source: [Career Karma](https://careerkarma.com/blog/python-valueerror-too-many-values-to-unpack-expected-2/)

### Exceptions (errors)

#### Exception types

**[`exception TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError)**
Raised when an operation or function is applied to an object of **inappropriate type**.

Passing arguments of the wrong type (e.g. passing a list when an int is expected) should result in a `TypeError`, but passing arguments with the wrong value (e.g. a number outside expected boundaries) should result in a `ValueError`.

**[`exception ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError)**: Raised when an operation or function receives an argument that has the right type but an **inappropriate value**, and the situation is not described by a more precise exception such as `IndexError`.

**[`exception IndexError`](https://docs.python.org/3/library/exceptions.html#IndexError)**: Raised when a sequence subscript is **out of range**. (Slice indices are silently truncated to fall in the allowed range; if an index is not an integer, TypeError is raised.)

#### Handling exceptions

```py
while True:
    try:
        x = int(input("Please enter a number: "))
        break
    except ValueError:
        print("Oops!  That was no valid number.  Try again...")
```

The `try` statement works as follows.

* First, the `try` clause (the statement(s) between the `try` and `except` keywords) is executed.
* If no exception occurs, the except clause is skipped and execution of the `try` statement is finished.
* If an exception occurs during execution of the `try` clause, the rest of the clause is skipped. Then, if its type matches the exception named after the `except` keyword, the except clause is executed, and then execution continues after the try/except block.
* If an exception occurs which does not match the exception named in the `except` clause, it is passed on to outer `try` statements; if no handler is found, it is an unhandled exception and execution stops with a message as shown above.

*Source: [8.3. Handling Exceptions](https://docs.python.org/3/tutorial/errors.html#handling-exceptions)*

#### Raising exceptions

The `raise` statement allows the programmer to force a specified exception to occur.

```py
raise NameError('HiThere')
```


### pytest (testing)

To run a specific test within a module:

```bash
$ pytest test_mod.py::test_func
```

*Source: [How to invoke pytest in command line](https://docs.pytest.org/en/latest/how-to/usage.html#how-to-invoke-pytest)*

#### Assertions about objects (e.g. correct instantion)

```py
# foo.py
class MyClass:
    def __init__(self, public_attr_1, public_attr_2):
        self.public_attr_1 = public_attr_1
        self.public_attr_2 = public_attr_2
```

```py
# test_foo.py
import pytest
from foo import MyClass
 
def test_initial_value():
    obj_1 = MyClass(1, 2)     
    assert obj_1.public_attr_1 == 1
    assert obj_1.public_attr_2 == 2
 
def test_no_value():
    with pytest.raises(Exception) as e_info:
        obj = MyClass()   
```

*Source: [Python-forum.io](https://python-forum.io/thread-5727-post-28324.html#pid28324)*

#### Assertions about exceptions

In order to write assertions about raised exceptions, you can use `pytest.raises()`.

```py
# Module example
import pytest

def myfunc():
    raise ValueError("Exception 123 raised")
```

```py
# Test example
def test_myfunc():
    with pytest.raises(ValueError):
        myfunc()
```

*Source: [Assertions about exceptions](https://docs.pytest.org/en/6.2.x/assert.html#assertions-about-expected-exceptions)*


### Pip (package management)

Check installed pip packages: 

```bash
$ python3 -m pip list
````

Source: [Pip documenation > Pip list](https://pip.pypa.io/en/stable/cli/pip_list/)

Example output: 

```bash
Package    Version
---------- -------
attrs      21.2.0
iniconfig  1.1.1
packaging  21.3
pip        21.3.1
pluggy     1.0.0
py         1.11.0
pyparsing  3.0.6
pytest     6.2.5
setuptools 59.0.1
toml       0.10.2
wheel      0.37.0

```