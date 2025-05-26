# Abstraction

* Abstraction is the concept of hiding the complex implementation details and showing only the necessary features of an object. This helps in reducing programming complexity and effort
* The difference between between normal class and abstract class is that here we will be inheriting ABC
* Abstract method will be completely method
* In child class can inherit abstract class, but to use the abstract method it needs to write its own implementation
* Here we are just specifying that there is an functionality available in the form of abstract method, if any child class inherits it then it has to implement the function in its own way

```python
from abc import ABC,abstractmethod

## Abstract base cclass
class Vehicle(ABC):
    def drive(self):
        print("The vehicle is used for driving")

    @abstractmethod
    def start_engine(self):
        pass

class Car(Vehicle):
    def start_engine(self):
        print("Car enginer started")

def operate_vehicle(vehicle):
    vehicle.start_engine()
    vehicle.drive()

car=Car()
operate_vehicle(car)
```
