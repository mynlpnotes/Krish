# Encapsulation

* Encapsulation is the concept of wrapping data (variables) and methods (functions) together as a single unit
* It restricts direct access to some of the object's components, which is a means of preventing accidental interference and misuse of the data
* Protected can be used only inside the derived class
* But there are no strict rules, this are for guidelines, we can still access it

```python
### Encapsulation  with Getter and Setter MEthods
### Public,protected,private variables or access modifiers

class Person:
    def __init__(self,name,age):
        self.name=name      ## public variables
        self.age=age        ## public variables
        self.__name=name    ## private variables
        self._name=name     ## protected variables
    
    ## getter method for name
    def get_name(self):
        return self.__name
    
    ## setter method for name
    def set_name(self,name):
        self.__name=name

person=Person("Krish",34,"Male")
person.name # Krish
person.__name # will give error -> AttributeError: 'Person' 
# object has no attribute '__name'
person._name # Krish

class Employee(Person):
    def __init__(self,name,age,gender):
        super().__init__(name,age,gender)


employee._name
print(person.get_name())
```
