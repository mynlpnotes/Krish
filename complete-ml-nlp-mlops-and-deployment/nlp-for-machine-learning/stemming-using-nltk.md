# Stemming using NLTK

* Stemming is the process of reducing a word to its word stem
* Stemming is important in natural language understanding (NLU) and natural language processing (NLP)
* Disadvantage: After stemming for some of words, we may not get a correct exact meaning
* For use case like Spam/Ham we should use stemming
* For use case like chatbot we cannot use this
* Regular Expression Stemmer algorithms takes a single regular expression and removes any prefix or suffix that matches the expression
* Snowball stemmer is better version of the Porter Stemmer since some issues of it were fixed in this stemmer.
* We can also specify language here

```python
from nltk.stem import PorterStemmer
stemming=PorterStemmer()
# eating, eats, eaten ----> eat
# history ----> histori
# congratulations ----> congratul

from nltk.stem import RegexpStemmer
reg_stemmer=RegexpStemmer('ing$|s$|e$|able$', min=4)
# eating --> eat
# ingeating --> eat

from nltk.stem import SnowballStemmer
snowballsstemmer=SnowballStemmer('english')
snowballsstemmer.stem(word)
# fairly --> fair # porter stemmer gives fairli
# sportingly --> sport # porter stemmer gives sprtingli
# goes --> goe
```
