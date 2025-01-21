# Inheritance

* Inherit attributes and methods from another class
* Child class will inherit from parent class, and not vice versa
* While delcaring the child class, we need to pass parent class name
* class child\_class (parent\_class):
* The constructor of child class should also take the parameters of constructor of parent class
* It should 1st take the parameters of constructor of parent class and then parameters of self
* Use keyword super to call method or attribute of parent class from child class
* super().**init**(windows,doors,enginetype)
* Incase of multiclass inheritance, we need to use the class name instead of super

```python
## Single inheritance
## Parent class
class Car:
    def __init__(self,windows,doors,enginetype):
        self.windows=windows
        self.doors=doors
        self.enginetype=enginetype
    
    def drive(self):
        print(f"The person will drive the {self.enginetype} car ")

# Child class
class Tesla(Car):
    def __init__(self,windows,doors,enginetype,is_selfdriving):
        super().__init__(windows,doors,enginetype)
        self.is_selfdriving=is_selfdriving

    def selfdriving(self):
        print(f"Tesla supports self driving : {self.is_selfdriving}")

tesla1=Tesla(4,5,"electric",True)
tesla1.selfdriving()
tesla1.drive()

## Multi class inheritance
## When a class inherits from more than one base class.
## Base class 1
class Animal:
    def __init__(self,name):
        self.name=name

    def speak(self):
        print("Subclass must implement this method")

## BAse class 2
class Pet:
    def __init__(self, owner):
        self.owner = owner


##Derived class
class Dog(Animal,Pet):
    def __init__(self,name,owner):
        Animal.__init__(self,name)
        Pet.__init__(self,owner)

    def speak(self):
        return f"{self.name} say woof"
    

## Create an object
dog=Dog("Buddy","Krish")
print(dog.speak())
print(f"Owner:{dog.owner}")
```
