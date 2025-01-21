# Project structure, logging and exception handling

**Project Structure:**

* PROJECT\_NAME
  * &#x20;src
    * \_\_init\_\_.py
    * logger.py
    * exception.py
    * utils.py
    * pipeline
      * \_\_init\_\_.py
      * train\_pipeline.py
      * predict\_pipeline.py
    *   components

        * \_\_init\_\_.py
        * data\_ingestion.py
        * data\_transformation.py
        * model\_trainer.py


* exception.py

```python
import sys
from src.logger import logging

def error_message_detail(error,error_detail:sys):
    _,_,exc_tb=error_detail.exc_info()
    file_name=exc_tb.tb_frame.f_code.co_filename
    error_message="Error occured in python script name [{0}] line number 
                    [{1}] error message[{2}]".format(
     file_name,exc_tb.tb_lineno,str(error))

    return error_message

class CustomException(Exception):
    def __init__(self,error_message,error_detail:sys):
        super().__init__(error_message)
        self.error_message=error_message_detail(error_message,
                error_detail=error_detail)
    
    def __str__(self):
        return self.error_message
# Output: Error occur in python script <<>> line number <<>> error message <<>>
```



* logger.py

```python
import logging
import os
from datetime import datetime

LOG_FILE=f"{datetime.now().strftime('%m_%d_%Y_%H_%M_%S')}.log"
logs_path=os.path.join(os.getcwd(),"logs",LOG_FILE)
os.makedirs(logs_path,exist_ok=True)

LOG_FILE_PATH=os.path.join(logs_path,LOG_FILE)

logging.basicConfig(
    filename=LOG_FILE_PATH,
    format="[ %(asctime)s ] %(lineno)d %(name)s - %(levelname)s - %(message)s",
    level=logging.INFO,
)

# File name - DD_MM_YYYY_HH_MM_SS.log
# Log structure:
# YYYY-MM-DD HH:MM:SS <<line number>>  <<script>>  <<level>>  <<log message>>
```
