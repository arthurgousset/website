---
title: "🤷‍♂️ Python (noob notes)"
date: 2021-12-21T12:00:00+01:00
draft: false
showtoc: true
tags: ["python", "noob notes"]
---

Context: These are noob notes on Python (mostly notes-to-self). They are incomplete by default.

## Formatting and style

### Indentation

Closing brace/bracket/parenthesis on multiline constructs:

```py
# correct
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )

# also correct
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

*Source: [PEP 8: Indentation](https://www.python.org/dev/peps/pep-0008/#indentation)*

## Built-in

### Strings

#### f-strings (formatted string literals)

*Source: [RealPython](https://realpython.com/python-formatted-output/#the-string-format-method-simple-replacement-fields)* (for all notes on formatted strings below)

##### **Syntax**: **`{[<name>][!<conversion>][:<format_spec>]}`**

| Component     | Meaning                                                                   |
|---------------|---------------------------------------------------------------------------|
| **`<name>`**        | Specifies the source of the value to be formatted                         |
| **`!<conversion>`**  | Indicates which standard Python function to use to perform the conversion |
| **`:<format_spec>`** | Specifies more detail about how the value should be converted             |

##### **`<name>`**:
- indicates which **arguments** are passed (e.g. `a`, `b`, `c` in example below)

```py
# with variables
a = 1
b = 2
c = 3
f'{a} {b} {c}'

# with list
L = ['foo', 'bar', 'baz']
f'{L[0]} {L[1]} {L[3]}'

# with dictionary
d = {'key1': 'foo', 'key2': 'bar'}
f'{d[key1]} {d[key2]}'

# with arbitrary object attribute
f'{obj.attr}'
```


##### **`!<conversion>`**:
- format an object as a **string**

| Value | Meaning              |
|-------|----------------------|
| `!s`    | Convert with `str()`   |
| `!r`    | Convert with `repr()`  |
| `!a`    | Convert with `ascii()` |

##### **`:<format_spec>`**:

- represents the `.format()` functionality
- `:[[<fill>]<align>][<sign>][#][0][<width>][<group>][.<prec>][<type>]`

| Subcomponent | Effect                                                                                                                                                    |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `:`            | Separates the <format_spec> from the rest of the replacement field                                                                                        |
| `<fill> `      | Specifies how to pad values that don’t occupy the entire field width                                                                                      |
| `<align>`      | Specifies how to justify values that don’t occupy the entire field width                                                                                  |
| `<sign>`       | Controls whether a leading sign is included for numeric values                                                                                            |
| `#`            | Selects an alternate output form for certain presentation types                                                                                           |
| `0`            | Causes values to be padded on the left with zeros instead of ASCII space characters                                                                       |
| `<width>`      | Specifies the minimum width of the output                                                                                                                 |
| `<group>`      | Specifies a grouping character for numeric output                                                                                                         |
| `.<prec>`      | Specifies the number of digits after the decimal point for floating-point presentation types, and the maximum output width for string presentations types |
| `<type>`       | Specifies the presentation type, which is the type of conversion performed on the corresponding argument                                                  |

##### **`<type>`**:

-  specifies the presentation

| Value  | Presentation Type             |
|--------|-------------------------------|
| `b`      | Binary integer                |
| `c`      | Single character              |
| `d`      | Decimal integer               |
| `e` or `E` | Exponential                   |
| `f` or `F` | Floating point                |
| `g` or `G` | Floating point or Exponential |
| `o`      | Octal integer                 |
| `s`      | String                        |
| `x` or `X` | Hexadecimal integer           |
| `%`      | Percentage                    |

```py
# ':b' binary
>>> f'{1:b}'
'1'
>>> f'{5:b}'
'101'
>>> f'{10:b}'
'1010'

# '%' percentage
>>> f'{0.01:%}'
'1.000000%'
>>> f'{0.01:.1%}'
'1.0%'
>>> f'{0.01:.0%}'
'1%'
```


##### `[[<fill>]<align>]`:
- controls where output is positioned within the specified field width
- `<width>` has to be specified, else `<fill>` and `<align>` are ignored


##### **`<align>`**:

| Option | Action           |
|---------|------------------|
| `<`       | left-justifies   |
| `>`       | right-justifies  |
| `^`       | centers          |
| `=`       | left-aligns sign |
    
```py
# '<'
>>> f'{1:=+8}'
'+      1'
>>> f'{1:+8}' # comparison without '='
'      +1'
```

##### **`<fill>`**:
- specifies how to fill in **extra space** when the formatted value doesn’t completely fill the output width


```py
>>> f'{1:+>8}'
'+++++++1'
>>> f'{1:+<8}'
'1+++++++'
```
    

```py
# '.f'
>>> f'{123.456789:.2f}'
'123.46'
>>> f'{123.456789:.3f}'
'123.457'
>>> f'{123.456789:.4f}'
'123.4568'
>>> f'{123.456789:.5f}'
'123.45679'
```

##### **`<sign>`**:
- controls whether a *sign* appears in numeric output 


| Sign | Action                                      |
|------|---------------------------------------------|
| `+`    | incl. leading sign for **positive** and **negative** values |
| `-`    | incl. leading sign for **negative** values              |

```py
# '+' pos and neg values
>>> f'{1:+}' 
'+1'
>>> f'{-1:+}'
'-1'

# '-' only neg values
>>> f'{1:-}'
'1'
>>> f'{-1:-}'
'-1'
```

##### **`<width>`**: 
- specifies the **minimum width** of the output field
- if output is longer, minimum is ignored

```py
>>> f'{1:8}'
'       1'
>>> f'{1:4}'
'   1'
>>> f'{1:2}'
' 1'
>>> f'{1000:2}' # ignored if longer
'1000'
```

##### **`<group>`**:
- add a *separator* character in **numeric output** (either a comma character `,` or an underscore character `_`)

```py
>>> f'{1000:,}'
'1,000'
>>> f'{1000:_}'
'1_000'
>>> f'{1000000:,}'
'1,000,000'
>>> f'{1000000:_}'
'1_000_000'
```

##### **`.<prec>`**: 
- **decimal digits** for floating point

```py
# decimals
>>> f'{1:.0f}'
'1'
>>> f'{1:.1f}'
'1.0'
>>> f'{1:.2f}'
'1.00'
>>> f'{1:.3f}'
'1.000'

# with width
>>> f'{1:4.0f}'
'   1'
>>> f'{1:4.1f}'
' 1.0'
>>> f'{1:4.2f}'
'1.00'
>>> f'{1:4.3f}'
'1.000'
```


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

### Lists

#### Comparing lists with `.sort()` or `set(list)` and `==`

Lists are not `==` if elements are at different indices.

Instead sort lists in-situ using `.sort()` or compare sets using `set(list)`.

```py
# Example
>>> [1, 2] == [2, 1]
False

>>> [1, 2].sort() == [2, 1].sort()
True

>>> set([1, 2]) == set([2, 1])
True
```

#### Checks if element(s) exists in list

Using **`in`** operator:

```py
if i in lst:
  print("Found")
  
if "a" in "arthur":
  print("Found")
```

Using **`list.count()`** function:

```py
list.count(elem) == 1
```
*Source: [thispointer.com](https://thispointer.com/python-how-to-check-if-an-item-exists-in-list-search-by-value-or-condition/)*


Using **`all()`** function:

```py
'''
    check if list1 contains all elements in list2
'''
result =  all(elem in list1  for elem in list2)
````

*Source: [thispointer.com](https://thispointer.com/python-check-if-a-list-contains-all-the-elements-of-another-list/)*


**[`all(iterable)`](https://docs.python.org/3/library/functions.html#all)**: Return `True` if all elements of the *iterable* are true (or if the iterable is empty). Equivalent to:

```py
def all(iterable):
    for element in iterable:
        if not element:
            return False
    return True
```

Using **`any()`** function:

```py
'''
    check if list1 contains any elements of list2
'''
result =  any(elem in list1  for elem in list2)
```

*Source: [thispointer.com](https://thispointer.com/python-check-if-a-list-contains-all-the-elements-of-another-list/)*

**[`any(iterable)`](https://docs.python.org/3/library/functions.html#any)**: Return True if any element of the iterable is true. If the iterable is empty, return False. Equivalent to:

```py
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```

#### [`list.index(x)`](https://docs.python.org/3/tutorial/datastructures.html)

Return zero-based index in the list of the first item whose value is equal to x. Raises a `ValueError` if there is no such item.

`list.index(x[, start[, end]])`: The optional arguments *start* and *end* are interpreted as in the slice notation and are used to limit the search to a particular subsequence of the list. The returned index is computed relative to the beginning of the full sequence rather than the *start* argument.

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

#### Key-value types

- Keys are unique within a dictionary and must be of an immutable data type such as strings, numbers, or tuples.
- Values must not be unique and can be of any type

*Source: [TutorialPoint](https://www.tutorialspoint.com/python/python_dictionary.htm)*

#### `d.items()` and `ErrorValue: too many values to unpack (expected 2)`

Source: [Career Karma](https://careerkarma.com/blog/python-valueerror-too-many-values-to-unpack-expected-2/)

### Objects

#### Constructor (`__init__`)

`Constructors` **initialise** variables when an object is created. Constructors have a **reserved** name `__init__`, e.g.:
We never really call the `__init__` method itself e.g. `CashRegister.__init__`. It's only really used to initialise variables when an object is instantiated.

```py
class CashRegister:
  def __init__(self):
    self._itemCount = 0
    self._totalPrice = 0.0
# instantiate using registerABC = CashRegister()

# or with argument
class CashRegister:
  def __init__(self, initial_balance):
    self._itemCount = 0
    self._totalPrice = initial_balance
# instantiate using registerABC = CashRegister(50)
```

#### `self`

By default, we always pass `self` as an argument when **defining** a `method`, e.g.:

```py
def methodName(self, argument_1, argument_1, ...)
```

But we don't pass `self` when **calling** the method, e.g.:

```py
object.methodName(argument_1, argument_1, ...)
```

You can also use `self` inside methods of a class to refer to the state of the object, e.g.:

```py
class CashRegister: 
  def clear(self):
    self._itemCount = 0
```

Similarly you can reference other objects to access their state inside methods, e.g.:

```py
class CashRegister: 
  def copy(self, other):
    self._itemCount = other._itemCount
    self._totalPrice = other._totalPrice

# call inside main function using registerABC.copy(registerDEF)
```

#### `is` operator

`is` and `is not` are the identity operators. They are used to check if two values (or variables) are located on the same part of the **memory**.

#### [`id(object)`](https://docs.python.org/3/library/functions.html#id) (memory-like address)

[`id(object)`](https://docs.python.org/3/library/functions.html#id): Return the “identity” of an object. This is an integer which is guaranteed to be **unique** and **constant** for this object during its lifetime.

[`hex(x)`](https://docs.python.org/3/library/functions.html#hex) Convert an integer number to a lowercase hexadecimal string prefixed with “0x”

```py
# Example
obj = [1, 2]

>>> id(obj)
4466657600

>>> hex(id(obj))
'0x10a3bc940'
```



#### Attributes of an object

**[`object.__dict__`](https://docs.python.org/2/library/stdtypes.html#object.dict)**: A dictionary or other mapping object used to store an object’s (writable) attributes. 

Alternatively, **[`vars(an_obj)`](https://docs.python.org/2/library/functions.html#vars)**: return the `__dict__` attribute for a module, class, instance, or any other object with a `__dict__` attribute.

```py
class Parent:
  name : str
  age : int
  def __init__(self, name : str, age : int):
    self.name = name
    self.age = age

p = Parent("John Doe", 40)
vars(p)
>>> {'name': 'John Doe', 'age': 40}
p.__dict__
>>> {'name': 'John Doe', 'age': 40}
```

#### Rare use of `global`

We can only **access** global variables in local scopes but cannot **modify** them from local scopes.

The solution is to use the `global` keyword.

The basic rules for `global` keyword in Python are:

* When we create a variable inside a function, it is *local* by default.
* When we define a variable outside of a function, it is *global* by default. You don't have to use `global` keyword.
* We use `global` keyword to read and write a *global* variable inside a function.
* Use of `global` keyword outside a function has no effect.

```py
# Example 1: **Accessing** global Variable From Inside a Function
c = 1 # global variable

def add():
    print(c)

add()
>>> 1
```

```py
# Example 2: **Modifying** Global Variable From Inside the Function
c = 1 # global variable
    
def add():
    c = c + 2 # increment c by 2
    print(c)

add()
>>> UnboundLocalError: local variable 'c' referenced before assignment
```

```py
# Example 3: Changing Global Variable From Inside a Function using global
c = 0 # global variable

def add():
    global c
    c = c + 2 # increment by 2
    print("Inside add():", c)

add()
print("In main:", c)
>>> Inside add(): 2
>>> In main: 2
```

*Source: [Programmiz](https://www.programiz.com/python-programming/global-keyword)*


#### Inheritance

- Inheritance syntax
  - Pass `parent class` as **argument** in `child class` definition, e.g. `class Child_class(Parent_class):`
  - Use `super()` to pass arguments into parent class method
 
```py
class Parent:
  name : str
  age : int
  def __init__(self, name : str, age : int):
    self.name = name
    self.age = age
 
class Mum(Parent):
  profession : str
  def __init__(self, name : str, age : int, profession : str):
    super().__init__(name, age)
    self.profession = profession
    
class Dad(Parent):
  hobby : str
  def __init__(self, name : str, age : int, hobby : str):
    super().__init__(name, age)
    self.hobby = hobby
```
 


#### Example:

```py
class Employee:
'''
Attributes: 
- name
- payroll number
- salary
'''
  def __init__(self, nm, prnum):
    self._name = nm
    self._payrollNum = prnum
    self._salary = 0

  def setSalary(self, sal):
    self._salary = sal

  def statusReport(self):
    s = "%s:%s,%s." % (self._name, self._payrollNum, self._salary)
    return s

class AcademicEmployee(Employee):
'''
New attribute(s):
- department

Inherited attributes (from Employee): 
- name
- payroll number
- salary
'''
  def __init__(self, nm, prnum):
    super().__init__(nm, prnum)
    self._department = "N/A"
  
  def setDepartment(self, dept):
    self._department = dept

class TeachingEmployee(AcademicEmployee):
'''
New attribute(s):
- courses

Inherited attributes (from AcademicEmployee): 
- name
- payroll number
- salary
- department
'''
  def __init__(self, nm, prnum):
    super().__init__(nm, prnum)
    self._courses = "N/A"
  
  def setCourses(self, crss):
    self._courses = crss
```

#### `__repr__` and `__str__`

Almost every object you implement should have a functional `__repr__` that’s usable for understanding the object. Implementing **`str` is optional**: do that if you need a “pretty print” functionality (for example, used by a report generator).

*Source: [Stack Overflow](https://stackoverflow.com/a/2626364)*

Example:

```py
class Person:

    def __init__(self, person_name, person_age):
        self.name = person_name
        self.age = person_age

    def __str__(self):
        return f'Person name is {self.name} and age is {self.age}'

    def __repr__(self):
        return f'Person(name={self.name}, age={self.age})'


p = Person('Pankaj', 34)

print(p.__str__())
>>> Person name is Pankaj and age is 34
print(p.__repr__())
>>> Person(name=Pankaj, age=34)
```

*Source: [JournalDev](https://www.journaldev.com/22460/python-str-repr-functions)*

#### Name of a class using `type().__name__`

**[`definition.name`](https://docs.python.org/2/library/stdtypes.html#definition.name)**: The name of the class, type, function, method, descriptor, or generator instance.

```py
class Parent:
  name : str
  age : int
  def __init__(self, name : str, age : int):
    self.name = name
    self.age = age

def __repr__(self) -> str: # visualises Parent object in CLI
  return f'{type(self).__name__}(name: {self.name}, age: {self.name})'
  

>>> john = Parent("John Doe", 54)
>>> print(john)
Parent(name: John Doe, age: 54)
```

*Source: [DelftStack](https://www.delftstack.com/howto/python/python-get-class-name/)*

### Reading Files

#### **[`open()`](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)**
Returns a file object, and is most commonly used with two arguments: `open(filename, mode)`.

```py
f = open('workfile.txt', 'r')
```

It is good practice to use the `with` keyword when dealing with file objects. The advantage is that the **file is properly closed** after its suite finishes, even if an exception is raised at some point. Using `with` is also much shorter than writing equivalent `try`-`finally` blocks:

```py
>>> with open('workfile.txt', 'r') as f:
...     read_data = f.read()

>>> # We can check that the file has been automatically closed.
>>> f.closed
True
```

After a file object is closed, either by a `with` statement or by calling `f.close()`, attempts to use the file object will automatically fail.


| Character | Meaning                                                         |
|-----------|-----------------------------------------------------------------|
| 'r'       | open for reading (default)                                      |
| 'w'       | open for writing, truncating the file first                     |
| 'x'       | open for exclusive creation, failing if the file already exists |
| 'a'       | open for writing, appending to the end of file if it exists     |
| 'b'       | binary mode                                                     |
| 't'       | text mode (default)                                             |
| '+'       | open for updating (reading and writing)                         |

*Source: Python docs [`open(file, mode)`](https://docs.python.org/3/library/functions.html#open)*

#### [`f.read()`](https://docs.python.org/3/tutorial/inputoutput.html#methods-of-file-objects)

- Reads data and returns it as a **string** (in text mode) or **bytes object** (in binary mode). 
- Optional argument `size` (`f.read(size)`): at most `size` characters (in text mode) or size bytes (in binary mode) are read and returned.
- Without `size` argument, `f.read()` reads the entire contents of the file (your problem if the file is twice as large as your machine’s memory)
- if the end of the file has been reached, `f.read()` will return an **empty string** (`''`).


```py
>>> f.read()
'This is the entire file.\n'
>>> f.read() # reached end of file
''
```

#### [`f.readline()`](https://docs.python.org/3/tutorial/inputoutput.html#methods-of-file-objects)

- Reads a single line from the file
- A newline character (`\n`) is left at the end of the string, and is only omitted on the last line of the file (if the file doesn’t end in a newline)
- If `f.readline()` returns an **empty string** (`''`), the **end of the file** has been reached
- you can **loop** over the file object

```py
# manual
>>> f.readline()
'This is the first line of the file.\n'
>>> f.readline()
'Second line of the file\n'
>>> f.readline() # reached end of file
''

# looping (preferred)
>>> for line in f:
...     print(line, end='')
...
This is the first line of the file.
Second line of the file
```

#### [`f.readlines()` or `list(f)`](https://docs.python.org/3/tutorial/inputoutput.html#methods-of-file-objects)

- Reads all the lines of a file in a **list**
- Each **element** in the list is a string representing a line from the file

```py
# Example
>>> lines = f.readlines()
>>> print(lines)
['This is the first line of the file.\n', 'Second line of the file\n']
```

#### [`str.split()`](https://docs.python.org/3.3/library/stdtypes.html?highlight=split#str.split): Used to split string into separate words

[`str.split(sep=None, maxsplit=-1)`](https://docs.python.org/3.3/library/stdtypes.html?highlight=split#str.split)

- Return a list of the words in the string, using *sep* as the delimiter string
- If *maxsplit* is given, at most *maxsplit* splits are done (thus, the list will have at most `maxsplit+1` elements). 
- If *maxsplit* is not specified or `-1`, then there is no limit on the number of splits (all possible splits are made).
- If *sep* is given, consecutive delimiters are not grouped together and are deemed to delimit empty strings (for example, `'1,,2'.split(',')` returns `['1', '', '2']`)
- If *sep* is not specified or is `None`, consecutive whitespace are regarded as a single separator, and the result will contain **no empty strings at the start or end** if the string has leading or trailing whitespace (for example, `' 1  2   3  '.split()` returns `['1', '2', '3']`)

```py
line = 'Hello how are you doing'
words = line.split()
print(words)
>>> ['Hello', 'how', 'are', 'you', 'doing']
```

#### `str.lstrip()` `str.rstrip()` `str.strip()`: Used to remove whitespace

[`str.lstrip([chars])`](https://docs.python.org/3.3/library/stdtypes.html?highlight=split#str.lstrip): Return a copy of the string with **leading** characters removed.

[`str.rstrip([chars])`](https://docs.python.org/3.3/library/stdtypes.html?highlight=split#str.rstrip): Return a copy of the string with **trailing** characters removed. 

[`str.strip([chars])`](https://docs.python.org/3.3/library/stdtypes.html?highlight=split#str.strip): Return a copy of the string with the **leading** and **trailing** characters removed. 


If *chars* argument is omitted or `None`, **defaults to removing whitespace**.

```py
>>> '   spacious   '.lstrip()
'spacious   '
>>> '   spacious   '.rstrip()
'   spacious'
>>> '   spacious   '.strip()
'spacious'
```


#### `f.write(string)` 

- Writes the contents of *string* to the file, returning the number of characters written.

```py
# "w" for writing to file
>>> outfile = open("text.txt", "w")
>>> outfile.write('This is a test\n')
15
```



### Type hinting

#### Forward type hinting: Used Class is hinted but not yet defined

> When a type hint contains names that have not been defined yet, that definition may be expressed as a **string** literal, **to be resolved later**.

*Source: [PEP484 on Type Hints](https://www.python.org/dev/peps/pep-0484/#forward-references)*



```py
# Example
class Tree:
    def __init__(self, left: 'Tree', right: 'Tree'):
        self.left = left
        self.right = right
```

#### [`typing.Callable`](https://docs.python.org/3/library/typing.html#typing.Callable)

Requires import:
```py
from typing import Callable

# code
```

- Syntax: `Callable[[Arg1Type, Arg2Type], ReturnType]` 
- Requires exactly two values (e.g. `Callable[[int], str]`): 
1. **argument list**: must be a list of types or an ellipsis (e.g. `[int]`)
2. **return type**: must be a single type (e.g. `str`)

There is no syntax to indicate optional or keyword arguments


```py
# Example
from typing import Callable

foo : Callable[[int], str] # function of (int) -> str.

def foo(int: i) -> str:
  return str(i)
```

### Exiting a Python program

The **most preferred method** is `sys.exit()`, because `exit()` and `quit()` functions cannot be used in the operational and production codes. They can only be implemented if the site module is imported.

**[`sys.exit([arg])`](https://docs.python.org/3/library/sys.html#sys.exit)**: 
- This is implemented by raising the `SystemExit` exception, so **cleanup actions** specified by finally clauses of `try` statements are honored, and it is **possible to intercept the exit attempt** at an outer level.
- The optional argument *arg* can be an **integer** giving the **exit status** (defaulting to zero), or another type of object. If it is an integer, zero is considered “successful termination” and any nonzero value is considered “abnormal termination” by shells and the like.

```py
import sys 
 
x = 50
 
if x != 100: 
    sys.exit("Values do not match")  
else: 
    print("Validation of values completed!!") 
>>> Values do not match
```

Using **`quit()`**: 
- As soon as the system encounters the `quit()` function, it terminates the execution of the program completely. 
- The `exit()` function can be considered as an alternative to the `quit()` function, which enables us to terminate the execution of the program.


```py
for x in range(1,10):
    print(x*10)
    quit()
# no output
```


*Source: [askpython.com](https://www.askpython.com/python/examples/exit-a-python-program)*


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

## Libraries

### `import copy`

#### [`copy.deepcopy()`](https://docs.python.org/3/library/copy.html)

```py
import copy

copy.copy(x) # Return a shallow copy of x.
copy.deepcopy(x) # Return a deep copy of x.
```

> copy() is a shallow copy function. If the given argument is a compound data structure, for instance a list, then Python will create another object of the same type (in this case, a new list) but for everything inside the old list, only their reference is copied. Think of it like:

```py
newList = [elem for elem in oldlist]
```

*Source: [Stack Overflow](https://stackoverflow.com/a/32791606)*

### `import random`

**[`random.choice(seq)`](https://docs.python.org/3/library/random.html#random.choice)**: Return a random element from the non-empty sequence *seq*. If *seq* is empty, raises IndexError.

The sequence can be a string, a range, a list, a tuple or any other kind of sequence. *Source: [W3School](https://www.w3schools.com/python/ref_random_choice.asp)*

**[`random.randint(a, b)`](https://docs.python.org/3/library/random.html#random.randint)**: 
Return a random integer *N* such that `a <= N <= b`. Alias for `randrange(a, b+1)`.

### `import os.path`: Used to check if file exists

**[`os.path.exists(path)`](https://docs.python.org/3/library/os.path.html#os.path.exists)**: Return `True` if file exists.

- If the file is in the same folder as the program, the *path* is just simply the **file name**.
- Else you need to pass the full **file path** of the file
- You should use the **forward-slash** (`/`) to separate the path. It’ll work across Windows, macOS, and Linux.

```py
import os.path

file_exists = os.path.exists('readme.txt')
print(file_exists)
>>> True
```

*Source: [Pythontutorial](https://www.pythontutorial.net/python-basics/python-check-if-file-exists/)*
