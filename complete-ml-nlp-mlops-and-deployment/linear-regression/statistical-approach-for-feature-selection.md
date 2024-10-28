# Statistical approach for feature selection

```python
import statsmodel.formula.api as smf
lm = smf.ols(formula=’sales~TV+radio’,data=data).fit()
lm.summary()


```

*

    <figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>
* P means significance value
* Since P is 0 then it means it’s a significant level
* Since P is 0.86 , so 100 – 86 = 14
* Then it means significance level for newspaper is very low
* It means out of 100 experiments, in 14 its contributing and in 86 its not contributing
* If significance level is less than 0.05 then we consider that feature
* Std error means the standard deviation
