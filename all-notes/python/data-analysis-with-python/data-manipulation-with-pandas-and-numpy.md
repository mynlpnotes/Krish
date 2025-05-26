# Data manipulation with Pandas and Numpy

```python
df.head(5)
df.tail(5)
df.describe()
#	Value	Sales
#count	47.000000	46.000000
#mean	51.744681	557.130435
#std	29.050532	274.598584
#min	2.000000	108.000000
#25%	27.500000	339.000000
#50%	54.000000	591.500000
#75%	70.000000	767.500000
#max	99.000000	992.000000

df.isnull().sum()

df_filled=df.fillna(0)
df['Sales_fillNA']=df['Sales'].fillna(df['Sales'].mean())

df=df.rename(columns={'Sale Date':'Sales Date'})
```
