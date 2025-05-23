# 🟢 End to End NLP Pipeline

1. <mark style="color:purple;background-color:purple;">**Data acquisition:**</mark>

* Available data -> csv, pdf, excel, db
* Other data -> scrape, API
* No data -> Create your own data
* if data is not there then do **augmentation**
* <mark style="color:purple;background-color:purple;">**Replace with synonyms**</mark>
* <mark style="color:purple;background-color:purple;">**Back translations**</mark>
* Additional noise - Add noise, unwanted information

2. <mark style="color:purple;background-color:purple;">**Text preparation**</mark>**:**

* **Text clean up:**
  * **Remove html tags, emoji, spell corrections**
  * **Basic preprocessing: Tokenization**
* **Optional preprocessing:**
  * **Stopword removing, stemming, lemmatization, lowercase**
  * **Language detection**
  * **Remove punctuation**
* Advances preprocessing:
  * POS tagging
  * Parsing
* Coreference resolution

3. <mark style="color:purple;background-color:purple;">**Feature engineering**</mark>**:**

* **Text representation/ Text vectorization**
* **BOW**
* **tf-idf**
* **One-hot encoding**
* **ngrams**
* **word2vec**

4. <mark style="color:purple;background-color:purple;">**Modelling**</mark>**:**

* Heuristic approach/ ML/ DL

5. <mark style="color:purple;background-color:purple;">**Evaluation**</mark>**:**

* Intrinsic evaluation - f1, auc, recall
* Extrinsic evaluation - done by users

6. <mark style="color:purple;background-color:purple;">**Deployment**</mark>**:**
7. <mark style="color:purple;background-color:purple;">**Monitoring and model updating**</mark>
