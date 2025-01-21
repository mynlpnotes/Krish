# Data Cleaning

#### Handling Missing values <a href="#handling-missing-values" id="handling-missing-values"></a>

1. Handling Missing values
2. Handling Duplicates
3. Check data type
4. Understand the dataset

<pre class="language-python"><code class="lang-python">df.isnull().sum() # To check null values

### Check all the categories
# If there are any spelling mistakes 
df['Gender'].value_counts()

# Single and unmarried is same
df['MaritalStatus'].value_counts()

df['Gender'] = df['Gender'].replace('Fe Male', 'Female')
df['MaritalStatus'] = df['MaritalStatus'].replace('Single', 'Unmarried')

## Check Misssing Values
##these are the features with nan value
features_with_na=[features for features in df.columns if df[features].isnull().sum()>=1]
for feature in features_with_na:
    print(feature,np.round(df[feature].isnull().mean()*100,5), '% missing values')
<strong># Age 4.62357 % missing values
</strong># TypeofContact 0.51146 % missing values
# DurationOfPitch 5.13502 % missing values
# NumberOfFollowups 0.92062 % missing values
# PreferredPropertyStar 0.53191 % missing values
# NumberOfTrips 2.86416 % missing values
# NumberOfChildrenVisiting 1.35025 % missing values
# MonthlyIncome 4.76678 % missing values


</code></pre>



### Imputing Null values <a href="#imputing-null-values" id="imputing-null-values"></a>

* Replace categorical with mode
* Replace numerical with median

```python
#Age
df.Age.fillna(df.Age.median(), inplace=True)

#TypeofContract
df.TypeofContact.fillna(df.TypeofContact.mode()[0], inplace=True)

# Remove unwanted columns
df.drop('CustomerID', inplace=True, axis=1)
```

