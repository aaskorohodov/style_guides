# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Spacings](#spacings)
* [Lines length](#lines-length)
* [Code explicitly](#code-explicitly)
  * [Readability VS speed](#readability-vs-speed)
* [Arguments](#arguments)
  * [Accepting arguments](#accepting-arguments)
  * [Pathing arguments](#pathing-arguments)
* [Type-annotations](#type-annotations)
  * [Circular imports](#circular-imports)
* [Constants and defaults](#constants-and-defaults)
* [Methods/functions separations](#methodsfunctions-separations)
* [F-strings VS format](#f-strings-vs-format)
* [Saving code for further use](#saving-code-for-further-use)
* [Interfaces VS base-classes](#interfaces-vs-base-classes)
* [Public and private methods](#public-and-private-methods)
<!-- TOC -->

# Spacings

* [Table of contents](#table-of-contents)

Consider sticking to PEP-8 spacing-recommendations, especially:

- Use spaces when declaring lists, tuples and sets

```python
# Correct
my_list = [1, 2, 3]

# Wrong
my_list_2 = [1,2,3]

# Correct
my_tuple = (1, 2, 3)

# Wrong
my_tuple2 = (1,2,3)

# Correct
my_set = {1, 2, 3}

# Wrong
my_set2 = {1,2,3}
```

- Use spaces when declaring dicts

```python
# Correct
my_dict = {1: 1, 2: 2}

# Correct
my_dict2 = {
    1: 1,
    2: 2
}

# Wrong
my_dict3 = {1:1,2:2}

# Wrong
my_dict4 = {
    1:1,
    2:2
}
```

- Use spaces in function arguments

```python
# Correct
def func(agr1: str, arg2: int = 1, arg3=2) -> None:
    """Docstring
    
    Args:
        agr1: Description
        arg2: Description
        arg3: Description"""

    print(agr1, arg2, arg3)

# Wrong (all 2 arguments are made with wrong spacing)
def func2(agr1:str, arg2:int=1, arg3 = 2) -> None:
    """Docstring
    
    Args:
        agr1: Description
        arg2: Description
        arg3: Description"""

    print(agr1, arg2, arg3)
```

- It is often considered a good practice to make spacings, when assigning/declaring several variables

```python
my_string       = '123'
my_numb         = 123
my_cool_list    = [1, 2, 3, 4, 5]
my_other_string = f'{my_string}{my_numb}'
```

This style makes it easier to distinguish variables and their values. In case your IDE warns you - turn this 
warn off.

# Lines length

* [Table of contents](#table-of-contents)

You should never exceed the length of 120 symbols for any line of code. If there is such a need - consider 
refactoring. You should configure our IDE to check for lines-length:

> Settings -> Editor -> Code Style -> Hard wrap at (120)

You can use any technics, to make your code fit this requirement:

```python
import threading


my_long_string = "In summary, focus your testing efforts on ensuring that your function behaves correctly " \
                 "according to its specification, handles valid and invalid inputs appropriately, and avoids " \
                 "errors and exceptions. While you don't need to test everything in your code, your testing " \
                 "strategy should target the critical aspects that impact your function's functionality, " \
                 "correctness, and reliability."

def func(long_long_long_argument: int,
         long_long_long_argument2: int,
         long_long_long_argument3: int,
         long_long_long_argument4: int) -> int:
    """Docstring"""
    
    # Function call, spread with line-breaking
    print(
      long_long_long_argument,
      long_long_long_argument2,
      long_long_long_argument3,
      long_long_long_argument4
    )
    
    # Breaking lines here as well
    return long_long_long_argument + \
           long_long_long_argument2 + \
           long_long_long_argument3 + \
           long_long_long_argument4

# Making call with several arguments with line-breaking
some_name = 'Very long name, that will not fit into a 120 characters, if used where it needed'
function_call_with_many_arguments = threading.Thread(target=func,
                                                     args=(1, 2, 3, 4),
                                                     daemon=True,
                                                     name=some_name)
```

# Code explicitly

* [Table of contents](#table-of-contents)

Your code should be written as explicit as possible. In general, you should consider writing more code, if this 
makes it easier to read:

```python
# Correct - this function explicitly shows the flow of its operations
def func(your_list: list[int]) -> int | float:
    """Docstring"""

    list_len                = len(list)
    sum_of_lists_elements   = sum(your_list)

    if list_len > 0:
        mean_value = sum_of_lists_elements / list_len
    else:
        mean_value = 0

    return mean_value

# Wrong - this function makes code harder to read and modify
def func2(your_list: list[int]) -> int | float:
    """Docstring"""

    return sum(your_list) / len(list) if len(list) > 0 else 0
```

## Readability VS speed

* [Table of contents](#table-of-contents)

There can be cases, when writing code more explicit will make it significantly slower. This often the case in
situations with a lot of repeatedly made operations. In this case you should choose to write you code in the way,
that might be more hard to read, but will make it faster.

In general, performance is more important than readability. But if reduced performance will not affect
User-experience - you should choose to make your code more readable.

# Arguments

## Accepting arguments

* [Table of contents](#table-of-contents)

If there are several arguments in a funtion/method, consider making line-braking, to improve readability:

```python
# Wrong (hard to read)
def func_with_lots_of_args(arg1: int, arg2: list[int, str, float], agr3: dict[str, int]) -> list[dict[str, int]]:
    """Docstring"""

    print(arg1, arg2, agr3)

    return [{'str': 123}]

# Correct (easy to read)
def func_with_lots_of_args2(arg1: int,
                            arg2: list[int, str, float],
                            agr3: dict[str, int]
                            ) -> list[dict[str, int]]:
    """Docstring"""

    print(arg1, arg2, agr3)

    return [{'str': 123}]
```

## Pathing arguments

* [Table of contents](#table-of-contents)

The same goes for pathing arguments into methods/functions:

```python
class MyClass:
    def func(self, agr1: int, agr2: str, arg3: dict, arg4: list) -> None:
        """Docstring"""
        
        pass


my_int  = 123
my_str  = '123'
my_dict = {1: 1}
my_list = [1, 2, 3]

my_instance = MyClass()

# Wrong
my_instance.func(my_int, my_str, arg3=my_dict, arg4=my_list)

# Wrong
my_instance.func(my_int, my_str,
                 arg3=my_dict, arg4=my_list)

# Correct
my_instance.func(my_int,
                 my_str,
                 arg3=my_dict,
                 arg4=my_list)
```

# Type-annotations

* [Table of contents](#table-of-contents)

You should always annotate all possible types, which includes:

- Arguments of methods and functions
- Return-values of methods and functions (except for when it is None and init of classes)
- Class's attributes
- Constants
- Variables, if type is not understood by IDE or not explicit for Developers

Annotations makes code much easier to handle, as they can reduce possible errors, made by the Developer, due to
IDE's build-in type-checking. For example, if function makes some complex logic, and Developer makes a mistake in
its return value (returns not what is intended to be returned), IDE will warn you:

```python
def func() -> int:
    """Docstring
    
    Returns:
        Some int"""

    my_str = 'str'
    my_number = 123

    # This will cause PyCharm's warning, as str is not the expected return type
    return my_str
```

## Circular imports

* [Table of contents](#table-of-contents)

There can be cases, where annotating types will cause a circular import Exception. Consider such an example:

```python
# file1.py

from file2 import Class2

class Class1:
    def do(self, arg: Class2):
        """Docstring"""
        
        pass
```
```python
# file2.py

from file1 import Class1

class Class2:
    def do(self, arg: Class1):
        """Docstring"""
        
        pass
```

This will result in an Exception, because each file will endlessly try to import another. There are several ways 
to avoid this exception, but it is recommended to use a combination of future and typing:

```python
from __future__ import annotations
from typing import TYPE_CHECKING

if TYPE_CHECKING:
    from file2 import Class2

class Class1:
    def do(self, arg: Class2):
        """Docstring"""
        
        pass
```
```python
# file2.py
from __future__ import annotations
from typing import TYPE_CHECKING

if TYPE_CHECKING:
    from file1 import Class1

class Class2:
    def do(self, arg: Class1):
        """Docstring"""
        
        pass
```

TYPE_CHECKING is a value, that will be 0 during runtime, and is 1 at all the other time. This allows IDE to 
threat any imports under 'if TYPE_CHECKING:' statement to be logit, and blocks actual imports during runtime.

The second part of these magic '''from __future__ import annotations''' works a bit more complicated, so you can
google it or simple use it blindly.

# Constants and defaults

* [Table of contents](#table-of-contents)

If there is a need in having some constant values, for example in case of default return-value for some function,
it is considered a better practice to declare this return value as a constant, rather than storing this value right
in the code, where it is used:

```python
# Wrong
def func(arg: int) -> int:
    """Docstring"""

    if arg < 0:
        return 123
    else:
        return arg + 10

# Correct
DEFAULT_VALUE = 123
ADDITIONAL_SUMM = 10

...

def func2(arg: int) -> int:
    """Docstring"""

    if arg < 0:
        return DEFAULT_VALUE
    else:
        return arg + ADDITIONAL_SUMM
```

This makes it easier to manage such constants, as they can all be set in a separate file, for example in init for 
a module, or at least at the beginning of the current file, where such method/function exists. In case of classes,
such values can be stored in class's attribute:

```python
class MyClass:
    def __init__(self):
        self.default_value: int     = 123
        self.additional_summ: int   = 10
      
    def func2(self, arg: int) -> int:
        """Docstring"""
    
        if arg < 0:
            return self.default_value
        else:
            return arg + self.additional_summ
```

# Methods/functions separations

* [Table of contents](#table-of-contents)

In general, it is considered a good practice to divide complicated classes into smaller ones, so that each would
have less code in it. Still there are cases, where classes may have many methods, or file may have many functions.
In such cases, it is recommended to group methods/functions and divide them with comments, 'declaring' groups:

```python
class OverComplicatedClass:
    def __init__(self):
        pass

    # Mathematical-methods

    def summ(self) -> int:
        pass

    def division(self) -> int:
        pass

    def multiply(self) -> int:
        pass
    
    # String-methods
    
    def concatenate(self) -> str:
        pass
    
    def lower(self) -> str:
        pass
    
    def upper(self) -> str:
        pass
```

This approach makes it easier to navigate in such classes/modules.

# F-strings VS format

* [Table of contents](#table-of-contents)

In general, in is recommended to use f-strings, instead of .format(), as f-strings are easier to read and modify,
and they are also harder to make mistakes in:

```python
name = "Alice"
age = 30

message1 = f"Hello, my name is {name} and I am {age} years old."
message2 = "Hello, my name is {} and I am {} years old.".format(name, age)
```

This illustrates, that using f-string is more convenient, as you can clearly see where {name} and {age} will go.
In case of format(), it is harder to find the exact place of formatting, and in case of several arguments it is 
easy to place them in the wrong spot or provide fewer/more arguments, than there are placeholders.

# Saving code for further use

* [Table of contents](#table-of-contents)

It is considered a bad practice, to comment unused code or keeping it in a project. If there is any segments of 
code, that is not needed in current release - consider deleting it completely, not to confuse Developers.

# Interfaces VS base-classes

* [Table of contents](#table-of-contents)

Python does not have direct support of Interfaces. Instead, there are informal interfaces or constructs, made with
other libraries. This allows you to build interfaces with some basic functionality, for example with methods,
that have some default behaviour:

```python
from abc import ABC, abstractmethod

class MyInterface(ABC):
    @abstractmethod
    def __init__(self):
        """Declaring as abstract, blocks it from being instantiated"""

    def my_method(self) -> str:
        """Method with default behaviour"""

        return 'default behaviour'

    
class MyClass(MyInterface):
    def __init__(self):
        pass

class OtherClass(MyInterface):
    def __init__(self):
        pass
    
    def my_method(self) -> str:
        """Docstring"""

        return 'overridden behaviour'
```

In this example, MyClass.my_method() can be used, which will result in executing MyInterface.my_method() with 
its default behaviour. This is not the case with some other programming languages, where interfaces require
all of their methods to be overriden.

In general, you can build such interfaces, that have any default behaviour - while this breaks the concept
of an interface, this goes well with Python's philosophy, which de-facto provides more freedom.

Still, keep in mind that mixing functionality of an interface and a base-class can be confusing, but negative 
effects can be neutralized by broader docstrings.

# Public and private methods

* [Table of contents](#table-of-contents)

Public methods have regular names, while private methods have underscores at the beginning of their names:

```python
class MyClass:
    def public_method(self) -> None:
        """Anyone can use this method!"""
        
        pass
    
    def _private_method(self) -> None:
        """This method can only be used inside this class!"""
    
        pass

    def __very_private_method(self) -> None:
        """This method can only be used inside this class and can not be overriden by any descendant!"""

        pass
```

This is a standard Python's convention, that should **always be maintained**! That means that:

- If you are building a method, that is designed to be private, you should make it _private()
- If you are building a method, that is designed not to be overriden, you should use __ in its name
- If you need to use private method outside if a class - refactor it, before using it
