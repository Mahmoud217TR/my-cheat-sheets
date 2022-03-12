# Strings in Python

**Table of Contents:**
* [Using Math Exepressions](#using-math-exepressions)
* [String Formatting](#string-formatting)
* [String Indexes](#string-indexes)
* [Appending on String](#appending-on-string)
* [The in keyword with strings](#the-in-keyword-with-strings)
* [Count Characters in string](#count-characters-in-string)
* [Spliting a string](#spliting-a-string)
* [String Length](#string-length)


## Using Math Exepressions

You can use mathmatical expressions to help you print:

```python
print('X' * 10) # Prints XXXXXXXXXX
```
	
## String Formatting

Formatting Strings:

```python
y = 'Welcome'
first = 'Ahmad'
last = 'Ali'

print(f'{y} my Friend') # Prints Welcome my Friend

print('the Value of x is {}'.format(x)) # Prints the Value of x is 10

print('{} my Friend {} {}!!').format(y,first,last) # Prints Welcome my Friend Ahmad Ali!!

print(f'{y} my Friend {first} {last}!!') # Prints Welcome my Friend Ahmad Ali!!
```
	
## String Indexes

Python Indexes:

```python
string = 'Welcome'

print(string[0]) # Prints W
print(string[2]) # Prints l

print(string[-1]) # Prints e
print(string[-2]) # Prints m

print(string[:4]) # Prints Welc 
print(string[2:]) # Prints lcome

print(string[1:4]) # Prints elc

print(string[:-1]) # Prints Welcom
```

## Appending on String

To append characters or other strings to a string:

```python
string = 'a'
string.append('b') # string value is ab
string.append('c') # string value is abc
```

## The `in` keyword with strings

To check if the string contains a word or character:

```python
string = "012345"
'6' in string # returns False
'1' in stzring # returns True
```

## Count Characters in string

To count characters in string:

```python
string = 'abbabab'
print(string.count('a')) # Prints 3
print(string.count('b')) # Prints 4
print(string.count('c')) # Prints 0
```

## Spliting a string

You can spilt a string to a **list** of substrings:

```python
string = "Hello and Good Morning"
words = string.split(' ')
print(words) # Prints ['Hello','and','Good','Morning']
```

## String Length

Length is the number of characters in the string:

```python
string = 'Hello'
print(len(string)) # prints 5
```