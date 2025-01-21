# 🟢 Modern Perceptron

* Mimics a biological neuron
* <mark style="color:purple;background-color:purple;">**It takes multiple inputs, processes them, and produces a single binary output.**</mark>
* Sigmoid is also an threshold function
* Components: weights, bias, inputs, activation function
* A function that maps its input x to an output f(x) -> y
* Heaveside step function
*

    <figure><img src="../../.gitbook/assets/image (97).png" alt="" width="375"><figcaption></figcaption></figure>
*   Below is an example of single layer and single neuron NN

    <figure><img src="../../.gitbook/assets/image (98).png" alt="" width="375"><figcaption></figcaption></figure>

**Limitations of perceptron:**

* **Linear separability**: Can only work on <mark style="color:purple;background-color:purple;">**linearly separable problem such as AND and OR**</mark>. It fails for problems like XOR.
* **Single-layer limitation**: <mark style="color:purple;background-color:purple;">**A single-layer perceptron cannot represent more complex decision boundaries.**</mark>
