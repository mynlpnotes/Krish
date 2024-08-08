# Polymorphism

* Allows objects of different classes to be treated as objects of a common superclass.&#x20;
* It provides a way to perform a single action in different forms.&#x20;
* Polymorphism is typically achieved through method overriding and interfaces
* It enables a single function to handle objects of different classes, each with its own implementation of a method

**Method overloading:**

* Method overriding allows a child class to provide a specific implementation of a method that is already defined in its parent class

**Abstract Base Class:**

* Abstract Base Classes (ABCs) are used to define common methods for a group of related objects.
* They can enforce that derived classes implement particular methods, promoting consistency across different implementations
* We define an abstract class by using the @abstractclass decorator

```python
## Base Class
class Animal:
    def speak(self):
        return "Sound of the animal"
    
## Derived Class 1
class Dog(Animal):
    def speak(self):
        return "Woof!"
    
## Derived class
class Cat(Animal):
    def speak(self):
        return "Meow!"
    
## Function that demonstrates polymorphism
def animal_speak(animal):
    print(animal.speak())
    
dog=Dog()
cat=Cat()
print(dog.speak()) # Woof!
print(cat.speak()) # Meow!
animal_speak(dog)  # Woof!


### Polymorphissm with Functions and MEthods
## base class
class Shape:
    def area(self):
        return "The area of the figure"
    
# Derived class 1
class Rectangle(Shape):
    def __init__(self,width,height):
        self.width=width
        self.height=height

    def area(self):
        return self.width * self.height
    
# Derived class 2
class Circle(Shape):
    def __init__(self,radius):
        self.radius=radius

    def area(self):
        return 3.14*self.radius *self.radius
    
# Fucntion that demonstrates polymorphism
def print_area(shape):
    print(f"the area is {shape.area()}")


rectangle=Rectangle(4,5)
circle=Circle(3)

print_area(rectangle)
print_area(circle)

from abc import ABC,abstractmethod

## Define an abstract class
class Vehicle(ABC):
    @abstractmethod
    def start_engine(self):
        pass

## Derived class 1
class Car(Vehicle):
    def start_engine(self):
        return "Car enginer started"
    
## Derived class 2
class Motorcycle(Vehicle):
    def start_engine(self):
        return "Motorcycle enginer started"
    
# Function that demonstrates polymorphism
def start_vehicle(vehicle):
    print(vehicle.start_engine())

## create objects of cAr and Motorcycle

car = Car()
motorcycle = Motorcycle()

start_vehicle(car)
```
