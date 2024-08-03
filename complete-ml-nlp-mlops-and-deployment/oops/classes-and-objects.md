# Classes and objects

* A class is a blue print for creating objects
* Using constructor we will be able to define all the attributes which will be available inside the class
* self is responsible in accessing the instance variable inside the class

```python
class Car:
    pass

audi=Car()
bmw=Car()

# We can assign value to attribute of object
# Even if we have not defined such attribute inside the class
# But this is not the correct manner of initializing object
audi.windows=4
print(audi.windows)

### Instance Variable and Methods
class Dog:
    ## constructor
    def __init__(self,name,age):
        self.name=name
        self.age=age

## create objects
## if we dont pass name and age, it will give error
dog1=Dog("Buddy",3)
print(dog1)
print(dog1.name)
print(dog1.age)

## Define a class with instance methods
class Dog:
    def __init__(self,name,age):
        self.name=name
        self.age=age
    
    def bark(self):
        print(f"{self.name} says woof")


dog1=Dog("Buddy",3)
dog1.bark()
```
