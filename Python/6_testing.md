# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Politics](#politics)
* [What to test](#what-to-test)
* [What to use](#what-to-use)
* [Tests structure](#tests-structure)
  * [Fixtures](#fixtures)
  * [Entry-point](#entry-point)
* [When to run tests](#when-to-run-tests)
<!-- TOC -->

# Politics

In general, you should test every single piece of your code, as Extreme programming prescribes.

Consider following these statements:

- If a piece of code was not tested - it should be considered broken
- There is no code too simple to be tested
- If your function/method requires too many tests, to test all of its behaviours: split it into smaller
- Do not test Python's build-in behaviour (0/0 will cause ZeroDivisionError each time, trust me)
- Testing all basic segments of your code does not mean, that it works as expected - write integration tests
- Having unit tests and integration tests does not mean, that you program works as expected - perform manual testing
- Having manual testing complete does not mean, that your program works as expected - asks Users to test it

In practice, there can be situations, where you push your code into production without testing it. In this case, you
should notify any Users of yur code, that your code is not tested, therefor can cause unpredictable results or simply
not working at all. If Users go well with that - go for it, but keep in mind, that this untested code need to be 
tested in the future.

# What to test

As a rule of thumb, you should test each function and method, **to do what is designed to**, and **not to do**, 
what it designed not to.

Consider this example:

```python
def summ(arg1: int | float, arg2: int | float) -> int | float:
    """Sums 2 numbers
    
    Raises:
        ValueError: If any arg is not int or float
    Returns:
        Summ of 2 arguments"""
    
    my_args = [arg1, arg2]
    
    for el in my_args:
        if not isinstance(el, int) or not isinstance(el, float):
            raise ValueError
    
    summ_of_args = arg1 + arg2

    return summ_of_args
```

What should be tested:

- Function raises ValueError, if any of the args is not int or float
- Function works with any numbers (positive ints and floats, negative ints and floats, 0)
- Function returns type int or float with any arguments (from expected)
- Function works, if one of the argument is int, and the other is a float

What should not be tested:

- Function raises an error, if only 1 argument pathed
- Function works with decorators (decorators, if present, should be tested separately)
- Other basic Python's behaviour

What else can be done:

- Checking for correct type of the arguments can be moved into separate function
- In this case, tests should be made for that separate function
- Summ still should be checked for raising exception, as it still will be its functionality
- Summ should not be checked for raising exact exception type, as this becomes responsibility of another function

# What to use

Consider using unittest as this is lightweight but powerful library.

# Tests structure

Tests should be placed in a 'Tests' folder, which should be a module (init.py).

Inside this folder, consider building a structure, similar to the project's structure. Remember, that for testing
bigger segments of your code (integration-testing) you can build different folders-structure as well, to reflect
your integration-testing strategy.

## Fixtures

If any of the test require some files, you should place them in a folder named 'fixtures'. There should be 1 such 
folder in the Tests folder, where all fixtures will be present, or a separate fixtures-folders in different 
sub-folders, nested in Tests.

## Entry-point

There should be a possibility to execute all tests at once, before committing any changes. This file should be present
in the Tests-root-folder. You can customize the entry-point, to fit your needs, for example:

- Adding beautiful prints with different color for different situations (test failed/succeeded)
- Measuring time for each test or overall time for all tests (or both)
- Provide a way to add new tests into automatic entry-point manually (and exclude them as well)
- Checking, if all tests are added into automatic entry-point (not to miss any tests from execution)
- etc.

# When to run tests

Tests should be executed after any changes, before each commit into production-thread. You can scip testing, if your
comment is a part of a development process.