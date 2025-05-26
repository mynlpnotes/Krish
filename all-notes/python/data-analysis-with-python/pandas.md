# Pandas

* Pandas is a powerful data manipulation library in Python, widely used for data analysis and data cleaning.&#x20;
* It provides two primary data structures: Series and DataFrame.&#x20;
* A Series is a one-dimensional array-like object, while a DataFrame is a two-dimensional, size-mutable, and potentially heterogeneous tabular data structure with labeled axes (rows and columns).

```python
data=[1,2,3,4,5]
series=pd.Series(data)
#Series 
#0    1
#1    2
#2    3
#3    4
#4    5

## Create a Series from dictionary
data={'a':1,'b':2,'c':3}
series_dict=pd.Series(data)
#a    1
#b    2
#c    3

## create a Dataframe from a dictionary oof list
data={
    'Name':['Krish','John','Jack'],
    'Age':[25,30,45],
    'City':['Bangalore','New York','Florida']
}
df=pd.DataFrame(data)

df=pd.read_csv('sales_data.csv')
df.tail(5)

df['Name']
# return series of Name column

df.loc[0] # pickup 0th row

df.iloc[0] # 

## Adding a column
df['Salary']=[50000,60000,70000]

df.drop('Salary',axis=1,inplace=True) ## Remove a column
df.drop(0,inplace=True)               ## Remove a row

df.dtypes ## Display the data types of each column
df.describe() ## Statistical summary


```
