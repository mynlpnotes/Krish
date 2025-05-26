# Try, except and finally

* Exception handling in Python allows you to handle errors gracefully and take corrective actions without stopping the execution of the program
* Exceptions are events that disrupt the normal flow of a program

```python
## Exception try ,except block
try:
    a=b
except:
    print("The variable has not been assigned")

## Using excpetion type
try:
    a=b
except NameError as ex:
    print(ex)

## we can use except Exception as ex -- this is the base class for all exceptions

## try,except,else and finally
# if there is no excpetion then else block will be executed
# if exception or no exception still finally will be executed
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("You can't divide by zero!")
except Exception as ex:
    print(ex)
else:
    print(f"The result is {result}")
finally:
    print("Execution complete.")
```
