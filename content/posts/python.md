---
title: "🤷‍♂️ Python (noob notes)"
date: 2021-12-21T12:00:00+01:00
draft: false
showtoc: true
tags: ["python", "noob notes"]
---

Context: These are noob notes on Python (mostly notes-to-self). They are incomplete by default.

### Formatting and style

#### Indentation

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

### Strings

#### f-strings (formatted string literals)

```py
>>> import math
>>> print(f'The value of pi is approximately {math.pi:.3f}.')
The value of pi is approximately 3.142.
```

*Source: Python docs [7.1. Fancier Output Formatting](https://docs.python.org/3/tutorial/inputoutput.html#fancier-output-formatting)*

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

#### Checks if element(s) exists in list

Using **`in`** operator:

```python
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

`d.items()` and `ErrorValue: too many values to unpack (expected 2)`

Source: [Career Karma](https://careerkarma.com/blog/python-valueerror-too-many-values-to-unpack-expected-2/)

### [`copy.deepcopy()`](https://docs.python.org/3/library/copy.html)

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

### Type hinting

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