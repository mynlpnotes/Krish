# huggingface hub python library

* It provides simple APIs that work on top of git to manage those repositories’ content and to integrate the Hub in your projects and libraries
* It also required auth token
* Create repo

```python
from huggingface_hub import create_repo

create_repo("dummy-model")
```

* Other arguments which may be useful are:
  * `private`, in order to specify if the repository should be visible from others or not.
  * `token`, if you would like to override the token stored in your cache by a given token
  * `repo_type`, if you would like to create a `dataset` or a `space` instead of a model. Accepted values are `"dataset"` and `"space"`.
* Once repo is created we can add files to it
