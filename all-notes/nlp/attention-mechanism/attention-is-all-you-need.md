# Attention is all you need

* Research paper
*

    <figure><img src="../../../.gitbook/assets/image (551).png" alt=""><figcaption></figcaption></figure>
* Scaled-Dot Production we seen already
* **Scaled dot product:**
*

    <figure><img src="../../../.gitbook/assets/image (552).png" alt=""><figcaption></figcaption></figure>
* Scaling done to avoid vanishing gradient - divide by 1/√d
* d = length of the embedding
* Masking is optional
* Scores will be passed to softmax, which when done matrix multiplication with V we get Y1, Y2….
* Masking is for adding noise, its like forcing to learn is something is missing, like even if am is missing then also it learns
* Multi head attention block we have already seen
* ![](<../../../.gitbook/assets/image (553).png>)
* It is having encoder and decoder, here instead of RNN we are using attention blocks
* We can stack encoder and decoder multiple times
