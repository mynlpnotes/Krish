# Approaches for uploading file to the hub

* git for regular files, and git-lfs (which stands for [Git Large File Storage](https://git-lfs.github.com/)) for larger files.

1. upload\_file:

* Directly pushes to the push using https post
* Limitation is of 5GB

```python
from huggingface_hub import upload_file

upload_file(
    "<path_to_file>/config.json",
    path_in_repo="config.json",
    repo_id="<namespace>/dummy-model",
)
```

2. Using the Repository class

* Clone the repo using repository class and then start making changes
* git commit using repo class

2. The git-based approach
