# Sets

* Sets are a built-in data type in Python used to store collections of unique items.&#x20;
* They are unordered, meaning that the elements do not follow a specific order
* They do not allow duplicate elements.&#x20;
* Sets are useful for membership tests, eliminating duplicate entries, and performing mathematical set operations like union, intersection, difference, and symmetric difference.

```python
##create a set
my_set={1,2,3,4,5}

my_set=set([1,2,3,4,5,6]) # list to set

my_set.add(7) # if we add twice also, it wont give error, but wont add again 

my_set.remove(3) # if element is not present then it will give error
my_set.discard(11) # wont give error,even if element is not present

removed_element=my_set.pop() # returns 1st element

my_set.clear() # cleats all elements

# membership test
3 in my_set # returns True/ False

union_set=set1.union(set2) # Union
intersection_set=set1.intersection(set2) # intersection
set1.difference(set2) # difference

set1.issubset(set2) # True/False
```
