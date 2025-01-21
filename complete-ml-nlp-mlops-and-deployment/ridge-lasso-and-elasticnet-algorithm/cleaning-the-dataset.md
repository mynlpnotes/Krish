# Cleaning the Dataset

```python
dataset.info()
# This will display column name, non-null count and data type of each column

# Data Cleaning
## missing values
dataset[dataset.isnull().any(axis=1)]
# This will show the records which are having null values

# There are 2 regions 1st 122 records belong to 1st region and remaining to 2nd region
# Also the label is put directly in 1st column once 
# So we divide into 2 regions by add 1 more column
dataset.loc[:122,"Region"]=0
dataset.loc[122:,"Region"]=1
df=dataset

# if we do df.info() then the Region will be of float type
# float takes more memory, so we convert it to int
df[['Region']]=df[['Region']].astype(int)

# There are 2 null records because of the region label issue
df=df.dropna().reset_index(drop=True)

## fix spaces in columns names
df.columns=df.columns.str.strip()

# Chnage the required columns into int
df[['month','day','year','Temperature','RH','Ws']]=df[['month','day','year','Temperature','RH','Ws']].astype(int)

# Change remaining columns to float apart from classes
objects=[features for features in df.columns if df[features].dtypes=='O']
for i in objects:
    if i!='Classes':
        df[i]=df[i].astype(float)

```
