# Practical - Multiple Linear Regression

**Assumptions:**

* If there is some linear relationship between ypred and ytest then that means that model has performed well
* Plot KDE plot for residuals, if we get some kind of normal distribution then model is good
* Plot scatter plot with predictions and residuals, if it is distributed and do not have any pattern then model is good



* Here we can see that there seems to be some relation between index\_price and interest\_rate
* Inverse relation between unemployment\_rate and index\_price
* Inverse relation between unemplyment\_rate and interest\_rate
*

    <figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

    ```python
    #drop unneccessary columns
    df_index.drop(columns=["Unnamed: 0","year","month"],axis=1,inplace=True)

    ##check null values
    df_index.isnull().sum()

    sns.pairplot(df_index)

    df_index.corr()

    ## Visualiza the datapoints more closely
    plt.scatter(df_index['interest_rate'],df_index['unemployment_rate'],color='r')
    plt.xlabel("Interest rate")
    plt.ylabel("unemployment rate")

    ##independent and dependent features
    X=df_index.iloc[:,:-1]
    y=df_index.iloc[:,-1]

    X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.25,random_state=42)

    # plot data and a linear regression model fit
    sns.regplot(df_index['interest_rate'],df_index['index_price'])
    sns.regplot(df_index['interest_rate'],df_index['unemployment_rate'])

    scaler=StandardScaler()
    X_train=scaler.fit_transform(X_train)
    X_test=scaler.fit_transform(X_test)

    regression=LinearRegression()
    regression.fit(X_train,y_train)

    ## cross validation
    from sklearn.model_selection import cross_val_score
    validation_score=cross_val_score(regression,X_train,y_train,
                                    scoring='neg_mean_squared_error',
                                    cv=3)

    np.mean(validation_score)
    # Do predictions and calculate performance metrics

    ## Assumptions
    plt.scatter(y_test,y_pred)

    residuals=y_test-y_pred
    sns.displot(residuals,kind='kde')

    plt.scatter(y_pred,residuals)
    ```
*

    <figure><img src="../../.gitbook/assets/image (26).png" alt="" width="270"><figcaption></figcaption></figure>
* Output of reg plot
*

    <figure><img src="../../.gitbook/assets/image (27).png" alt="" width="206"><figcaption></figcaption></figure>

