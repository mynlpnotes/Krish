# Pytorch data types

Pytorch has different precision type for each type of data types. Precision is the amount of detail used to describe a number. If we want more amount of detail, we need more precise dtype. Floating point type :

Precision can matter in back propagation, if change in gradient is very small then it should not be lost



* Default dtype of a tensor is torch.float32 or torch.float
* Half of default is torch.float16 or torch.half
* Double of default is torch.float64 or torch.double

Integer dtype :

* torch.int8
* torch.int16 or torch.short
* torch.int32 or torch.int
* torch.int64 or torch.long

Boolean dtype :

* torch.bool

