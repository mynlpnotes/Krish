# Variables in Python

* Used to store data that can be referenced and manipulated at run time
* Created when value initiated
* No need for declaration
* Data type can change dynamically

**Naming convention:**

* Should be descriptive
* Always start with a letter or \_
* Can contain number, letter and \_ in name
* Case sensitive

```python
# Declaring and assigning variables
age = 32

print("age:",age)

# Type converison
age_str = str(age) # '32'
age = int(age_str) # 32
age_float = float(age)

# input 
age = input('Enter age')
# Here data type of age will be str
# So we will have to change it, to use it
```
