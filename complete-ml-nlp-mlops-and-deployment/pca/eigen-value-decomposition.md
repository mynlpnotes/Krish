# Eigen Value Decomposition

* Eigen value of eigen vectors is whenever there is a possibility to showcase any of the data by sum of the constants
* X1 X2
* 2    4
* 4    8
* 3    6
* 8    16
* We can represent X2 using X1, by using 2X1
* That means we have multiplied X1 by a constant, to represent X2 by X1
* Since we are able to represent X2 by X1, we no longer need X2 now
* Eigen vector and eigen values says that it is possible to represent any vector in any other vector format if we are able to find out the constant
* If we are able to find eigen value and eigen vector then we will be done
* Any points which are having magnitude as well as direction are known as vector
* sigma   = A.T @ A/5 🡪 store covariance
* l , x = np.linalg.eig(sigma) 🡪 computes the eigen values and right eigenvectors of a square array
* l is eigen value, x is eigen vector
* Eigen vector corresponding to highest eigen value will be PC1
* PC1 🡪 array(\[-0.56062881, -0.82806723])
* PC2 🡪 array(\[-0.82806723, 0.56062881])
* Always check whether PC1 and PC2 are orthogonal or not
* sigma@x\[:,0]
* sigma@x\[:,1]
* Transformed array:
* pc1\_arr  = A @ x\[:,1]
* array(\[ -7.47835704, 7.21091862, -10.54893951, 0.26743842, 3.07058247, 7.47835704])
* pc2\_arr = A@x\[:,0]
* array(\[ 1.44019997, -0.05150393, -1.31144014, -1.38869604, 2.75164011, -1.44019997])
* scaler = StandardScaler()
* df\_scaled = scaler.fit\_transform(df)
* from sklearn.decomposition import PCA
* pca = PCA(n\_components=2)
* pca.fit\_transform(df1) 🡪 after this dimension of the data, will be row, no. of columns, if n\_components is not provided
* principal\_component = pca.fit\_transform(df1)
* plt.figure()
* plt.plot(np.cumsum(pca.explained\_variance\_ratio\_))
* plt.xlabel("number of required component")
* plt.ylabel("eVR")
* Use the data processed after PCA for training
* For prediction also, we need to 1st transform the input   &#x20;
* dt\_model.predict(pca1.transform(scalar.transform(\[\[1.52101,13.64,4.49,1.10,71.78,0.06,8.75,0.00,0.0]])))
