# Project Structure

```
agent
    __init__.py
    workflow.py
config
    config.yaml
custom_logger
    __init__.py
    my_logger.py
data_ingestion
    __init__.py
    ingestion_pipeline.py
data_models
    __init__.py
    models.py
exception
    __init__.py
    exceptions.py
fallback_data  --> Incase we fail to get data from web, we will use this
    all the files will be here
notebook
    experiment.ipynb
prompt_library
    __init__.py
    prompt.py
toolkit
    __init__.py
    tools.py
utils
    __init__.py
    config_loader.py
    model_loader.py
archive.py
main.py
```
