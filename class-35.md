# Pythonisms

## [Dunder Methods](https://dbader.org/blog/python-dunder-methods)

## What Are Dunder Methods?

In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example ```__init__``` or ```__str__```.

As it quickly became tiresome to say under-under-method-under-under Pythonistas adopted the term “dunder methods”, a short form of “double under.”

These “dunders” or “special methods” in Python are also sometimes called “magic methods.” But using this terminology can make them seem more complicated than they really are—at the end of the day there’s nothing “magical” about them. You should treat these methods like a normal language feature.

Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string').

## Special Methods and the Python Data Model

This elegant design is known as the Python data model and lets developers tap into rich language features like sequences, iteration, operator overloading, attribute access, etc.

## Enriching a Simple Account Class

- Initialization of new objects
- Object representation
- Enable iteration
- Operator overloading (comparison)
- Operator overloading (addition)
- Method invocation
- Context manager support (with statement)

# [Iterators](https://dbader.org/blog/python-iterators)

```
Objects that support the __iter__ and __next__ dunder methods automatically work with for-in loops.
```

# [Generators](https://dbader.org/blog/python-generators)

## What Are Python Generators?

**Generators** are a tricky subject in Python. With this tutorial you’ll make the leap from class-based iterators to using generator functions and the “yield” statement in no time.
