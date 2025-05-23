# Evaluation Metrics, Loss Function

| Task                           | Common Evaluation Metrics             | Common Loss Functions                      |
| ------------------------------ | ------------------------------------- | ------------------------------------------ |
| Text Generation                | Perplexity, BLEU, ROUGE, METEOR       | Cross-Entropy Loss (next-token prediction) |
| Classification                 | Accuracy, Precision, Recall, F1-score | Cross-Entropy Loss (for class labels)      |
| Question Answering             | Exact Match (EM), F1-score            | Cross-Entropy Loss (token-level)           |
| Language Translation           | BLEU, chrF, METEOR                    | Cross-Entropy Loss (token-level)           |
| Summarization                  | ROUGE (ROUGE-1, ROUGE-2, ROUGE-L)     | Cross-Entropy Loss (token-level)           |
| Sentiment Analysis             | Accuracy, F1-score, Precision, Recall | Cross-Entropy Loss (for class labels)      |
| Named Entity Recognition (NER) | Precision, Recall, F1-score           | Cross-Entropy Loss (token-level)           |
