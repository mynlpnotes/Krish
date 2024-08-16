# Function, Copy, Closure and Decorators

**Decorators:**

* Decorators are a powerful and flexible feature in Python that allows you to modify the behavior of a function or class method.&#x20;
* They are commonly used to add functionality to functions or methods without modifying their actual code
* Clousure means function inside functionx, we can pass function inside another funcion

```python
# Function copy
# After copying the function, even if we delete the original function, still it will 
# work
def welcome():
    return "Welcome to the advanced python course"

wel=welcome
print(wel())
del welcome
print(wel())
# Welcome to the advanced python course
# Welcome to the advanced python course

# Closure
def main_welcome(msg):   
    def sub_welcome_method():
        print("Welcome to the advance python course")
        print(msg)
        print("Please learn these concepts properly")
    return sub_welcome_method()

main_welcome("Welcome everyone")
# Welcome to the advance python course
# Welcome everyone
# Please learn these concepts properly

def main_welcome(func):
    def sub_welcome_method():
        print("Welcome to the advance python course")
        func("Welcome everyone to this tutorial")
        print("Please learn these concepts properly")
    return sub_welcome_method()
main_welcome(print)
# Welcome to the advance python course
# Welcome everyone to this tutorial
# Please learn these concepts properly

def main_welcome(func,lst):   
    def sub_welcome_method():
        print("Welcome to the advance python course")
        print(func(lst))
        print("Please learn these concepts properly")
    return sub_welcome_method()
main_welcome(len,[1,2,3,4,5])
# Welcome to the advance python course
# 5
# Please learn these concepts properly

# Decorator
def coure_introduction():
    print("This is an advanced python course")

coure_introduction()
# This is an advanced python course

main_welcome(coure_introduction)
# Welcome to the advance python course
# This is an advanced python course
# Please learn these concepts properly

@main_welcome
def coure_introduction():
    print("This is an advanced python course")
# This will call course_introduction inside main_welcome directly




```

