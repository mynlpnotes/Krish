# Dictionaries

* Dictionaries are unordered collections of items.&#x20;
* They store data in key-value pairs.&#x20;
* Keys must be unique and immutable (e.g., strings, numbers, or tuples)
* While values can be of any type.

```python
empty_dict={}
empty_dict=dict()

student={"name":"Krish","age":32,"grade":24}

# Accessing elements
student['grade']
student['age']
student.get('last_name',"Not Available") # if element is not available then return 'Not Available'

student["age"]=33  ##update value for the key
student["address"]="India" ## added a new key and value

del student['grade'] ## delete key and value pair
keys=student.keys() ##get all the keys
items=student.items() ##get all key value pairs

# shallow copy
# if we change any value in student, then it will reflect in student_copy as well
student_copy=student

student_copy1=student.copy() # deep copy

# iterating
for keys in student.keys():
    print(keys)

for value in student.values():
    print(value)

for key,value in student.items():
    print(f"{key}:{value}")

## Dictionary Comphrehension
squares={x:x**2 for x in range(5)}
evens={x:x**2 for x in range(10) if x%2==0}







```
