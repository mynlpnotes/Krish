# Loops in Python

1. for Loop
   * Iterating over a range
   * Iterating over a string
2. while Loop
3. Loop Control Statements
   * break
   * continue
   * pass
4. Nested Loops

* break exits the loop
* continue skips the current itteration and continues with the next

```python
for i in range(5):
    print(i) # 0....4

for i in range(1,6):
    print(i) # 1....5

for i in range(1,10,2):
    print(i)  # 1 3 5 7 9

for i in range(10,1,-1):
    print(i) # 10 9 ....2

str="Krish Naik"

name = 'Hitesh'
for i in name:
    print(i) # H i t e s h

while count<5:
    print(count)
    count=count+1

for i in range(10):
    if i==5:
        break
    print(i)

for i in range(10):
    if i%2==0:
        continue
    print(i)
    
for i in range(3):
    for j in range(2):
        print(f"i:{i} and j:{j}")
```
