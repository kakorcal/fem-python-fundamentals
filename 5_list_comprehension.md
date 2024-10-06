# (List comprehension)[https://practical.learnpython.dev/05_practical_applications/00_list_comprehensions/]

* A list comprehension consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. The expressions can be any kind of Python object. List comprehensions will commonly take the form of `[<value> for <vars> in <iter>]`.
* Could think if it as a map function

## Without list comprehension
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [] # empty list
>>> for name in names:
...   my_list.append(len(name))
...
>>> print(my_list)
[4, 3, 4, 5]
```

## With list comprehension
```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [len(name) for name in names]
>>> print(my_list)
[4, 3, 4, 5]
```

## With conditionals

* When expression is True, it will include it into the new list
* Could think of this as a filter function

```
>>> names = ["Nina", "Max", "Rose", "Jimmy"]
>>> my_list = [name for name in names if len(name) % 2 == 0]
>>> print(my_list)
["Nine", "Rose"]
```

## Joining into a string

```
>>> my_nums = [1,2,3]
>>> ", ".join([str(num * 2) for num in my_nums])
'2, 4, 6'
```

## Other comprehensions

* (Dictionary, generator and sets)[https://practical.learnpython.dev/05_practical_applications/10_other_comprehensions/]