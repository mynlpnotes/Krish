# EDA and Feature Engineering

* In density plot we can see if it is right skewed, left skewed etc

```python
## Let ave the cleaned dataset
df.to_csv('Algerian_forest_fires_cleaned_dataset.csv',index=Fal

# EDA
## drop day,month and year - They are not important
df_copy=df.drop(['day','month','year'],axis=1)

## categories in classes
df_copy['Classes'].value_counts()
## Encoding of the categories in classes
df_copy['Classes']=np.where(df_copy['Classes'].str.contains('not fire'),0,1)

## Plot desnity plot for all features
plt.style.use('seaborn')
df_copy.hist(bins=50,figsize=(20,15))
plt.show()

# Draw pie chart of classes to see its distribution

# Check the correlation
df_copy.corr()
# We can also use heatmap so as to visualize, we can use seaborn for this

# As per the correlation, plot the figures and check if there are any observations

# Plot box plot to check the outliers
```

* Density plot of all features
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
