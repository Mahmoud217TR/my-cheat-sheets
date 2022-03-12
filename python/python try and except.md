# Try & Except in Python

**Table of Contents:**
* [Try & Except Syntax](#try--except-syntax)
* [Finally](#finally)
* [Exception Types](#exception-types)


## Try & Except Syntax

We use try for a code that could make an error at runtime to handle it:

```python
try:
    # Your Code
except:
    # If any exception accord how to handle it
```

You can specify the exeption like so:

```python
try:
    # Your Code
except ZeroDivisionError:
    # Only works if  the exception is (ZeroDivisionError)
```


## Finally

The keyword `finally` is to run some block of code if your code works or it didn't:

```python
try:
    # Your Code
except:
    # If any exception accord how to handle it
finally:
    # Works always
```


## Exception Types

Some Popular exceptions to use:
* ValueError
* ZeroDivisionError
* AttributeError
* TypeError