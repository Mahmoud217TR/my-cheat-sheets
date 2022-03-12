# Lists

**Table of Contents:**
* [Creating lists](#creating-lists)
* [List Indexes](#list-indexes)
* [List Count](#list-count)
* [List Length](#list-length)
* [List Appending](#list-appending)
* [List Inserting](#list-inserting)
* [Sorting Lists](#sorting-lists)
* [Unpacking Lists](#unpacking-lists)


## Creating lists

You Can create lists just by using `[]` or the constructor `list()`:

```python
l1 = [1, 2, 3]	# List contains the values 1, 2, 3

l2 = ['a', 'b', 'c', 'd'] # List contains the values a, b, c, d

l3 = [1, 'a', True, 'Hi'] # List contains the values 1, a, True, Hi

l4 = list() # Empty list
```


## List Indexes

Similar to the string indexes:

```python
myList = [1, 2, 3, 4, 5]

print(myList[0]) # prints 1
print(myList[2]) # prints 3

print(myList[-1]) # prints 5
print(myList[-2]) # prints 4

print(myList[:3]) # prints [1, 2, 3, 4]
print(myList[2:]) # prints [3, 4]  

print(myList[1:3]) # prints [2, 3, 4]

print(myList[:-1]) # prints [1, 2, 3, 4]
```


## List Count

To count items in list:

```python
myList = ['a', 1, 'c', 1, '1', 'hello']

print(myList.count(1)) # Prints 2
print(myList.count('1')) # Prints 1
print(myList.count('a')) # Prints a
```


### List Length

Length is the number of items in the list:

```python
myList = [10, 20, 30, 40]
print(len(myList)) # prints 4
```


## List Appending

To append items or other list to the end of the list:

```python
myList = ['a']

myList.append(1) # myList value is ['a', 1]
myList.append(True) # myList value is ['a', 1, True]

myList.append([1, False, "Hi"]) # myList value is ['a', 1, True, [1, False, "Hi"]]
```


## List Inserting

To insert items or other list to a dedicated position in the list:

```python
myList = [1, 2, 3, 'a', True]

myList.insert(0,6) # myList value is [6, 1, 2, 3, 'a', True]
myList.insert(6,"Hi") # myList value is [6, 1, 2, 3, 'a', True, "Hi"]

myList.insert(4,[4,5]) # myList value is [6, 1, 2, 3, [4,5], 'a', True, "Hi"]
```

## Sorting Lists

To sort a list:

```python 
myList = [1,5,1,3,2,7,9,8,5]

mySortedList = sorted(myList) # myList value [1,5,1,3,2,7,9,8,5], mySortedList value [1,1,2,3,5,5,7,8,9]

myList.sort() # myList value [1,1,2,3,5,5,7,8,9]
```

## Unpacking Lists

The number of variables must be the same as the number of elements in the list:

```python
myList = [1,'a',True]
a,b,c = myList  # a = 1 , b = 'a' , c = True
```