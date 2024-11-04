# Libraries and modules

## The main method

The purpose of checking for the main method is to make sure that the code in your main method is only run when it’s executed as a stand-alone program. Because of how Python’s import system works, if someone else imports your Python program, any code in it is executed on import.

__name__ is a special variable that’s set by Python that tells it where it was called from. We can tell it’s a special variable because it starts and ends with __. That’s a hint that you don’t want to change the value of this variable, or it could adversely affect the execution of your Python program.

To avoid running our code when it’s imported by other modules, we put it in a conditional statement, and explicitly check if __name__ == "__main__".

```
# name_lib.py

def name_length(name):
    return len(name)

def upper_case_name(name):
    return name.upper()

def lower_case_name(name):
    return name.lower()

if __name__ == "__main__":
    name = "Nina"
    length = name_length(name)
    upper_case = upper_case_name(name)

    print(f"The length is {length} and the uppercase version is: {upper_case}")
```

## Virtual environment

Virtual environments are a handy way to store the dependencies your Python application requires. Creating a virtual environment makes a self-contained folder that includes a full Python installation, allowing you to install dependencies specific to your application (or even a specific version of Python if you want) without relying on the global system version of Python.

### requirements.txt

requirements.txt is a special file that we use to tell pip, the Python package manager, which dependencies to install. The format is simple: you can create one manually by putting each dependency you import into a text file named requirements.txt, one dependency on each line.

Alternatively, you can install each dependency in your virtualenv using pip. Once you’re done (your application stops complaining about missing imports), you can run:

```
pip freeze > requirements.txt
```

This will automatically generate a requirements.txt file for you, using the specific version of each dependency you installed in your virtualenv.

Later on, when you move your Python application to a new virtualenv, a new computer, or deploy it to the world, you can bring all your dependencies with you with requirements.txt. To install all your requirements again in a new virtual environment you can simply run:

```
pip install -r requirements.txt
```

## Install libraries with pip

```
python -m pip install <SOME_LIB>
```

## PYTHONPATH

This is a list of paths on your system where Python will look for packages. Python will always look first in the working directory (the folder you’re in when you start the REPL or run your program), so if your module folder is there, you can import it. You can also install your modules just like any other external modules, using a setup.py file. It’s also possible to change or add paths to your PYTHONPATH list if you need to store modules elsewhere, but this isn’t a very portable solution.

## Unit testing

https://practical.learnpython.dev/07_programs_libraries_modules/55_tests/

unittest is both a framework for writing tests, as well as a test runner, meaning it can execute your tests and return the results.

```
import unittest

def multiply(x, y):
  return x * y

class TestMultiply(unittest.TestCase):

  def test_multiply(self):
    test_x = 5
    test_y = 10
    self.assertEqual(multiply(test_x, test_y), 50, "Should be 50")

if __name__ == "__main__":
  unittest.main()
```

Standard unittest tests are fine for most projects. As your programs grow and organization becomes more complex, you might want to consider an alternative testing framework or test runner. The 3rd party nose2 and pytest modules are compatible with unittest but do things slightly differently
