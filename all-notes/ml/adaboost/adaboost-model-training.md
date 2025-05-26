# Adaboost Model Training

```python
from sklearn.ensemble import AdaBoostClassifier

models={
    "Logisitic Regression":LogisticRegression(),
    "Decision Tree":DecisionTreeClassifier(),
    "Random Forest":RandomForestClassifier(),
    "Gradient Boost":GradientBoostingClassifier(),
    "Adaboost":AdaBoostClassifier()
}

adaboost_param={
    "n_estimators":[50,60,70,80,90],
    "algorithm":['SAMME','SAMME.R']
}

randomcv_models = [
                   ("RF", RandomForestClassifier(), rf_params),
                    ("AB", AdaBoostClassifier(), adaboost_param)
                   ]


```
