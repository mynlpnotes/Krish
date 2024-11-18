# Get File Size

```python
import os

def print_file_size(file):

    File_Size = os.path.getsize(file) # returns bytes
    File_Size_KB = round(File_Size/1024,4)

    print("Image File Size is " + str(File_Size_KB) + "KB" )
```
