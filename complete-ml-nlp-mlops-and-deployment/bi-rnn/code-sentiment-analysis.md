# Code - Sentiment Analysis

```python
# This will download dataset as tf
dataset, info = tfds.load(dataset_name, with_info=True, as_supervised=True)
# info can be used to get info about the data

dataset.keys()
#Output: dict_keys(['test', 'train', 'unsupervised'])

# Form train and test set
train_ds, test_ds = dataset["train"], dataset["test"]

# To show the 1st 3 records
for example, label in train_ds.take(3):
  print(f"sample text:\n{example.numpy()}\n")
  print(f"label:\n{label.numpy()}\n")

#BUFFER_SIZE – maintain the buffer of the data in the RAM, so that it can be fetched immediately
#Prefetch – How many records to be kept ready
train_ds = train_ds.shuffle(Config.BUFFER_SIZE).batch(Config.BATCH_SIZE).prefetch(tf.data.AUTOTUNE)
test_ds = test_ds.batch(Config.BATCH_SIZE).prefetch(tf.data.AUTOTUNE)

# Convert text info vectors
encoder = tf.keras.layers.TextVectorization(max_tokens=Config.VOCAB_SIZE)
# Since we want to encode only text, we use lambda function, which will
# take text and label as input and return text
encoder.adapt(train_ds.map(lambda text, label: text))

# We can use this to check the data and labels in a batch
for example, label in train_ds.take(1):
  print(f"sample text:\n{example.numpy()}\n")
  print(f"label:\n{label.numpy()}\n")
  print(f"label:\n{len(label.numpy())}\n")

# To display the 1st 20 tokens
vocab = np.array(encoder.get_vocabulary())
vocab[:20]

# to see the encoded values in 1st 3 records
encoder(example.numpy()[:3])
# Output:
<tf.Tensor: shape=(3, 978), dtype=int64, numpy=
array([[ 74,  10, 397, ...,  77, 513,   1],
       [142,   1, 148, ...,   0,   0,   0],
       [119,   1,   1, ...,   0,   0,   0]])>

#---- Build the model -----
embedding_layer = tf.keras.layers.Embedding(
    input_dim = len(encoder.get_vocabulary()), # 1000
    output_dim = Config.OUTPUT_DIM, # 64
    mask_zero = True
) # it handles the variable sequences lengths - if the sentence is short, it adds zero
# makes use of 
# <sos> - Start of Sentence
# <pad> - padding
# <eod> - End of the Data

Layers = [
          encoder, # text vectorization
          embedding_layer, # embedding
          tf.keras.layers.Bidirectional(
              tf.keras.layers.LSTM(64)
          ),
          tf.keras.layers.Dense(64, activation="relu"),
          tf.keras.layers.Dense(1)
]
model = tf.keras.Sequential(Layers)
model.summary()
model.compile(
    loss=tf.keras.losses.BinaryCrossentropy(from_logits=True), # 
    optimizer=tf.keras.optimizers.Adam(1e-4),
    metrics=["accuracy"]
)

# Define callbacks
def callbacks(base_dir="."):

  # tensorboard callbacks - 
  unique_log = time.asctime().replace(" ", "_").replace(":", "")
  tensorboard_log_dir = os.path.join(Config.TB_ROOT_LOG_DIR, unique_log)
  os.makedirs(tensorboard_log_dir, exist_ok=True)

  tb_cb = tf.keras.callbacks.TensorBoard(log_dir=tensorboard_log_dir)

  # ckpt callback
  ckpt_file = os.path.join(Config.CHECKPOINT_DIR, "model")
  os.makedirs(Config.CHECKPOINT_DIR, exist_ok=True)

  ckpt_cb = tf.keras.callbacks.ModelCheckpoint(
      filepath=ckpt_file,
      save_best_only=True
  )

  callback_list = [
                   tb_cb,
                   ckpt_cb
  ]

  return callback_list

callback_list = callbacks()
history = model.fit(train_ds,
                    epochs=Config.EPOCHS,
                    validation_data=test_ds,
                    validation_steps=30,
                    callbacks=callback_list)

test_loss, test_acc = model.evaluate(test_ds)
print(f"test loss: {test_loss}")
print(f"test accuracy: {test_acc}")

# To display the plots
def get_plot(history, metric):
  history_obj = history.history
  plt.plot(history_obj[metric])
  plt.plot(history_obj[f'val_{metric}'])
  plt.xlabel("Epochs -->")
  plt.ylabel(f"{metric} -->")
  plt.legend([metric, f'val_{metric}'])

get_plot(history, metric="accuracy")
get_plot(history, metric="loss")

# Load tensorboard
%load_ext tensorboard
%tensorboard --logdir base_log_dir/tb_log_dir

# Prediction
sample_text = (
    "The movie was cool. The animation and the graphics were out of the world. I would recommend this movie."
)
model.predict([sample_text])
# Output:
# array([[0.81837535]], dtype=float32)
# If less than 0 then negative else positive
# We making use of raw logits here and not using activation function in output

# Can also try with little complex model
Layers2 = [
          encoder, # text vectorization
          embedding_layer2, # embedding
          tf.keras.layers.Bidirectional(
              tf.keras.layers.LSTM(64, return_sequences=True)
          ),
          tf.keras.layers.Bidirectional(
              tf.keras.layers.LSTM(32) ### 
          ),
          tf.keras.layers.Dense(64, activation="relu"),
          tf.keras.layers.Dropout(0.5), ###
          tf.keras.layers.Dense(1)
]

model2 = tf.keras.Sequential(Layers2)
```
