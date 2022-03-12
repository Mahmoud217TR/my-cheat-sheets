# Dictionaries in Python

**Table of Contents:**
* [Creating a Dictionary](#creating-a-dictionary)
* [Getting value from Dictionary](#getting-value-from-dictionary)

## Creating a Dictionary

```python
myDict = {
    Key1 : Value1,
    Key2 : Value2,
    Key3 : Value3
}

myDict = dict()
```
The Keys should be Unique and case senstive


## Getting value from Dictionary

```python
myDict = {'Name' : 'Mahmoud',
        'Age' : 21,
        1 : True,
        2 : False}

print(myDict.get('Name'))   # Prints Mahmoud
print(myDict.get('Age'))    # Prints 21
print(myDict.get(1))    # Prints True
print(myDict.get(2))    # Prints False

print(myDict.get('Birthdate'))  # Prints None
print(myDict.get(3))    # Prints None

print(myDict.setdefault(3,1))   # Prints 1 (Because 1 is a Default Value)
print(myDict.get(3,'Hi'))   # Prints Hi (Because Hi is a Default Value)
```