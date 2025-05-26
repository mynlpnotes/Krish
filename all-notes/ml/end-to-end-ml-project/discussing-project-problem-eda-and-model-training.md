# Discussing Project Problem, EDA and Model Training

Lifecycle of ML Project:

1. Understanding the problem statement

* How students performance is affected by other variables such as Gender, Ethnicity, Parental level of education, Lunch and test preparation course

2. Data collection - 8 columns and 1000 rows
3. Data checks to perform
4. EDA
5. Data pre processing
6. Model training
7. Choose best model

EDA:

* Always do in ipynb and then show the results to the stakeholders

```python
pd.read_csv # To read the data
# columns - gender, race_ethnicity, parental_education, lunch, test_course, 
#           math_score, reading_score, writing_score

# Check missing value
df.isna().sum()

# Check Duplicates
df.duplicated().sum()

# Check data types
df.info()
# column not-null datatype

# Check number of unique values if each columns
df.nunique()

# Check statistic of dataset
df.describe()

# Find the number of categories in each categorial column

# Based on datatype, segregate numerical and categorical columns

# Add column - Total score & Average - This 2 columns will be predicted by the model

# Check number of students who have got 100 marks
# Check number of students who have less than 20 marks
# We can also visualize it
# We can visulaize by gener and marks etc
# 

```



Model Training:

```python
# Prepare X and y columns
# Create Column Transformer with 3 types of transformers
num_features = X.select_dtypes(exclude="object").columns
cat_features = X.select_dtypes(include="object").columns

from sklearn.preprocessing import OneHotEncoder, StandardScaler
from sklearn.compose import ColumnTransformer

numeric_transformer = StandardScaler()
oh_transformer = OneHotEncoder()

preprocessor = ColumnTransformer(
    [
        ("OneHotEncoder", oh_transformer, cat_features),
         ("StandardScaler", numeric_transformer, num_features),        
    ]
)

X = preprocessor.fit_transform(X)

# Train, test split
# We will call subroutine to train models using different algo and get R2 square and 
# store in a df
```
