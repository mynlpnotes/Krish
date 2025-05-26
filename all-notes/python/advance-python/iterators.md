# Iterators

* Iterators are advanced Python concepts that allow for efficient looping and memory management.
* Iterators provide a way to access elements of a collection sequentially without exposing the underlying structure.
* This uses lazy loading technique
* On 'next' it will give next element
* if there are no more elements left then it will give error
*

```python
# List
for i in my_list:
    print(i)

## Iterator
iterator=iter(my_list)
print(type(iterator))
# <class 'list_iterator'>

## Iterate through all the element
next(iterator)

try:
    print(next(iterator))
except StopIteration:
    print("There are no elements in the itera
```
