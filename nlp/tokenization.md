# Tokenization

Later on we will be using langchain and lamaindex going forward

```python
## Using split
text.split()    # Word tokenization => THis will give list of words
text.split(".") # Sentence tokenization

# Using regex
import re
re.findall("[\w]+", text)

# Using nltk
from nltk.tokenize import word_tokenize,sent_tokenize
nltk.download("all")

word_tokenize(text)
sent_tokenize(my_corpus)



```
