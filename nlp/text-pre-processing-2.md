# Text Pre processing - 2

```python
# Remove Punctuations
import string
exclude=string.punctuation
def remove_punc(text):
    for char in exclude:
        text = text.replace(char, "")
    return text

data["review"]=data["review"].apply(remove_punc)

# Abbreviation
chat_words={
"AFAIK":"As Far As I Know",
"AFK": "Away From Keyboard",
"ASAP":"As Soon As Possible",
"BTW":"By The Way",
"B4":"Before",
"LAMO":"Laugh My A.. Off",
"FYI":"For your information"    
}

def chat_conversion(text):
    new_text=[]
    for w in text.split():
        if w.upper() in chat_words:
            new_text.append(chat_words[w.upper()])
        else:
            new_text.append(w)
    return " ".join(new_text)

chat_conversion(text1) # For your information this is not true

# Spell Correction
from textblob import TextBlob
text="this is my processing notebook pleae download this ntebook"
textblob=TextBlob(text)
textblob.correct().string
# Does not always give correct results
# Useful only for simple texts

# Remove stopwords
from nltk.corpus import stopwords
stopwords.words("english")

def remove_stop_words(text):
    new_text=[]
    for words in text.split():
        if words in stopwords.words("english"):
            new_text.append("")
        else:
            new_text.append(words.strip())
    return " ".join(new_text).replace("  "," ")

# Remove emoji
import emoji

def remove_emoji(text):
    clean_text=emoji.demojize(text)
    return clean_text

emoji.is_emoji("thumbs up") # False

# Stemming
from nltk.stem import PorterStemmer

def stemming(text):
    obj=PorterStemmer()

    stem_word=[obj.stem(word) for word in text.split()]

    return stem_word

# Lemmatization
from nltk.stem import WordNetLemmatizer

def lammatization(text):
    words=text.split()

    lemmetizer=WordNetLemmatizer()

    lemetized_word=[lemmetizer.lemmatize(word) for word in words]
    
    return lemetized_word
```
