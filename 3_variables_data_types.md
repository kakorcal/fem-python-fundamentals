# Helpful REPL methods

1. `type`

```
>>> num = 42
>>> type(42)
<class 'int'>
>>> type([])
<class 'list'>
```

2. `dir`

```
>>> dir(int)
['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__', 'as_integer_ratio', 'bit_count', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 'numerator', 'real', 'to_bytes']
```

3. `help`

```
>>> help(int)
>>> help(str.isalpha)
Opens documentation
```

# All types are class objects

Constructors can be called for that class.
NOTE: not recommended. Only do this if you are converting between types

```
>>> int(5)
5
>>> int('5')
5
>>> float(3)
3.0
>>> bool(-1)
True
```

# Math operators

* Float division
```
>>> 25 / 5
5
```

* Integer division
```
>>> 25 // 5
5
```

* Powers
```
>>> 4 ** 3
64
```

# Strings

* Long strings
```
>>> a_long_string = """
... my
... long
... string
... """
>>> a_long_string
'\nmy\nlong\nstring\n'
>>> print(a_long_string)
my
long
string
```

* f strings (formatted strings)
```
>>> num = 5
>>> f"hi {num}"
'hi 5'
>>> print(f"hi {num}")
hi 5
```

# Lists

* NOTE: lists can be mutated with their methods or reassignment

```
>>> names = ['nina', 'max', 'jane']
>>> len(names)
3
>>> names[0]
'nina'
>>> names[0] = 'mark'
>>> names
['mark', 'max', 'jane']
>>> sorted(names)
['jane', 'mark', 'max']
>>> names
['mark', 'max', 'jane']
>>> names.sort()
>>> names
['jane', 'mark', 'max']
```

* List concat (non mutating)

```
>>> nums = [1,2,3]
>>> nums + [4,5,6]
[1,2,3,4,5,6]
>>> nums
[1,2,3]
```

* Search

```
>>> nums = [11,22,33]
>>> 22 in nums
True
```