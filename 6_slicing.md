# Slicing

* Slicing is a easy way to create sub-lists from larger lists. We can use a slice to obtain a subset of items from a list. Remember that a string is just a list of characters.

```
>>> my_string = "Hello, world!"
>>> my_string[7:12] # from 7 to 12
'world'
```

## Lopsided slicing

* You can also leave out one of the numbers in the slice. Leaving out the first number is equivalent to using a zero - you can think of this as “from the beginning.” Leaving out the last number is equivalent to using the length of the list you’re slicing - you can think of this as “until the end.”

```
>>> my_string = "Hello, world!"
>>> my_string[:5] # from zero to 5
'Hello'
>>> my_string[7:] # from 7 to the end
'world!'
>>> # Easy way to copy a string is by slicing from beginning to end
>>> my_new_string = my_string[:]
>>> my_new_string
'Hello, world!'
>>> # Negative indexing
>>> my_string[-1]
'!'
```