# ROC

**1. ROC Curve (Receiver Operating Characteristic Curve):**

* The **ROC curve** is a graphical representation that shows the **performance of a classification model** at various thresholds.
* **Axes**:
  * **X-axis**: **False Positive Rate (FPR)**: ( $$\frac{FP}{FP + TN}$$ )
  * **Y-axis**: **True Positive Rate (TPR)**, also called **Recall**: ( $$\frac{TP}{TP + FN}$$ )

**2. How ROC Curve Works:**

* Vary the decision threshold (from 0 to 1) and calculate **TPR** and **FPR** at each threshold.
* <mark style="color:purple;background-color:purple;">**Plot TPR vs FPR for each threshold on the graph.**</mark>
* **Points on ROC curve** represent how the model performs at different thresholds.

**3. ROC Curve Interpretation:**

* **Ideal classifier**: A perfect classifier would have **TPR = 1** and **FPR = 0**, and the point would be at the **top-left corner** of the graph.
* **Random classifier**: A random classifier would lie along the **diagonal line** (from (0,0) to (1,1)) of the graph.
* **Curve above diagonal**: Indicates a good classifier that distinguishes between classes.

**4. AUROC (Area Under the ROC Curve):**

* **AUROC** is the area under the **ROC curve** and is a summary of the classifier's overall performance.
* **Range**: AUROC ranges from **0 to 1**:
  * **AUC = 1**: Perfect classifier (ideal model).
  * **AUC = 0.5**: Random classifier (no better than random guessing).
  * **AUC < 0.5**: Worse than random guessing (misclassified predictions).

**5. Calculating AUROC:**

* **Numerically**, AUROC is calculated using integration or methods like the **trapezoidal rule** to approximate the area under the ROC curve.
* <mark style="color:purple;background-color:purple;">**Higher AUROC indicates better classification performance.**</mark>

**6. Using ROC Curve for Threshold Selection:**

* **Threshold variation**: As the threshold changes (e.g., from 0 to 1), **TPR** and **FPR** change. By plotting these values, you can see how the classifier behaves at different thresholds.
* **Choosing the optimal threshold**:
  * <mark style="color:purple;background-color:purple;">**Maximizing TPR: If recall is the priority (e.g., in medical diagnosis), select a threshold where TPR is high, even at the cost of increasing FPR.**</mark>
  * <mark style="color:purple;background-color:purple;">**Minimizing FPR: If false positives are costly (e.g., in fraud detection), select a threshold with a low FPR, even if it reduces TPR.**</mark>
  * <mark style="color:purple;background-color:purple;">**The ideal threshold corresponds to a point on the ROC curve that balances the trade-off between TPR and FPR (typically where the curve is steepest).**</mark>

**7. Summary:**

* <mark style="color:purple;background-color:purple;">**The ROC curve helps visualize a model's performance across different thresholds.**</mark>
* <mark style="color:purple;background-color:purple;">**AUROC is a scalar metric summarizing the model's overall performance.**</mark>
* <mark style="color:purple;background-color:purple;">**The ROC curve helps in selecting the best threshold for a classifier based on the desired trade-off between True Positive Rate and False Positive Rate.**</mark>
