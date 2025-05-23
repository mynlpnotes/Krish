---
hidden: true
---

# Understanding Self Attention

* The tiger jumped out of a tree to get a drink because it  &#x20;was thirsty
* Here tiger and it are the same so they should be strongly connected



1. Creating queries, keys, and values:&#x20;

* Each input embedding is multiplied by three learned  &#x20;weight matrices (Wq, Wk, Wv) to generate query (Q), key (K), and value (V) vectors.&#x20;
* **Query:** The query vector helps the model ask, “Which other words in the sequence are  \
  relevant to me?”
* **Key:** The key vector is like a label that helps the model identify how a word might be  \
  relevant to other words in the sequence.
* **Value:** The value vector holds the actual word content information.



2. Calculating score:

* Dot product of the query vector of one  &#x20;word with the key vectors of all the words in the sequence



3. Normalization:&#x20;

* The scores are divided by the square root of the key vector dimension (dk)  &#x20;for stability, then passed through a softmax function to obtain attention weights.&#x20;
* These  &#x20;weights indicate how strongly each word is connected to the others



4. Weighted values:&#x20;

* Each value vector is multiplied by its corresponding attention weight.
* The results are summed up, producing a context-aware representation for each word.



<figure><img src="../../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>
