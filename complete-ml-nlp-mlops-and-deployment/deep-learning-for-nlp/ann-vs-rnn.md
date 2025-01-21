# 🟢 ANN vs RNN

* Dataset (Sentiment Analysis)

| Text                 | Output |
| -------------------- | ------ |
| The food is good     | 1      |
| The food is bad      | 0      |
| The food is not good | 0      |

* To solve this with ANN, we will 1st do text pre processing
* We have 6 unique words&#x20;
* Remove is, the as they are stopwords
* So vocabulary is 4 here
* We can use BOW to convert text int vector
* Since this is text data, sequence information is important, but after encoding the order will be lost
* <mark style="color:purple;background-color:purple;">**Whenever we work with text data, it is always a good idea to give 1 word at a time to the network**</mark>
* <mark style="color:purple;background-color:purple;">**So for this we use will be using RNN**</mark>
