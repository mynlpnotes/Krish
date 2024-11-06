# Logistic Regression OVO

* One vs One
* **Purpose**: Handles multi-class classification by creating <mark style="color:purple;background-color:purple;">**binary classifiers for each unique pair of classes.**</mark>
* **Method**:
  * For ( C ) classes, train ( \frac{C \times (C - 1)}{2} ) binary classifiers.
  * Each classifier distinguishes between two specific classes (e.g., A vs B, A vs C).
* **Prediction**:
  * <mark style="color:purple;background-color:purple;">**Each classifier votes for one of its two classes.**</mark>
  * <mark style="color:purple;background-color:purple;">**The class with the most votes across all classifiers is chosen as the final prediction.**</mark>
* **Advantages**:
  * Effective when classes overlap or are imbalanced.
* **Disadvantages**:
  * Requires many classifiers for large ( C ), <mark style="color:purple;background-color:purple;">**increasing computation**</mark>.
