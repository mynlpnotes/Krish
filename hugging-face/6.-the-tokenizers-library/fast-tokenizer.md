# Fast Tokenizer

* Slow tokenizers are those written in Python inside the Transformers library, while the fast versions are the ones provided by Tokenizers, which are written in Rust
* Fast tokenizers always keep track of the original span of texts the final tokens come from — a feature we call _offset mapping_.&#x20;
* This in turn unlocks features like mapping each word to the tokens it generated or mapping each character of the original text to the token it’s inside, and vice versa
* `[CLS]` and `[SEP]` are mapped to `None`

```python
# To check if tokenizer is fast or slow
tokenizer.is_fast
# True
```

* Fast tokenizer enables us to below

```python
# Access the 
encoding.tokens()
#['[CLS]', 'My', 'name', 'is', 'S', '##yl', '##va', '##in', 'and', 'I',
# 'work', 'at', 'Hu', '##gging', 'Face', 'in', 'Brooklyn', '.', '[SEP]']

# word_ids() method to get the index of the word
[None, 0, 1, 2, 3, 3, 3, 3, 4, 5, 6, 7, 8, 8, 9, 10, 11, 12, None]

# We can map any word or token to characters in the original text, and vice versa,
# via the word_to_chars() or token_to_chars() and char_to_word() or char_to_token() 
# methods
start, end = encoding.word_to_chars(3)
example[start:end]
# Sylvain
```







