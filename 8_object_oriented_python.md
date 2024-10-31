# Object oriented python

* An object can be a function, a variable, a property, a class… everything in Python is an object. You can think of an object as a generic container - a list object might contain a sequence of int objects, along with some function objects. The int objects contain integer numbers. The function objects contain code that can be executed on the list object or maybe on the items in the list.

```
class Car:
  runs = True

  def start(self):
    if self.runs:
      print("Car is started. Vroom vroom!")
    else:
      print("Car is broken :(")

my_car = Car()
my_car.runs = False
my_car.start()

my_other_car = Car()
my_other_car.start()

```

```
# Output
My car runs: False
Car is broken :(
Car is started. Vroom vroom!
```

## @classmethod

Static methods on a class

```
class Car:
  runs = True
  number_of_wheels = 4

  @classmethod
  def get_number_of_wheels(cls):
    return cls.number_of_wheels

  def start(self):
    if self.runs:
      print("Car is started. Vroom vroom!")
    else:
      print("Car is broken :(")

my_car = Car()
print(f"Cars have {Car.get_number_of_wheels()} wheels.")

# Of course, we can override this in our instance:
my_car.number_of_wheels = 6

# And when we access our new instance variable:
print(f"My car has {my_car.number_of_wheels} wheels.")

# But, when we call our class method on our instance:
print(f"My car has {my_car.get_number_of_wheels()} wheels.")
```

```
Cars have 4 wheels.
My car has 6 wheels.
My car has 4 wheels.
```

## type, isinstance, and subclass

```
>>> type(my_car)
<class '__main__.Car'>
>>> isinstance(42, int)
True
>>> isinstance("Hello world!", str)
True
>>> isinstance(my_car, float)
False
>>> isinstance(my_car, Car)
True
# bool is a subclass of int
>>> issubclass(bool, int)
True
# int is a subclass of object
>>> issubclass(int, object)
True
# technically, everything is a subclass of object
>>> issubclass(bool, object)
True
```

## __init__

Methods that are bracketed by underscores are sometimes called "magic methods."

__init__ is an optional constructor method that gets run when you instantiate an instance of a class.

```
class Car:
  runs = True

  def __init__(self, make, model):
    self.make = make
    self.model = model

  def start(self):
    if self.runs:
      print(f"Your {self.make} {self.model} is started. Vroom vroom!")
    else:
      print(f"Your {self.make} {self.model} is broken :(")

my_car = Car("Ford", "Thunderbird")
my_car.start()
```

## __str__ and __repr__

__str__ returns readable end-user output.
__repr__ returns the Python code necessary to rebuild the object.

```
>>> import datetime
>>> now = datetime.datetime.now()
>>> str(now)
'2019-03-16 21:04:01.396256'
>>> repr(now)
'datetime.datetime(2019, 3, 16, 21, 4, 1, 396256)'
```

```
class Car:
  def __init__(self, make, model):
    self.make = make
    self.model = model

  def __str__(self):
    return f"<<Car object: {self.make} {self.model}>>"

  def __repr__(self):
    return f"Car('{self.make}', '{self.model}')"

my_car = Car("Ford", "Thunderbird")
print(f"This object is a {str(my_car)}")
print(f"To reproduce it, type: {repr(my_car)}")
```

## Inheritance

```
class Vehicle:
  def __init__(self, make, model, fuel="gas"):
    self.make = make
    self.model = model
    self.fuel = fuel


class Car(Vehicle):
  def __init__(self, make, model, fuel="gas"):
    super().__init__(make, model, fuel)
```

```
# You'll need to import the super class when using the sub class
from vehicle import Vehicle, Car

my_car = Car("Ford", "Thunderbird")
print(f"my_car is type {type(my_car)}")
print(f"my_car uses {my_car.fuel}")

print(f"my_car is a Car: {isinstance(my_car, Car)}")
print(f"my_car is a Vehicle: {isinstance(my_car, Vehicle)}")
print(f"Car is a subclass of Vehicle: {issubclass(Car, Vehicle)}")
```

```
my_car is type <class 'vehicle.Car'>
my_car uses gas
my_car is a Car: True
my_car is a Vehicle: True
Car is a subclass of Vehicle: True
```

## Catching exceptions

### try and except

```
try:
  int("a")
except ValueError as error:
  # use 'as' to access the error variable
  print(f"Something went wrong. Message: {error}")

print("Reached end of the program.")
```

```
# Output
Something went wrong. Message: invalid literal for int() with base 10: 'a'
Reached end of the program.
```

### Exception list

* (Full list)[https://docs.python.org/3/library/exceptions.html]

### Best practices

1. Catch more specific exceptions first
2. Don't catch 'Exception' since it will catch every type of exception
3. Don't catch 'BaseException' for the same reason as 2

### Custom exceptions

Use inheritance to create custom exceptions

```
class IncorrectValueError(Exception):
...  def __init__(self, value):
...    message = f"Got an incorrect value of {value}"
...    super().__init__(message)
...
>>> my_value = 9999
>>> if my_value > 100:
...   raise IncorrectValueError(my_value)
...
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
__main__.IncorrectValueError: Got an incorrect value of 9999
```