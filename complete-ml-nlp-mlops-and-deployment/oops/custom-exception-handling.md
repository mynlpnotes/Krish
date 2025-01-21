# Custom Exception Handling

```python
class Error(Exception):
    pass

class dobException(Error):
    pass

year = int(input("Enter DOB"))
age = 2024 - year

try:
    if age <=30 and age >=20:
        print("The age is valid for the exame")
    else:
        raise dobException
except dobException:
    print("Age is not within the required age criteria")
```
