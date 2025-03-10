# 🟢 Language Models

* <mark style="color:purple;background-color:purple;">**All the transformer models have been trained as language model**</mark>
* This means they have been trained on large amounts of raw text in a self-supervised fashion.&#x20;
* Self-supervised learning is a type of training in which the objective is automatically computed from the inputs of the model.&#x20;
* That means that humans are not needed to label the data!



<mark style="color:purple;background-color:purple;">**A Language Model is a machine learning model that can understand, generate, and predict human language by learning patterns and probabilities in text.**</mark>

* Predict the **next word** in a sequence.
* Assign **probabilities** to sequences of words.

**Example:**\
Input: _"I am feeling very"_\
Prediction: _"happy"_



**Training a Language Model**

| **Step**            | **Description**                                                           |
| ------------------- | ------------------------------------------------------------------------- |
| **Data Collection** | Large text datasets (books, websites, articles).                          |
| **Tokenization**    | Split text into tokens (words/subwords).                                  |
| **Objective**       | Predict the next word (or missing word).                                  |
| **Loss Function**   | Measures prediction error and adjusts model weights (Cross Entropy Loss). |
| **Optimization**    | Repeats predictions and corrections millions (or billions) of times.      |

