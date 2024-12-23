# View vs Reshape

View:

* View Returns a new tensor with the same data but of a different shape.&#x20;
* If you're also concerned about memory usage and want to ensure that the two tensors share the same data use view else reshape.&#x20;
* Also if you want contiguous memory then use view.

Reshape:

* This is preferred, it can work with sequential as well as non sequential data
* Returns a tensor with the same data and number of elements as input, but with the specified shape.
* It creates a new copy in the memory with the desired shape and its address will be stored
