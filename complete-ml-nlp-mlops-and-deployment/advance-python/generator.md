# Generator

* Generators are a simpler way to create iterators.&#x20;
* They use the yield keyword to produce a series of values lazily, which means they generate values on the fly and do not store them in memory
* We use yield keyword here
* Generators are particularly useful for reading large files because they allow you to process one line at a time without loading the entire file into memory.

```python
def square(n):
    for i in range(3):
        yield i**2

square(3)
# generator object square at 0x00000222FFEFF2A0>

for i in square(3):
    print(i)
# This will print 0 1 4

a=square(3)
next(a)

## Practical : Reading LArge Files
def read_large_file(file_path):
    with open(file_path,'r') as file:
        for line in file:
            yield line

file_path='large_file.txt'

for line in read_large_file(file_path):
    print(line.strip())
```
