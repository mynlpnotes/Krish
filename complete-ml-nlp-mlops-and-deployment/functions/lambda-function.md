# Lambda Function

* Lambda functions are small anonymous functions defined using the **lambda** keyword.&#x20;
* They can have any number of arguments but only one expression.&#x20;
* They are commonly used for short operations or as arguments to higher-order functions.

```python
#Syntax
lambda arguments: expression

addition=lambda a,b:a+b
print(addition(5,6))

even1=lambda num:num%2==0

addition1=lambda x,y,z:x+y+z

## map()- applies a function to all items in a list
list(map(lambda x:x**2,numbers))
```
