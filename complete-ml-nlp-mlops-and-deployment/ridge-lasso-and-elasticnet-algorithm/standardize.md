# Standardize

* Standardize the data coz if the data is in different scales then it will be difficult for the model to understand the relations, if we bring the data to lower scale then model will be able to understand the relations better

1. Handle Null values 🡪 using fillna or imputer
2. Standardize 🡪 mean = 0, standard deviation = 1 , using StandardScaler
3. Check multi collinearity
4. Train test split

```python
scaler = StandardScaler()
arr = scaler.fit_transform(df) 🡪 gives numpy array
df1 = pd.DataFrame(arr)
```
