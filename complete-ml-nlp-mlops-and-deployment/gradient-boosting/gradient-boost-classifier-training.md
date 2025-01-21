# Gradient Boost Classifier Training

```python
from sklearn.ensemble import GradientBoostingClassifier

models={
    "Logisitic Regression":LogisticRegression(),
    "Decision Tree":DecisionTreeClassifier(),
    "Random Forest":RandomForestClassifier(),
    "Gradient Boost":GradientBoostingClassifier(),
    "Adaboost":AdaBoostClassifier()
}

gradient_params={"loss": ['log_loss','deviance','exponential'],
             "criterion": ['friedman_mse','squared_error','mse'],
             "min_samples_split": [2, 8, 15, 20],
             "n_estimators": [100, 200, 500],
              "max_depth": [5, 8, 15, None, 10]
                }

randomcv_models = [
                   ("RF", RandomForestClassifier(), rf_params),
                   ("GradientBoost", GradientBoostingClassifier(), gradient_params)
                   ]
```
