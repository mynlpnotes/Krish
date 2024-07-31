# List and List comprehension

* Ordered mutable collection of items (Mutable means they can be changed)
* They can contain items of different data types

```python
# Delcaring a list
lst=[]

# Items of mixed data type
names=["Krish","Jack","Jacob",1,2,3,4,5]

# Accessing list elements
fruits[2]
fruits[1:]
fruits[1:3]

# Modifying list items
fruits[1]="watermelon"

# Modifying list
fruits.append("orange") ## Add an item to the end
fruits.insert(1,"watermelon")
fruits.remove("banana") ## Removing the first occurance of an item

popped_fruits=fruits.pop() ## Remove and return the last element # orange

index=fruits.index("cherry") # 3
fruits.count("banana") # 2

fruits.sort() ## Sorts the list in ascending order
fruits.reverse() ## Reverse the list
fruits.clear() ## Remove all items from the list

# Slicing list
print(numbers[2:5])
print(numbers[:5])
print(numbers[5:])
print(numbers[::2])
print(numbers[::-1])

numbers[::3] # This will take every 3rd element
numbers[::-2] # This will take every 2nd element from last

# Iterating over list
for number in numbers:
    print(number)
    
for index,number in enumerate(numbers):
    print(index,number)

# List comprehension
sqaure=[num**2 for num in range(10)] # Basic list comprehension
even_numbers=[num for num in range(10) if num%2==0] # with condition
pair=[[i,j] for i in lst1 for j in lst2] # Nested
lengths = [len(word) for word in words] # with function calls
```
