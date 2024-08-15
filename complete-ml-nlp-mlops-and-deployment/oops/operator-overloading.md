# Operator Overloading

* Operator overloading allows you to define the behavior of operators (+, -, \*, etc.) for custom objects.
* You achieve this by overriding specific magic methods in your class.

```python
#### Common Operator Overloading Magic Methods
'''
__add__(self, other): Adds two objects using the + operator.
__sub__(self, other): Subtracts two objects using the - operator.
__mul__(self, other): Multiplies two objects using the * operator.
__truediv__(self, other): Divides two objects using the / operator.
__eq__(self, other): Checks if two objects are equal using the == operator.
__lt__(self, other): Checks if one object is less than another using the < operator.

__gt__
'''

class Vector:
    def __init__(self,x,y):
        self.x=x
        self.y=y

    def __add__(self,other):
        return Vector(self.x+other.x,self.y+other.y)
    
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)

    def __mul__(self, other):
        return Vector(self.x * other, self.y * other)
    
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"
    
## create objectss of the Vector Class
v1=Vector(2,3)
v2=Vector(4,5)

print(v1+v2)
print(v1-v2)
print(v1*3)
# Vector(6, 8)
# Vector(-2, -2)
# Vector(6, 9)
```
