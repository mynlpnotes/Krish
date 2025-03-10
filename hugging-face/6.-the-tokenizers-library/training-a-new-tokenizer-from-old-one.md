# Training a new tokenizer from old one

* Training a tokenizer is not the same as training a model! Model training uses stochastic gradient descent to make the loss a little bit smaller for each batch.&#x20;
* It’s randomized by nature (meaning you have to set some seeds to get the same results when doing the same training twice).&#x20;
* Training a tokenizer is a statistical process that tries to identify which subwords are the best to pick for a given corpus, and the exact rules used to pick them depend on the tokenization algorithm.&#x20;
* It’s deterministic, meaning you always get the same results when training with the same algorithm on the same corpus.
* We can use the API - AutoTokenizer.train\_new\_from\_iterator()
* We define a function that returns a generator
* We won’t have to specify anything about the tokenization algorithm or the special tokens we want to use; our new tokenizer will be exactly the same as GPT-2, and the only thing that will change is the vocabulary, which will be determined by the training on our corpus
* It might take a bit of time if corpus is very large, but for this dataset of 1.6 GB of texts it’s blazing fast (1 minute 16 seconds on an AMD Ryzen 9 3900X CPU with 12 cores).

```python
from datasets import load_dataset

# This can take a few minutes to load, so grab a coffee or tea while you wait!
raw_datasets = load_dataset("code_search_net", "python")
# Dataset({
#     features: ['repository_name', 'func_path_in_repository', 'func_name', 'whole_func_string', 'language', 
#       'func_code_string', 'func_code_tokens', 'func_documentation_string', 'func_documentation_tokens', 'split_name', 
#       'func_code_url'
#     ],
#     num_rows: 412178
# })

print(raw_datasets["train"][123456]["whole_func_string"])
#def handle_simple_responses(
#      self, timeout_ms=None, info_cb=DEFAULT_MESSAGE_CALLBACK):
#    """Accepts normal responses from the device.
#
#    Args:
#      timeout_ms: Timeout in milliseconds to wait for each response.
#      info_cb: Optional callback for text sent from the bootloader.
#
#    Returns:
#      OKAY packet's message.
#    """
#    return self._accept_responses('OKAY', info_cb, timeout_ms=timeout_ms)

def get_training_corpus():
    dataset = raw_datasets["train"]
    for start_idx in range(0, len(dataset), 1000):
        samples = dataset[start_idx : start_idx + 1000]
        yield samples["whole_func_string"]

from transformers import AutoTokenizer

old_tokenizer = AutoTokenizer.from_pretrained("gpt2")

example = '''def add_numbers(a, b):
    """Add the two numbers `a` and `b`."""
    return a + b'''

tokens = old_tokenizer.tokenize(example)
tokens
# ['def', 'Ġadd', '_', 'n', 'umbers', '(', 'a', ',', 'Ġb', '):', 'Ċ', 'Ġ', 'Ġ', 'Ġ', 'Ġ"""', 'Add', 'Ġthe', 'Ġtwo',
# 'Ġnumbers', 'Ġ`', 'a', '`', 'Ġand', 'Ġ`', 'b', '`', '."', '""', 'Ċ', 'Ġ', 'Ġ', 'Ġ', 'Ġreturn', 'Ġa', 'Ġ+', 'Ġb']
# This tokenizer has a few special symbols, like Ġ and Ċ, which denote spaces
# and newlines, respectively.

tokenizer = old_tokenizer.train_new_from_iterator(training_corpus, 52000)

tokenizer.save_pretrained("code-search-net-tokenizer")

from huggingface_hub import notebook_login

notebook_login()
tokenizer.push_to_hub("code-search-net-tokenizer")
```
