# Code - Text Generation



{% embed url="https://colab.research.google.com/drive/1ZPt3jtYU9qBnYBTD3EaDKSPu1v-RnTAV?authuser=1#scrollTo=0UHJDA39zf-O" %}

```python
# if we use uth-8 then we dont get it as bytes
text = open(Config.path_to_file, 'rb').read().decode(encoding='utf-8')

# To get the unique characters 
vocab = sorted(set(text))

# Vectorize the text
char2idx = {uniChar:idx for idx, uniChar in enumerate(vocab)}
#Output: {'\n': 0, ' ': 1, '!': 2, '$': 3....}
idx2char = np.array(vocab)
# Output: ['\n' ' ' '!' '$' '&' "'" ',' '-' '.' '3' ':' ';' '?' 'A' 'B'...]

# Convert the text into numbers now
text_as_int = np.array([char2idx[c] for c in text])
# Output: array([18, 47, 56, ..., 45,  8,  0])

# The maximum length sentence you want for a single input in characters
examples_per_epoch = len(text)//(Config.seq_length+1)

# Create training examples / targets
char_dataset = tf.data.Dataset.from_tensor_slices(text_as_int)

for i in char_dataset.take(5):
    print(idx2char[i.numpy()])
# Output: 
# F
# i....

# If there are any extra sequences at the end then drop it
sequences = char_dataset.batch(Config.seq_length+1, drop_remainder=True)

for item in sequences.take(5):
    print(repr(''.join(idx2char[item.numpy()])))
# Output:
#'First Citizen:\nBe....All:\nSpeak, speak.\n\nFirst Citizen:\nYou '
#'are all resolved r....ed. resolved.\n\nFirst Citizen:\nFirst, you k'
#"now Caius Marcius .... we know't.\n\nFirst Citizen:\nLet us ki"

def split_input_target(chunk):
    input_text = chunk[:-1]
    target_text = chunk[1:]
    return input_text, target_text

dataset = sequences.map(split_input_target)

# Each index of these vectors is processed as a one time step. 
# For the input at time step 0, the model receives the index for "F" 
# and tries to predict the index for "i" as the next character. 
# At the next timestep, it does the same thing but the RNN considers 
# the previous step context in addition to the current input character
# If we keep buffer size = 1000, it will keep 1000 records in memory(RAM), for training
# it will pick randomly from this 1000, and after a record is picked up, it will
# be replaced with data from local, so speed increases
dataset = dataset.shuffle(Config.BUFFER_SIZE).batch(Config.BATCH_SIZE, drop_remainder=True)

# Build the model
# tf.keras.layers.Embedding: The input layer. A trainable lookup table that
# will map the numbers of each character to a vector with embedding_dim dimensions
# Output of embedding will be passed to GRU
# Output of each GRU will be passed to Dense layer
# If retuen sequence = True, it will take input and give output
# if false,then it will take all inputs and give output at the end
def build_model(vocab_size, embedding_dim, rnn_units, batch_size):
    model = tf.keras.Sequential([
        tf.keras.layers.Embedding(vocab_size, embedding_dim,
                                  batch_input_shape=[batch_size, None]),
        tf.keras.layers.GRU(rnn_units,
                            return_sequences=True,
                            stateful=True,
                            recurrent_initializer='glorot_uniform'),
        tf.keras.layers.Dense(vocab_size)
    ])
    return model

model = build_model(
    vocab_size=len(vocab),
    embedding_dim=Config.embedding_dim,
    rnn_units=Config.rnn_units,
    batch_size=Config.BATCH_SIZE)

# Try the model
for input_example_batch, target_example_batch in dataset.take(1):
    example_batch_predictions = model(input_example_batch)
    print(example_batch_predictions.shape, "# (batch_size, sequence_length, vocab_size)")
# Output: (64, 100, 65) # (batch_size, sequence_length, vocab_size)
# In the above example the sequence length of the input is 100 
# but the model can be run on inputs of any length

# To get actual predictions from the model you need to sample 
# from the output distribution, to get actual character indices. 
# This distribution is defined by the logits over the character vocabulary.
# Note: It is important to sample from this distribution as taking 
# the argmax of the distribution can easily get the model stuck in a loop.
sampled_indices = tf.random.categorical(example_batch_predictions[0], num_samples=1)
sampled_indices = tf.squeeze(sampled_indices,axis=-1).numpy()

# print('Hello/nHi') -- This will print in 2 lines
# print(repr('Hello/nHi')) -- Hello/nHi
print("Input: \n", repr("".join(idx2char[input_example_batch[0]])))
print("Next Char Predictions: \n", repr("".join(idx2char[sampled_indices ])))
# Input: 
# 'profess\nMyself your loyal servant, you.....yet that dare\nLess'

# Next Char Predictions: 
# 'kJKZg:dN$cPJc3EfCJtTLsrTnmqOWEtJFRVTR.w3....XPxS ZI,HnZrkNNHI,YqVB'

# Train the model
def loss(labels, logits):
    return tf.keras.losses.sparse_categorical_crossentropy(labels, logits, from_logits=True)

model.compile(optimizer='adam', loss=loss)

checkpoint_prefix = os.path.join(Config.checkpoint_dir, "ckpt_{epoch}")

checkpoint_callback = tf.keras.callbacks.ModelCheckpoint(
    filepath=checkpoint_prefix,
    save_weights_only=True)

history = model.fit(dataset, epochs=Config.EPOCHS, callbacks=[checkpoint_callback])

# Restore the latest checkpoint
# To keep this prediction step simple, use a batch size of 1.
# Because of the way the RNN state is passed from timestep to 
# timestep, the model only accepts a fixed batch size once built.
# To run the model with a different batch_size, you need to rebuild
# the model and restore the weights from the checkpoint.
model = build_model(vocab_size, Config.embedding_dim, Config.rnn_units, batch_size=1)
model.load_weights(tf.train.latest_checkpoint(Config.checkpoint_dir))
model.build(tf.TensorShape([1, None]))

def generate_text(model, start_string):
    # Evaluation step (generating text using the learned model)
    # Number of characters to generate
    num_generate = 1000
    # Converting our start string to numbers (vectorizing)
    input_eval = [char2idx[s] for s in start_string]
    input_eval = tf.expand_dims(input_eval, 0) 
    # Expand dimension as we want to pass 2 dimension array [] --> [1,]
    # Empty string to store our results
    text_generated = []
    # Low temperature results in more predictable text.
    # Higher temperature results in more surprising text.
    # Experiment to find the best setting.
    temperature = 1.0
    # Here batch size == 1
    model.reset_states()# Reset the states if any
    for i in range(num_generate):
        predictions = model(input_eval)
        # remove the batch dimension
        predictions = tf.squeeze(predictions, 0)
        # using a categorical distribution to predict the character returned by the model
        predictions = predictions / temperature
        predicted_id = tf.random.categorical(predictions, num_samples=1)[-1,0].numpy()
        # Pass the predicted character as the next input to the model
        # along with the previous hidden state
        input_eval = tf.expand_dims([predicted_id], 0)
        text_generated.append(idx2char[predicted_id])
    return (start_string + ''.join(text_generated))


print(generate_text(model, start_string=u"ROMEO: "))
```
