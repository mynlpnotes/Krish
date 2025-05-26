# Importing Creating Modules and Packages

* To create a custom package, we create a folder
* and inside it we create \_\_init\_\_.py&#x20;
* Then this module can be called inside other scripts in the same project
* \_\_init\_\_.py is a special file to define package and initialize their namespaces
* Sub package import is when inside a package we have one more package

```python
import math
math.sqrt(16) #4

from math import sqrt, pi
print(sqrt(16)) #4
print(pi) #3.14

import numpy as np # here np is alias
#pip install numpy # if module is not already installed

from math import *
sqrt(25)

# to import subpackage
from package.subpackage.mult import *



```
