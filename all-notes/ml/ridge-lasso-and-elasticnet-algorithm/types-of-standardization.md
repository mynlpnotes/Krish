# Types of Standardization



| Feature                  | **Z-score Standardization** (StandardScaler)  | **Min-Max Scaling** (MinMaxScaler)                                   | **Max Abs Scaling** (MaxAbsScaler)                 |
| ------------------------ | --------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------- |
| **Formula**              | $$( Z = \frac{X - \mu}{\sigma} )$$            | $$( X_{\text{scaled}} = \frac{X - X_{\min}}{X_{\max} - X_{\min}} )$$ | $$\[ X_{\text{scaled}} = \frac{X}{|X_{\max}|} \]$$ |
| **Output Range**         | Mean of 0, standard deviation of 1            | Typically \[0, 1] or custom range                                    | \[-1, 1]                                           |
| **Effect on Outliers**   | Outliers affect mean and standard deviation   | Outliers may compress other values                                   | Less affected by outliers, retains sparsity        |
| **Use Case**             | General standardization; good for most models | For features requiring fixed range, like in neural networks          | For sparse data with values centered around zero   |
| **Data Type**            | Any continuous data                           | Continuous data in a bounded range                                   | Sparse data (like some NLP or recommendation data) |
| **Common Models**        | Linear Regression, Logistic Regression, SVM   | Neural Networks, Image Processing                                    | Sparse data processing, SVM, k-NN                  |
| **`scikit-learn` Class** | `StandardScaler`                              | `MinMaxScaler`                                                       | `MaxAbsScaler`                                     |
| **Example Use**          | Models sensitive to feature scaling           | Scaling pixel values \[0, 255]                                       | Scaling sparse word frequency vectors              |

