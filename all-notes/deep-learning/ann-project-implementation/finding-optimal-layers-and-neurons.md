# Finding Optimal Layers and Neurons

* Start Simple: Begin with a simple architecture and gradually increase complexity if needed.
* Grid Search/Random Search: Use grid search or random search to try different architectures.
* Cross-Validation: Use cross-validation to evaluate the performance of different architectures.
* Heuristics and Rules of Thumb: Some heuristics and empirical rules can provide starting points, such as:
  * The number of neurons in the hidden layer should be between the size of the input layer and the size of the output layer.
  * A common practice is to start with 1-2 hidden layers.

```python
## Define a function to create the model and try different parameters(KerasClassifier)

def create_model(neurons=32,layers=1):
    model=Sequential()
    model.add(Dense(neurons,activation='relu',input_shape=(X_train.shape[1],)))

    for _ in range(layers-1):
        model.add(Dense(neurons,activation='relu'))

    model.add(Dense(1,activation='sigmoid'))
    model.compile(optimizer='adam',loss="binary_crossentropy",metrics=['accuracy'])

    return model

## Create a Keras classifier
model=KerasClassifier(layers=1,neurons=32,build_fn=create_model,verbose=1)

# Define the grid search parameters
param_grid = {
    'neurons': [16, 32, 64, 128],
    'layers': [1, 2],
    'epochs': [50, 100]
}

# Perform grid search
grid = GridSearchCV(estimator=model, param_grid=param_grid, n_jobs=-1, cv=3,verbose=1)
grid_result = grid.fit(X_train, y_train)

# Print the best parameters
print("Best: %f using %s" % (grid_result.best_score_, grid_result.best_params_))
```
