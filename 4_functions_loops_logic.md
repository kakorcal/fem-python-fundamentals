# Tuples

## Properties
* Tuples are immutable as opposed to lists
* Tuples need a trailing comma if there is only one item
```
>>> my_tup = ()
>>> type(my_tup)
<class 'tuple'>
>>> my_tup = ("hi")
>>> type(my_tup)
<class 'str'>
>>> my_tup = ("hi",)
>>> type(my_tup)
<class 'tuple'>
```

* Tuple unpacking
```
>>> student = ('marcy', 8, 'history')
>>> # underscore will discard the variable
>>> name, _, subject = student
```

# Sets

## Properties

* Sets are mutable but store unique immutable value and unsorted
```
>>> # For creating empty sets you need to use the constructor
>>> type(set())
>>> <class 'set'>
>>> type({3})
>>> <class 'set'>
>>> my_set = {3,3,4}
>>> my_set
{3,4}
```

* You can dedup lists with a set constructor
```
>>> names = ['Nina', 'Nina', 'Max']
>>> sets(names)
{'Max', 'Nina'}
```

# Hash

* Shortcut to check if type mutability. Only immutable types are hashable

```
>>> hash(5)
5
>>> hash([])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

# Dictionary

* Key value pairs. Values are mutable but keys are immutable
```
>>> type({})
<class 'dict'>
>>> my_dict = {"one": 1, "two": 2}
```

* Get with default value
```
>>> my_dict = {"one": 1, "two": 2}
>>> my_dict.get("three", "my default")
'my default'
```

* Looping over dictionaries - use my_dict.items() method to get both key and value

```
>>> my_dict.items()
dict_items([('one', 1), ('two', 2)])
```

# `*.pyc` files

* For optimization and other reasons, Python code can be compiled to intermediary .pyc files. The good news is you don’t have to worry about them. The bad news is, very occasionally stale versions of these compiled files can cause problems. To safely delete them from the current project directory, run find . -name "*.pyc" -delete (on linux or macOS). Add these files to gitignore

# pretty print `pprint`

* Available in standard lib

```
>>> from pprint import pprint
```

# Functions

* Don't use mutable types as default arguments - only one instance is initialized

```
>>> def do_stuff(my_list=[]):
...   my_list.append('hi')
...   return my_list
...
>>> do_stuff()
['hi']
>>> do_stuff()
['hi', 'hi']
```

* Solution to above will be to use `None` as a placeholder
```
>>> def do_stuff(my_list=None):
...   if my_list == None:
...     my_list = []
...     my_list.append('hi')
...   return my_list
...
```

* You can't reassign outer variable values within a function

```
>>> name = 'Nina'
>>> def change_name():
...   name = 'Max'
...   print(f"name in function: {name}")
...
>>> change_name()
name in function: Max
>>> name
Nina
```

# Boolean

* bool constructor can evaluate expressions

```
>>> bool(3 > 5)
False
>>> bool([])
False
```

* Equality for mutable types checks values and not reference

```
>>> list1 = [1,2,3]
>>> list2 = [1,2,3]
>>> list1 == list2
True
```

* For checking for reference equality, use the `is` keyword
* Don't use == for checking truthyness

```
>>> list1 = [1,2,3]
>>> list2 = [1,2,3]
>>> list1 is list2 # do these point to same place in memory?
False
>>> x = None
>>> x is None
True
>>> [] is None
False
>>> a = True
>>> a is True
```

# Operators

* Keywords: `and`, `or`, `not`

```
>>> True and (True or False)
True
>>> if [1,2]:
...   print('hi')
...
hi
```

* Don't equality check booleans!

```
>>> 3 < 5 == True
False
```

# Loops

## Using `in` keyword

```
>>> colors = ["red", "blue", "green"]
>>> for color in colors:
...   print(color)
...
```

## Using `range`

```
>>> for num in range(3, 7):
...   print(num)
...
```

## Using `enumerate`

```
>>> # Makes index accessible with tuple unpacking
>>> colors = ["red", "blue", "green"]
>>> for index, color in enumerate(colors)
...   print(f"{index}: {color}")
...
```

## Looping over dictionaries

```

>>> hex_colors = {
...   "Red": "#FF0000",
...   "Green": "#008000",
...   "Blue": "#0000FF",
... }
...
>>> # Only the key is accessible when looping
>>> for key in hex_colors:
...   print(key)
...
>>> # Makes value accessible with tuple unpacking
>>> for key, value in hex_colors.items():
...   print(f"{key} {value}")
...
```

## Listify enumerates

```
>>> colors = ["red", "blue", "green"]
>>> list(enumerate(colors))
[(0, 'red'), (1, 'blue'), (2, 'green')]
```
