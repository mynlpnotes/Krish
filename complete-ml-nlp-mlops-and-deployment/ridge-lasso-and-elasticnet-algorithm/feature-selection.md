# Feature Selection

* If features are highly correlated then we should remove it
* We should define some threshold for it -- Domain expert
*

    ```python
    ## Independent And dependent features
    X=df.drop('FWI',axis=1)
    y=df['FWI']

    X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.25,random_state=42)

    ## Feature Selection based on correlaltion
    X_train.corr()

    # Visualize the correlation
    plt.figure(figsize=(12,10))
    corr=X_train.corr()
    sns.heatmap(corr,annot=True)

    def correlation(dataset, threshold):
        col_corr = set()
        corr_matrix = dataset.corr()
        for i in range(len(corr_matrix.columns)):
            for j in range(i):
                if abs(corr_matrix.iloc[i, j]) > threshold: 
                    colname = corr_matrix.columns[i]
                    col_corr.add(colname)
        return col_corr

    ## threshold--Domain expertise
    corr_features=correlation(X_train,0.85

    ## drop features when correlation is more than 0.85 
    X_train.drop(corr_features,axis=1,inplace=True)
    X_test.drop(corr_features,axis=1,inplace=True)

    # Feature scaling or standardization
    scaler=StandardScaler()
    X_train_scaled=scaler.fit_transform(X_train)
    X_test_scaled=scaler.transform(X_test)
    ```
