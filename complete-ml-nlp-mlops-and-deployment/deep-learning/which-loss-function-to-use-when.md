# Which Loss function to use when



| Hidden Layers       | Output Layer | Problem Statement          | Loss Function              |
| ------------------- | ------------ | -------------------------- | -------------------------- |
| Relu or its variant | Sigmoid      | Binary classification      | Binary cross entropy       |
| Relu or its variant | Softmax      | Multi class classification | Categorical or Sparse CE   |
| Relu or its variant | Linear       | Regression                 | MSE, MAE, Huber loss, RMSE |
