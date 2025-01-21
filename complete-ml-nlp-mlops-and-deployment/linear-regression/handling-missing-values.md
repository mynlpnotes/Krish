# Handling Missing values

1. **Missing completely at Random:**

* Missing values are randomly distributed throughout the dataset, and there is no systematic reason for why they are missing
* Example - Missing response of participants in a survey

2. **Missing at Random:**

* The missing values are systematically related to the observed data, but not to the missing data
* Suppose participants dont prefer to answer their income and the reason for it is related to gender or age and not to the income level

3. **Missing data not at random:**

* The missingness is not random and is dependent on unobserved or unmeasured features that are associated with the missing values
* Participants with low job satisfaction might refuse to enter their income

1. **Mean value imputation:**

* We can check the distribution of the variable
* If its almost normal then we will replace missing with mean
* Works well when we have normally distributed data

2. **Median value imputation:**

* Use if there are outliers OR the variable is not normally distributed

3. **Mode value imputation:**

* Used with categorical values

```python
df.sns.load_dataset('titanic')
df.head()

# Check missing values
df.isnull() # Wherever there is null value it will become True
df.isnull().sum() # It will give no. of nulls in each column

# Delete the rows or datapoints to handle missing missing values
# But we will lose huge datapoints
df.dropna()

# Columnwise - If any column is having lot of nulls then we can delete it
df.dropna(axis = 1)

# But we will try imputation techniques
# 1. Mean value imputation
df['age_mean'] = df['age'].fillna(df['age'].mean())

# 2. Median value imputation
df['age_median'] = df['age'].fillna(df['age'].median())

# 3. Mode imputation
df['embarked'].unique()
df['embarked'].notna() # Returns true per row if not na
mode_value = df[df['embarked'].notna()]['emabarked'].mode()[0]
df['emabarked'].fillna(mode_value)
```
