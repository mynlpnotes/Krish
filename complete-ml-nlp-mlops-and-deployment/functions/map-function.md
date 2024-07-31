# Map Function

* The map() function applies a given function to all items in an input list (or any other iterable) and returns a map object (an iterator).&#x20;
* This is particularly useful for transforming data in a list comprehensively.

```python
# Basic example
numbers=[1,2,3,4,5,6,7,8]
list(map(square,numbers)) # in arguments, we have to pass function and then list

# Lambda function with map
list(map(lambda x:x*x,numbers))

# Map multiple iterables
numbers1=[1,2,3]
numbers2=[4,5,6]
added_numbers=list(map(lambda x,y:x+y,numbers1,numbers2))

int_numbers = list(map(int, str_numbers)) # list of string to string of int

upper_word=list(map(str.upper,words)) # convert to upper case


```
