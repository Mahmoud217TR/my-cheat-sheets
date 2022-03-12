# Python Tuples

**Table of Contents:**
* [Tuples](#tuples)
* [Creating Tuples](#creating-tuples)
* [Tuples Indexes](#tuples-indexes)
* [Tuples Count](#tuples-count)


## Tuples
- You can't change tuple values.
- You can use iterate & count tuples items.
- Can contain different types of values.


## Creating Tuples

```python
myTuple = ('a',1,True,'Hi')
```

## Tuples Indexes

Similar to the list indexes:

```python
myTuple = (1, 2, 3, 4, 5)

print(myTuple[0]) # prints 1
print(myTuple[2]) # prints 3

print(myTuple[-1]) # prints 5
print(myTuple[-2]) # prints 4

print(myTuple[:3]) # prints [1, 2, 3, 4]
print(myTuple[2:]) # prints [3, 4]  

print(myTuple[1:3]) # prints [2, 3, 4]

print(myTuple[:-1]) # prints [1, 2, 3, 4]
```

## Tuples Count

To count items in tuple:

```python
myTuple = ('a', 1, 'c', 1, '1', 'hello')

print(myTuple.count(1)) # Prints 2
print(myTuple.count('1')) # Prints 1
print(myTuple.count('a')) # Prints a
```