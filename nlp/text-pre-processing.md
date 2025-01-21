# Text Pre processing

* Input is provided to LLM/Classical ML model and then we get output
* Data can be messy and have lot of ambiguity
* Latest LLM have very good reasoning capability so there data cleaning is not always required
* But if LLM is hallucinating then it is required
* Libraries: NLTK, Textblob, Spacy

```python
import pandas as pd

data=pd.read_csv("https://raw.githubusercontent.com/Ankit152/IMDB-sentiment-analysis/master/IMDB-Dataset.csv")
# This consists of review and sentiment

data.shape # 50000,2

data["review"][0] # To check the 1st review
```



| Pre Processing         | Steps                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------- |
| Tokenization           |                                                                                          |
| Lowercasing            | data\['review']\[3].lower()                                                              |
|                        | data\['review'].str.lower()                                                              |
| Uppercasing            | data\['review']\[3].upper()                                                              |
| Emoji                  |                                                                                          |
| Punctuation            |                                                                                          |
| HTML,URL               | We can write a subroutine for it and then apply it to the column in the pandas dataframe |
|                        |                                                                                          |
| Stopwords              |                                                                                          |
| Abbreviation or slangs |                                                                                          |
|                        |                                                                                          |

```python
import re

def remove_html_tag(text):
    pattern=re.compile('<.*?>')
    return pattern.sub("",text)

data["review"]=data["review"].apply(remove_html_tag)
```
