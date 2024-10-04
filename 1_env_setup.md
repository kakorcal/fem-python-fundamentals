# Env setup

## Virtual env

A [Virtual Environments](https://dev.to/joeljuca/til-python-virtual-environments-and-venv-c8e) in Python is a self-contained directory that contains a Python installation for a particular version of Python. It tricks both Python and pip to install and load packages into a local directory (aka.: your project's directory) instead of global-wide or user-wide directories. It allows you to work on different projects with the same dependencies but different versions without conflicts.

Read difference on [different env packages](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe)

```
$ python3 -m venv <ENV_NAME>
$ source <ENV_NAME>/bin/activate
```

More ways to [create envs](https://www.freecodecamp.org/news/python-virtual-environments-explained-with-examples/)

Difference between [virtual env and npm](https://stackoverflow.com/questions/59444346/is-npm-in-node-like-virtualenv-in-django)

## Upgrade pip

```
python3 -m pip install --upgrade pip
```
