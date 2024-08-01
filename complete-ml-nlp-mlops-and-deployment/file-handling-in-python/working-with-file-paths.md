# Working with file paths

```python
os.getcwd() # get current working dirctory
os.mkdir(new_directory) # create a new directory
items=os.listdir('.') # list all files and directory
os.path.join(dir_name,file_name) # joining paths
os.path.exists(path) # check if path exists
os.path.isfile(path) # check if path is file
os.path.isdir(path)  # check if path is directory
## Getting the absolute path
relative_path='example.txt'
absolute_path=os.path.abspath(relative_path)
```
