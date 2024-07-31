# Getting started with functions

* A function is a block of code that performs a specific task.&#x20;
* Functions help in organizing code, reusing code, and improving readability

```python
## syntax
def function_name(parameters):
    """Docstring"""
    # Function body
    return expression

# Default parameters
def greet(name="Guest"):
    print(f"Hello {name} Welcome To the paradise")

## Positional arguments
def print_numbers(*args):
    for number in args:
        print(number)
print_numbers(1,2,3,4,5,6,7,8,"Krish")

# Keywords Arguments
def print_details(**kwargs):
    for key,value in kwargs.items():
        print(f"{key}:{value}")
print_details(name="Krish",age="32",country="India")
#name:Krish
#age:32
#country:India

### Return multiple parameters
def multiply(a,b):
    return a*b,a
multiply(2,3)
# (6,2)        
```
