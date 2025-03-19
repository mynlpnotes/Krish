# 🟠 Anderson Darling Test

1. It compares the **actual data** to the **expected distribution**.
2. <mark style="color:purple;background-color:purple;">**It measures how far your sample data points deviate from the expected cumulative distribution (CDF).**</mark>
3. It gives you a **test statistic** (A²) and **p-values**.
   * A **lower test statistic** means your data **fits** the distribution well.
   * A **higher value** suggests the data does **not** fit the distribution.

#### **Interpretation:**

* **Null hypothesis (H₀):** The data follows the **specified distribution** (often normal).
* If the **p-value** is **low** (say < 0.05), you **reject H₀**, meaning the data **does not** follow the distribution.
* If the **p-value** is **high**, you **fail to reject H₀**, meaning there’s **no evidence against** the distribution (so the data fits).
