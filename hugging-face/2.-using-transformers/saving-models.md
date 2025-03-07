# 🟢 Saving Models

```python
model.save_pretrained("directory_on_my_computer")
```

* Model gets cached in cache folder, we can also change it by changing HF\_HOME environment variable
* This saves 2 files
  * config.json
  * pytorch\_model.bin&#x20;
