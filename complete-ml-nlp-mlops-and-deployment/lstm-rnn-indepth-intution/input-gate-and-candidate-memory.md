# 🟢 Input Gate and Candidate memory

* Xt and Ht-1 is concatenated
* From input gate we will get It
* From candidate memory we will get Ct
* It and Ct will be combined using pointwise multiplication
* <mark style="color:purple;background-color:purple;">**Based on the context, if any new information needed to be added in the memory cell then it will be added to Ct**</mark>
* <mark style="color:purple;background-color:purple;">**The sigmoid function outputs values between 0 and 1.**</mark>
* <mark style="color:purple;background-color:purple;">**This acts as a soft selection mechanism, deciding how much of the candidate memory should be allowed into the cell state**</mark>
* <mark style="color:purple;background-color:purple;">**The tanh function outputs values between -1 and 1, ensuring that the candidate memory has a well-defined range.**</mark>
* <mark style="color:purple;background-color:purple;">**This prevents uncontrolled growth of values inside the LSTM.**</mark>
* <mark style="color:purple;background-color:purple;">**If we directly added C\~t\tilde{C}\_tC\~t​ to the cell state, large values could disrupt learning.**</mark>
*   <mark style="color:purple;background-color:purple;">**The sigmoid gate ensures that the update is scaled properly, preventing sudden jumps in memory.**</mark>

    <figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
