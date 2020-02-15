#Naming Conventions for Python Codes


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->
<!-- code_chunk_output -->

- [Naming Conventions for Python Codes](#naming-conventions-for-python-codes)
  - [Introduction](#introduction)
  - [Naming Conventions](#naming-conventions)
    - [Summary Table](#summary-table)
    - [Variable Naming](#variable-naming)
      - [snake_case](#snake_case)
      - [Private Variable](#private-variable)
    - [Method Naming](#method-naming)
      - [snake_case](#snake_case-1)
    - [Module Naming](#module-naming)
      - [snake_case](#snake_case-2)
      - [Private Class](#private-class)
    - [Package Naming](#package-naming)
      - [snake_case](#snake_case-3)
    - [Underscore](#underscore)
      - [For ignoring values:](#for-ignoring-values)
      - [\__double_leading_underscore](#__double_leading_underscore)
      - [\__double_leading_and_trailing_underscore\_\_](#__double_leading_and_trailing_underscore__)
  - [Code Lay-out](#code-lay-out)
    - [Indentation](#indentation)
    - [Blank Lines](#blank-lines)
    - [Source File Encoding](#source-file-encoding)
    - [Imports](#imports)
    - [Model Level Dunder Names](#model-level-dunder-names)

<!-- /code_chunk_output -->


##Introduction
This document provides naming conventions for the Python codes for better python coding regarding to reading and consistency. It is based on the python naming convention from [NamingConvention](https://namingconvention.org/python/) and [PEP 8](https://www.python.org/dev/peps/pep-0008/).

## Naming Conventions
### Summary Table
| **Type**     | **Public**     | **Internal**     |
| :------------- | :------------- |:------------- |
| Packages       | `lower_with_under` |  NA    |
| Modules       | `lower_with_under`|    `lower_with_under`  |
| Classes       | `CapWords`|    `_CapWords`  |
| Exceptions       | `CapWords`|    NA  |
| Functions       | `lower_with_under()`|    `_lower_with_under()`  |
| Global/Class Constants | `CAPS_WITH_UNDER`| `_CAPS_WITH_UNDER`|
| Global/Class Variables | `lower_with_under`|    `_lower_with_under`  |
| Instance Variables | `lower_with_under`|    `_lower_with_under`  |
| Method Names | `lower_with_under()`|    `_lower_with_under()`  |
| Function/Method Parameters | `lower_with_under`|NA  |
| Local Variables | `lower_with_under`|    NA  |

### Variable Naming
####snake_case

* Should be all in lowercase
* Not begin with the special characters like e.g. & (ampersand), $ (dollar)
* If the name contains multiple words, it should be separated by underscores (\_) e.g. json_string
* Avoid one-character variables e.g. a, b

```python
class Student
    age = None # public variable
    ...
```

####Private Variable
Python does not support privacy directly. This naming convention is used as a weak internal use indicator.
* Should follow the above naming conventions
* Should use a leading underscore (\_) to distinguish between "public" and "private" variables
* For more read the [official python documentation](https://docs.python.org/2/tutorial/classes.html#private-variables-and-class-local-references).

```python
class Student:
    age = None # public variable
    _id = 0 # private variable
  ```
### Constant Naming
#### SCREAMING_SNAKE_CASE
*  be all uppercase letters e.g. AGE, HEIGHT
* If the name contains multiple words, it should be separated by underscores (\_) such as DAYS_IN_MONTH
* May contain digits but not as the first letter

```python
class Product:
    MAX_TEMPERATURE = 36; # constant
  ```

### Method Naming
#### snake_case

* Should be all in lowercase
* Preferably a verb e.g. get_car(), purchase(), book()
* If the name contains multiple words, it should be separated by underscores (\_) e.g. get_json()

```python
class Person:
    def get_height(self):  # method
        return self.height   
  ```

#### Private Method

Python does not support privacy directly. This naming convention is used as a weak internal use indicator.

* Should follow the above naming conventions
* Should use a leading underscore (\_) to distinguish between "public" and "private" functions in a module
* For more read the official python documentation.

```python
class Person:
    def _foot_to_centimeter(self): # private method
        return self.height * 30.48
 ```

### Module Naming
####snake_case

* Should be all in lowercase letters such as requests, math
* If contains multiple words, it should be separated by underscores (\_) e.g. expression_engine.py
* Should resonate with the class or methods inside the module

```python
from math import factorial
class Car:
    ...
  ```

### Class Naming
#### PascalCase

* Begin with an uppercase letter
* Preferably a noun e.g. Car, Bird, MountainBike
* Avoid acronyms and abbreviations

```python
class Car:
    ...
  ```

#### Private Class

Python does not support privacy directly. This naming convention is used as a weak internal use indicator.

* Should follow the above naming conventions
* Should use a leading underscore (\_) to distinguish between "public" and "private" classes
* For more read the [official python documentation](https://docs.python.org/2/tutorial/classes.html#private-variables-and-class-local-references).

```python
class _Car: # private class
```

### Package Naming
####snake_case

* Should be in lowercase.
* If the name contains multiple words, an underscore (\_) should separate it.E.g. expression_engine
* The name should resonate with the class or methods inside the module

```python
from math import factorial
class Car: # public class
    ...
  ```

### Exception Naming
#### PascalCase

*  Exceptions should be classes and hence the class naming convention should be used.
*  Add a suffix "Error" on your exception names, provided the exception is actually an error.
*  Avoid acronyms and abbreviations

```python
class ElectricCarError(Exception):
    """Basic exception for errors raised by non electric cars"""
    def __init__(self, car, type):
        if type is not "electric":
            msg = "%s is not an electric car" % car
        super(ElectricCarError, self).__init__(msg)
        self.car = car
  ```

### Underscore

#### For ignoring values:

If you do not need a specific value(s) while unpacking an object, just assign the value(s) to an underscore.

```python
x, _, y = (1, 2, 3)

# Ignore the multiple values. It is called "Extended Unpacking" which is available in only Python 3.x
x, *_, y = (1, 2, 3, 4, 5) # x = 1, y = 5  

# ignore the index
for _ in range(10):     
    task()  

# Ignore a value of specific location
for _, val in list_of_tuples: # [(1,2),(3,4),(5,6)]
    print(val) # output - 3
  ```

#### \_single_leading_underscore

This convention is used for declaring private variables, functions, methods and classes. Anything with this convention are ignored in `from module import *`.

#### singletrailing_underscore

This convention should be used for avoiding conflict with Python keywords or built-ins.

```python
  class_ = dict(n=50, boys=25, girls=25)
  # avoiding clash with the class keyword
 ```

#### \__double_leading_underscore

Double underscore will mangle the attribute names of a class to avoid conflicts of attribute names between classes. Python will automatically add "\_ClassName" to the front of the attribute name which has a double underscore in front of it.
[Read more in official python documentation](https://docs.python.org/3/tutorial/classes.html#private-variables)

####\__double_leading_and_trailing_underscore\_\_

This convention is used for special variables or ( magic )methods such as `__init__`, `__len__`. These methods provides special syntactic features.
    ```python
    class FileObject:
      '''Wrapper for file objects to make sure the file gets closed on deletion.'''

      def __init__(self, filepath='~', filename='sample.txt'):
        # open a file filename in filepath in read and write mode
        self.file = open(join(filepath, filename), 'r+')
      ```
[List of magic methods](https://github.com/RafeKettler/magicmethods/blob/master/magicmethods.pdf).

## Code Lay-out
### Indentation

Use 4 spaces per indentation level.

### Blank Lines

Surround top-level function and class definitions with two blank lines.
Method definitions inside a class are surrounded by a single blank line.
Extra blank lines may be used (sparingly) to separate groups of related
functions. Blank lines may be omitted between a bunch of related one-liners
(e.g. a set of dummy implementations).
Use blank lines in functions, sparingly, to indicate logical sections.

### Source File Encoding

Code in the core Python distribution should always use UTF-8.

### Imports

Imports should usually be on separate lines.
Imports are always put at the top of the file, just after any module comments
and docstrings, and before module globals and constants.
Wildcard imports (from < module > import * ) should be avoided, as they make it
unclear which names are present in the namespace, confusing both readers and
many automated tools.

### Model Level Dunder Names

Module level "dunders" (i.e. names with two leading and two trailing
underscores) such as __all__, __author__, __version__, etc. should be placed
after the module docstring but before any import statements except from
__future__ imports. Python mandates that future-imports must appear in the
module before any other code except docstrings:
```python
"""
This is the example module.
This module does stuff.
"""

from __future__ import barry_as_FLUFL

__all__ = ['a', 'b', 'c']
__version__ = '0.1'
__author__ = 'Cardinal Biggles'

import os
import sys
  ```
