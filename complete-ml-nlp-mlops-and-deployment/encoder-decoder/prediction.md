# Prediction



*   &#x20;

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
* We encode and embed input 1st, then it will go into encoder in reverse order
* So in RNN, 1st v3 will go, then v2 and then v1
* This encoded information will go into Decoder
* Here in decoder we wont pass any X now, we were passing earlier only for training
* Decoder will give some value at first instance, which will go to softmax, which will give maximum probability, which will be passed to embedding layer, from which we will get numeric value from which we will get the word
* At next instance, the output, hidden info of decoder and the embedded info will be passed to the RNN and so on
