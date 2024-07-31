# Tuples

* Tuples are ordered collections of items that are immutable.&#x20;
* They are similar to lists, but their immutability makes them different.

```python
empty_tuple=() # Create a tuple
lst=list()     # List
tpl=tuple()    # Tuple

numbers=tuple([1,2,3,4,5,6]) # List to tuple
list((1,2,3,4,5,6))          # tuple to list

# Remaining slicing operations will be same as list

concatenation_tuple=numbers + mixed_tuple  # Concatenate 2 lists
mixed_tuple * 3 # same contents will be repeated thrice

numbers[1]="Krish" # Will give error as elements cannot be changed

##unpacking a tuple
a,b,c=packed_tuple

## Unpacking with *
numbers=(1,2,3,4,5,6)
first,*middle,last=numbers 
# 1
# [2, 3, 4, 5]
# 6

# Nested tuple
nested_tuple = ((1, 2, 3), ("a", "b", "c"), (True, False))
print(nested_tuple[0])
print(nested_tuple[1][2])
```
