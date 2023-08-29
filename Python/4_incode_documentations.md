# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Self-explanatory code](#self-explanatory-code)
* [Basics](#basics)
  * [Comments VS docstrings](#comments-vs-docstrings)
  * [What should be documented](#what-should-be-documented)
  * [Where should type-annotations be?](#where-should-type-annotations-be)
  * [Whom do I write docs for?](#whom-do-i-write-docs-for)
  * [When to use comments](#when-to-use-comments)
* [Docstrings](#docstrings)
  * [What should be annotated with Docstring](#what-should-be-annotated-with-docstring)
  * [Docstring with Google-style](#docstring-with-google-style)
  * [Quotes](#quotes)
  * [Docstring structure](#docstring-structure)
    * [Header](#header)
    * [Attributes](#attributes)
    * [Broader description](#broader-description)
    * [Structure example](#structure-example)
  * [KeyWords](#keywords)
    * [Args](#args)
    * [Returns](#returns)
    * [Raises](#raises)
    * [Other](#other)
  * [Docstring for file](#docstring-for-file)
* [Comments](#comments)
  * [When to use comments](#when-to-use-comments-1)
  * [Double-quotes](#double-quotes)
  * [Hashtag VS single-quotes](#hashtag-vs-single-quotes)
  * [Comments VS self-explanatory code](#comments-vs-self-explanatory-code)
  * [Comment's style](#comments-style)
  * [Comments instead of Docstrings](#comments-instead-of-docstrings)
* [Requirements.txt](#requirementstxt)
<!-- TOC -->

---

# Self-explanatory code

* [Table of contents](#table-of-contents)

**Self-explanatory code is a myth**, that derives from the idea, that there should be as little comments and as
simple docstrings, as possible. By misunderstanding that idea (which is in general correct and helpful), people often
come to the such conclusion:

> There should be as few comments as possible
>> => No comments at all is the best 
>>> => I will not write comments at all, so that my code will be the best code ever!

> There should be as short Docstring as possible
>> 0 is the smallest number
>>> => My docstrings should have 0 symbols to be the shortest
>>>> => I should stop writing docstrings at all, to make my code the best!

# Basics

* [Table of contents](#table-of-contents)

In-code documentations are:

- Docstrings ("""this""")
- Comments (# this, '''this''', 'this', "and this")
- Type annotations (def func(arg_1: Type <- this))

## Comments VS docstrings

* [Table of contents](#table-of-contents)

In the context of these Guidelines:

```python
"""This is docstring. It is, because it is placed on top of the file and is put in double-quotes

A docstring is such a comment, that:

1. Is double-quoted
2. Is located at the beginning of function/class/method/file or under variable-declaration
"""

# This is comment

def func():
    """This is not a comment, it's a docstring, because it is at the beginning of function and is double-quoted"""

    pass

MyConstant = 123
"""This is a docstring for a variable. Hover your mouse on top of it, to see this docstring, picked up by IDE"""

def func2():
    # This is not a docstring, this is a comment

    pass

def func3():
    # Maybe now,
    # when I made this comment
    # to be so long and take several lines, it is a docstring?
    # No. This is still a comment. But now it is spread onto several lines.

    pass

"""Alright then, now I made a docstring!"""
"""No, you made a comment, but you used a double-quotes, which should not be done - use single-quotes for comments"""

'''How about now?'''
'''Still a comment, but now it looks right.

This is a comment, because it is located inside a code, not at the beginning of function/class/method/file,
and because it is not double-quoted.

In general, you can distinguish comment from docstring, by you IDE's behaviour:

- If IDE can not pick up your docstring and use it as a hint-tip - than you have a comment.
'''
```

## What should be documented

* [Table of contents](#table-of-contents)

Everything.

Every method/function/class should have a docstring. Docstring should be made as explicit, clear and convince, as
possible.

> Why should I make a docstring for a method, that returns the summ of 2 numbers, that it receives? It too simple
> to explain anything here!

There 2 main reasons:

1. With docstring, Developer can understand what your method does, without jumping to it.
2. If you stop writing docstrings at one place, you will stop doing that in some other as well.

## Where should type-annotations be?

* [Table of contents](#table-of-contents)

Everywhere, except for return values in init-methods of classes.

## Whom do I write docs for?

* [Table of contents](#table-of-contents)

Consider writing you documentation for a person, who started using Python today. This person have already learned
about basic cycles, classes and interfaces, but have not yet written a single line of code. This person have an IQ
of 7-year-old, and drunk a bottle of vodka yesterday, so they don't feel well. This person will interpret any piece
of code in the wrong way, if they have a chance to do so, which will lead to severe errors, that YOU (not this person)
will have to deal with.

## When to use comments

* [Table of contents](#table-of-contents)

Comments should be used in small pieces of code, to clarify its purpose or your intentions. Any place, where 
Developer may have a small bump in reading your code - comment should be there. Remember, that your code will 
be more often read, than writen. Basically, your code will be written exactly once.

---

# Docstrings

* [Table of contents](#table-of-contents)

- Docstrings in Python should be """double-quoted 3 times"""
- Docstrings can be picked up my PyCharm as hints for Developers
- Docstrings may be on top of any file, class, method, function and under any variable-declaration

## What should be annotated with Docstring

* [Table of contents](#table-of-contents)

1. Each file
2. Each class
3. Each method
4. Each function
5. Constants
6. Some variables, if Developer consider to do so (optional)

## Docstring with Google-style

* [Table of contents](#table-of-contents)

If you have never heard about these type of Docstrings, check this out:

> [Google-style docstring example](https://gist.github.com/redlotus/3bc387c2591e3e908c9b63b97b11d24e)

Google-styled Docstring is a convention for Docstrings, made by Google. This is a widely spread Docstring, that is
supported by PyCharm and many other IDEs. By 'supported' I mean that its keywords can be recognized, so PyCharm
will show, for example, arguments descriptions made with such Docstring, when you hover your mouse over function or
method.

My projects are not made in pure Google-style docstrings. Instead, there is a combination, where
type-annotations are made with Python's build-in annotations, and keywords in Docstrings are used for deeper
information.

```python
def func(arg_1: str, arg_2: int) -> int:
    """Header, that shortly explains what this function does
    
    More broad description, of what this function does.
    This broad description may take several lines.
    
    Broad description can also take several paragraphs
    if you have enough info to place here.
    
    Args:
        arg_1: Description for this arg
        arg_2: Description for that arg
    Notes:
        Some note, that can be used interchangeably with 'More broad description' above.
    Raises:
        Some description, about which errors can be raised by this function, if it does so or is expected to.
    Examples:
        Some examples, of what this function can do or how it can be used
    Returns:
        Description of what is the thing, that this function returns"""

    pass
```

What happens here:

- Type-annotations are made with Python's build-in mechanism
- Argument's descriptions are made with Google-style Docstring, under keyword 'Args'
- Arguments under 'Args' do not have type-annotations in Google-style (although it supports them)
- Return value is annotated with Python's mechanism, but description is made with Google-style

So overall this is a combination, that PyCharm understands. IDE will show type-hints for this function and all
descriptions for arguments and a return value. IDE will also get all the other keywords, that Google-style have,
like 'Notes', 'Raises', 'Examples' etc.

## Quotes

* [Table of contents](#table-of-contents)

- You should always use double-quotes, as this is a PEP-8 convention, Google-style convention and is the only way
  PyCharm can recognize it as a Docstring.

```python
# Correct
def func():
    """Some Docstring in double-quotes"""

    pass

# Wrong
def func():
    '''Some Docstring in single-quotes'''

    pass
```

- You should always use 3 pairs of double-quotes

```python
# Correct
def func():
    """Some Docstring in double-quotes"""

    pass

# Wrong
def func():
    ""Woun't be recognized py Python's interpreter as a comment section. Exception will be raised""

    pass

# Wrong
def func():
    "Wrong styling, broken conventions. Not a logit Docstring"

    pass
```

- Header should always follow first 3 quotes (immediately, no spacings, no line-braking)

```python
# Correct
def func():
    """Correct way to do that"""

# Wrong
def func():
    """
    Wrong way to do that"""

# Wrong
def func():
    """     Wrong way to do that"""
```

- Ending-quotes should always be immediately after docstring content

```python
# Correct
def func():
    """Correct way to do that"""

# Wrong
def func():
    """Not a correct way to do that
    """

# Wrong
def func():
    """
    Not a correct way to do that
    """

# Correct
def func() -> str:
    """Correct way to do that
    
    Returns:
        Some string"""

# Wrong
def func() -> str:
    """Not a correct way to do that
    
    Returns:
        Some string
    """

# Correct
def func() -> None:
    """Correct way to do that
    
    Broad description"""

# Wrong
def func() -> None:
    """Not a correct way to do that
    
    Broad description
    """
```

## Docstring structure

* [Table of contents](#table-of-contents)

Docstring Should be structured in this order:

1. **Header**, that briefly explains what this thing (method/function/class) does. 1 line only
2. 1 spacing (if there is anything else down there (all the rest is optional))
3. **Broad description** (if needed)
4. **Attributes** for Class description (if needed)
5. **Args** for methods/functions (if needed)
6. Notes, Examples, Raises or any other keywords (if needed)
7. **Returns** for methods/functions (if needed)

The only must-have is a Header. It should always be present, while all the rest is optional either because of the
Developer's choice or because of the Docstringed object's nature (nothing to return, not raises anything, etc.)

### Header

* [Table of contents](#table-of-contents)

**Header** should refer to the overall functionality of the object (function/method/class). It will be picked up by 
IDE as a function main description.

### Attributes

* [Table of contents](#table-of-contents)

**Attributes** are a special keyword for classes description. For each attribute, described this way, IDE will 
provide its description anywhere further in code, which is very useful.

### Broader description

* [Table of contents](#table-of-contents)

**Broad description** can be used for classes and functions/methods. It is optional, and can indicate that this
method/function is too complex => refactoring is needed. This description can take as many lines as necessary,
including several paragraphs, divided by empty lines.

### Structure example

* [Table of contents](#table-of-contents)

```python
class MyClass:
    """Header
    
    Broad description, that may take as much space as needed,
    including new line
    
    And even several different paragraphs
    may be used, if needed.
    
    Attributes:
        some_atr: Some description"""

    def __init__(self, arg: int):
        """Header
        
        Some broad description
        
        Args:
            arg: Description of an arg"""

        self.some_atr = arg

    def my_method(self, arg: str) -> str:
        """Header
        
        Broad description
        
        Args:
            arg: Description of an arg
        Notes:
            Some note
        Raises:
            ValueError: In some cases
        Returns:
            Some string, that is the result of this method"""

        if not arg:
            raise ValueError()
        else:
            arg += 'some tricky manipulations, explained in Broad description'
            return arg
```

## KeyWords

* [Table of contents](#table-of-contents)

Keywords are embed into Google-style Docstring convention.

### Args

* [Table of contents](#table-of-contents)

If there are any arguments - 'Args' should be used in a docstring for each of them

```python
# Correct
def func(arg: str) -> None:
    """Description
    
    Args:
        arg: Description"""

    pass

# Wrong
def func(arg: str) -> None:
    """Description"""

    pass
```

### Returns

* [Table of contents](#table-of-contents)

If function or method returns any value, except for None - 'Returns' should be used

```python
# Correct
def func(arg: str) -> None:
    """Description
    
    Args:
        arg: Description"""

    pass

# Wrong
def func(arg: str) -> None:
    """Description
    
    Returns:
        Nothing actually"""

    pass

# Wrong
def func(arg: str) -> str:
    """Description"""

    pass

# Correct
def func(arg: str) -> int:
    """Description
    
    Args:
        arg: Description
    Returns:
        Description"""

    pass
```

### Raises

* [Table of contents](#table-of-contents)

If function or method is implicitly raises any error - 'Raises' should be used

```python
# Correct
def func(arg: int) -> None:
    """Description
    
    Args:
        arg: Description
    Raises:
        ValueError: In some case"""

    if arg <= 0:
        raise ValueError()

# Wrong
def func(arg: int) -> None:
    """Description
    
    Args:
        arg: Description"""

    if arg <= 0:
        raise ValueError()
```
If function is expected to raise an error in some case implicitly - 'Raises' may be used (optional)

```python
# Correct
def func(arg: int) -> None:
    """Description
    
    Args:
        arg: Description
    Raises:
        ZeroDivisionError: If arg == 0"""

    print(10 / arg)

# Correct <- AS WELL!
def func(arg: int) -> None:
    """Description
    
    Args:
        arg: Description"""

    print(10 / arg)
```

### Other

* [Table of contents](#table-of-contents)

Any other keywords may be used if and when needed.

## Docstring for file

* [Table of contents](#table-of-contents)

- Files should also have trier Docstrings. You should do that by placing double-quoted Docstring on top of the file,
  higher than any imports. This Docstring may have any keywords as well, and any structure you like.

```python
"""
This is a module-level docstring.

Description of the module goes here.

Attributes:
    module_variable (int): Description of the module-level variable.
"""

module_variable = 42

def function_example():
    pass
```

- It should reflect the purpose of this file, rather that explain its classes of functions.

```python
# Wrong:
"""This module have 2 classes:

- MyClass1: does this
- MyClass2: does that"""
```
```python
# Correct:
"""This module does this and that"""
```

- It should be clear to the Developers, what they can add to this file, and what shouldn't.

# Comments

* [Table of contents](#table-of-contents)

Comments are:

- Any single-quoted comments
- Any comment, made with hashtag #

## When to use comments

* [Table of contents](#table-of-contents)

In general, you should use comments to explain small segments in your code, that may not be obvious, or to help
Developers read and understand your code. For example:

```python
def add_element(my_tuple: tuple, element: str) -> tuple:
    """This function adds provided element into provided tuple
    
    Args:
        my_tuple: Your tuple, to add element into
        element: Your element, to add into tuple
    Notes:
        Remember, that you will get a different tuple, not the one you pathed, as they are immutable!
    Returns:
        Tuple, updated with new element"""
    
    # Converting tuple into list, because tuples in Python are immutable
    my_list = list(my_tuple)
    my_list.append(element)
    
    return tuple(my_list)
```

In this example, Developer may not understand, why you converted my_tuple into list(). There are several options of 
how can tuple be updated with new element, and converting it into list may be confusing. This may force developer
to dive into your code or Python's documentation, lose time and or even get lost in that documentation.

You should not use comments everywhere, instead try to put yourself in position of any Developer that will read
your code, and if you think, that some place in your code looks good, but may be confusing - use comments.

If some place of your code does not look good - do not place a comment there, refactor it first. Otherwise, you may
start writing over-complicated code, and let your comment explain it. This can solve the problem of reading your 
code, but may cause your code to be too complicated to modify.

## Double-quotes

* [Table of contents](#table-of-contents)

It is considered a bad practice to use double-quotes for commenting. Any comment should be made with single-quotes.

## Hashtag VS single-quotes

* [Table of contents](#table-of-contents)

You should use hashtags to write single-lined comments, and single-quotes to write multy-lines comments, because
using hashtags to write multy-lines comments are hard to copy (Ctrl+C), due to hashtags, that will be copied with
your actual comment-text.


```python
# Correct way to write comment
my_var = 123

# Wrong way 
# to write comment
another_var = 321

'''Correct way 
to write comment'''
some_other_var = 456

'''Wrong way to write comment, because it is single-lined. User # for this'''
var_my = 654
```

## Comments VS self-explanatory code

* [Table of contents](#table-of-contents)

**Code is never self-explanatory**. The idea of self-explanatory code, that requires no comments is a myth. Still, 
you should try to make your code as simple and easy to understand, as possible, so that there would be as little 
comments as possible.

If you encountered a segment of code, that requires a lot of commenting, there could be 2 antipatterns present:

1. Docstring is too short and did not cover this segment of the code
2. Your code is too complicated and requires refactoring

If none of these two factors can be fixed, it would be better to have a comment still.

## Comment's style

* [Table of contents](#table-of-contents)

- Use 2 spaces between a code and comment, if comment goes in the same line
- Use 1 space from hashtag to the comment's text

```python
my_tuple = (1, 2, 3)
my_list = list(my_tuple)  # 2 spaces used after code ends, 1 space used after hashtag. Correct
my_list.append(4) # 1 space used between code and comment. Wrong
my_list.append(5)  #No space used after hashtag. Wrong
```

- Consider lining you comments, of there are several of them (if possible)

```python
my_var = 1              # Comment
another_var = 2         # Comment
my_list = [1, 2, 3, 4]  # Comment
```

This approach will help with reading your code, as it becomes easier to distinguish code from comments.

## Comments instead of Docstrings

* [Table of contents](#table-of-contents)

You should never use comments, when you can provide the same information in a docstring, because comment can not 
be picked up by IDE.

```python
CONSTANT = 123
# Wrong

CONSTANT2 = 123
"""Correct! Hover your mouse over CONSTANT2 declaration, to see that IDE picked it up (if reading in IDE)"""
```

Wrong:

```python
def func(arg1, arg2) -> None:
    # arg1 is a tuple
    # arg2 is a string
    
    pass
```

Wrong:

```python
# This is the beginning of some file, and here I will explain what it does, using comment, instead of docstring

def func() -> None:
    pass
```

Wrong:

```python
def complicated_func(arg1: str) -> str:
    """This function performs complex operations on strings.
    
    Args:
        arg1: You string
    Returns:
        Modified string"""
    
    # Now I will explain, what are these complicated manipulations are
    result = arg1 + 'Some complicated manipulations'
    
    return result
```

Correct:

```python
def complicated_func(arg1: str) -> str:
    """This function performs complex operations on strings.
    
    Now I will explain, what are these complicated manipulations are, using broad-explanation-section of a docstring,
    that can span onto several lines, right after docstring's header. It will also be picked up be IDE. Cool!
    
    Args:
        arg1: You string
    Returns:
        Modified string"""
    
    # And here I will only explain, that this operation is string-concatenation
    result = arg1 + 'Some complicated manipulations'
    
    return result
```
# Requirements.txt

* [Table of contents](#table-of-contents)

> Every project should include requirements.txt file, listed all the non-standard libraries, required for this 
> concrete project ot work.

The simplest way to make such file is to type this command:

```commandline
pip freeze
```

Then copy all the requirements as it is, into requirements.txt, including version specification

requirements.txt:

```
async-timeout==4.0.2 
clickhouse-driver==0.2.5 
kafka-python==2.0.2      
numpy==1.24.2        
```  

**Make sure, that there is no any libraries, that are not essential for this project to work, i.e. which were 
installed during the development process, but were not used.**

If there are some libraries, that would be installed by pip automatically, during the installation process of other
libraries (dependencies), you can skipp them. But to do so, you need to be extra sure, that these dependencies will
actually be installed automatically.

When working with newly pulled project, consider creating venv and installing all dependencies using:

```commandline
pip install -r requirements.txt
```