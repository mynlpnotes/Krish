# Magic Methods

* Magic methods in Python, also known as dunder methods (double underscore methods), are special methods that start and end with double underscores.&#x20;
* These methods enable you to define the behavior of objects for built-in operations, such as arithmetic operations, comparisons, and more

```python
'''
__init__': Initializes a new instance of a class.
__str__: Returns a string representation of an object.
__repr__: Returns an official string representation of an object.
__len__: Returns the length of an object.
__getitem__: Gets an item from a container.
__setitem__: Sets an item in a container.
'''

## Basics MEthods
class Person:
    def __init__(self,name,age):
        self.name=name
        self.age=age
person=Person("KRish",34)
print(person)
# <__main__.Person object at 0x0000029E5D31D4C0>

## Basics MEthods
class Person:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    
    def __str__(self):
        return f"{self.name},{self.age} years old"
    
    def __repr__(self):
        return f"Person(name={self.name},age={self.age})"
    
person=Person("KRish",34)
print(person)
print(repr(person))
# KRish,34 years old
# Person(name=KRish,age=34)
```
