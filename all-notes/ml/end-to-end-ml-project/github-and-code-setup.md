# Github and Code Setup

* clone repo
* conda create -p venv python==3.8 -y
* conda activate venv/

**setup.py**

* Responsible to create project as a package
* find\_packages will see all the folders which are having \_\_init\_\_.py
* It will create those folders as packages
* in requirements.txt we will add -e . -> This will trigger setup.py
* When we do pip install requirements.txt -> It will see .e . -> it will create a egg.info file
* This can be used anywhere or can also be deployed on pypi

```python
from setuptools import find_packages,setup
from typing import List

HYPEN_E_DOT='-e .'
def get_requirements(file_path:str)->List[str]:
    '''
    this function will return the list of requirements
    '''
    requirements=[]
    with open(file_path) as file_obj:
        requirements=file_obj.readlines()
        requirements=[req.replace("\n","") for req in requirements]

        if HYPEN_E_DOT in requirements:
            requirements.remove(HYPEN_E_DOT)
    
    return requirements

setup(
name='mlproject',
version='0.0.1',
author='Krish',
author_email='krishnaik06@gmail.com',
packages=find_packages(),
install_requires=get_requirements('requirements.txt')

)
```
