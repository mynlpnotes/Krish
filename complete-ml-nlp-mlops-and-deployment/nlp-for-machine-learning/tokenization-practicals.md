# 🟢 Tokenization Practicals

* <mark style="color:purple;background-color:purple;">**print((corpus)) # This will not display /n**</mark>
* <mark style="color:purple;background-color:purple;">**Use nltk for tokenization**</mark>
  * <mark style="color:purple;background-color:purple;">**sent\_tokenize ⇒ for sentence tokenization — breaks at /n . !**</mark>
  * <mark style="color:purple;background-color:purple;">**word\_tokenize ⇒ for word tokenization**</mark>

```python
##  Tokenization
## Sentence
from nltk.tokenize import sent_tokenize

print(corpus)   # this will display /n also
print((corpus)) # this will not display /n

documents=sent_tokenize(corpus) 
# will give list of sentences
# it breaks at /n . !

## Paragraph-->words
## sentence--->words
from nltk.tokenize import word_tokenize
# will give list of words
# this will consider hitesh's as a single word
# however hitesh. will be considered as 2 words

from nltk.tokenize import wordpunct_tokenize
wordpunct_tokenize(corpus)
# Here it will consider hitesh's as 3 words hitesh ' s

from nltk.tokenize import TreebankWordTokenizer
tokenizer=TreebankWordTokenizer()
tokenizer.tokenize(corpus)
# Here it will consider hitesh's as 2 words hitesh 's
# hitesh. will be considered as single word but w.r.t last full stop it will
# consider as a single word
```
