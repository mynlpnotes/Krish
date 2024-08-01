# File operation in Python

```python
# Read a whole file
with open('example.txt','r') as file:
    content=file.read()
    print(content)

# Read a file line by line
with open('example.txt','r') as file:
    for line in file:
        print(line.strip()) ## sstrip() removes the newline character

# Writing a file(Overwriting)
with open('example.txt','w') as file:
    file.write('Hello World!\n')
    file.write('this is a new line.')

## Write a file(wwithout Overwriting)
with open('example.txt','a') as file:
    file.write("Append operation taking place!\n")
    
### Writing a list of lines to a file
lines=['First line \n','Second line \n','Third line\n']
with open('example.txt','a') as file:
    file.writelines(lines)

# wb -> to write a binary file
# rb -> to read a binary file
# w+ -> to read and write a file


```
