# Output size calculation

* Input image: 60X60
* Kernel: 3X3
* Padding: 1
* Stride: 2
* Pooling: 2
* Image -> Conv -> Op1 -> Max pooling -> Op2

Output: ![](<../../.gitbook/assets/image (1).png>)



**Op1:** ( 60 - 3 + 2\*1 ) / 2 + 1 -> 30

Op2: (30 - 2 + 2 \* 0) / 2 + 1 -> 15
