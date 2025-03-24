# 🟢 Pandas Profiling

The report consists of the following:

* DataFrame overview,
* Each attribute on which DataFrame is defined,
* Correlations between attributes (Pearson Correlation and Spearman Correlation), and
* A sample of DataFrame.

**Overview:**

* Overview consists of 3 tabs, these are **Overview**, **Alerts,** and **Reproduction**.
* The **Overview** consists of dataset statistics and variable types.&#x20;
* Dataset statistics gives us information on number of variables, duplicates and missing values.
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714112214/r1-(1).png" alt=""><figcaption></figcaption></figure>



**Overview:**

* Next is the **Alerts** tab, which gives us information on the correlated variables.&#x20;
* Also, about the unique values. Here, the data is small but if the dataset will be large then it will also tell us about missing values, skewness of data, etc.
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714114449/r2-(1).png" alt=""><figcaption></figcaption></figure>



**Alerts:**

* The **Reproduction** tab tells us about the start and end time of the report generation, also about the duration, software version, etc. Take a look at the below image for more clearance.
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714115145/r3.png" alt=""><figcaption></figcaption></figure>

#### Variables

* This section gives us information on the variables, which tells us about the type of the variable, then distinct and missing values with the memory size that the variable is taking. Let’s see the example of two variables below, **id** is a real number and **grade** is categorical.
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714115412/r4.png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714115525/r5.png" alt=""><figcaption></figcaption></figure>

#### Correlations

* A statistical tool that helps in the study of the relationship between two variables is known as **Correlation.**

![r6](https://media.geeksforgeeks.org/wp-content/uploads/20230714115724/r6.png)



#### Missing Values

* The profile report also gives us information on missing values in the data visually using the bar plot.
*

    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714120006/r7.png" alt=""><figcaption></figcaption></figure>



#### Sample

* This displays the first and last 10 rows of the dataset.
*   \


    <figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20230714120139/r8.png" alt=""><figcaption></figcaption></figure>
