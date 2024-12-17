# Tree Plotting

* import  matplotlib.pyplot as plt
* from sklearn import tree
* sklearn.\_\_version\_\_ 🡪 0.23 🡪 above 23 needed to plot tree
* plt.figure(figsize=(20,20))
* tree.plot\_tree(dt\_model1,filled=True, class\_names=\[str(i) for i in set(y1) ,feature\_names=x1.columns)
* plt.savefig('dt\_model\_1')
* If we give filled = true then it will be colourful tree
*

    <figure><img src="../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Since we have 4 classes so that’s why in value its showing count for each class
