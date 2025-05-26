# KDTree Limitation

* KDTree is not ideal for handling mixed types of data because it is fundamentally designed for numeric, continuous spaces.
* For mixed numeric and categorical data, consider other methods like:
  * **Decision Trees** (which naturally handle mixed data types).
  * **Random Forests**.
  * **Distance-Based Algorithms with Custom Metrics** (e.g., KNN with hybrid distances).
