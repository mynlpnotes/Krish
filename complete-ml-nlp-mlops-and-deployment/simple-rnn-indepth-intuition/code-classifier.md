# Code - Classifier

```python
import numpy as np
import tensorflow as tf

with open('reviews.txt', 'r') as f:
    reviews = f.read()
with open('labels.txt', 'r') as f:
    labels = f.read()
# Reviews file contans review seperated by /n and labels.txt contains labels

# Data Pre-Processing
from string import punctuation
all_text = ''.join([c for c in reviews if c not in punctuation])
reviews = all_text.split('\n') # list of all reviews
all_text = ' '.join(reviews)
words = all_text.split()

# Encoding the words
from collections import Counter
counts = Counter(words)
vocab = sorted(counts, key=counts.get, reverse=True)

# Create your dictionary that maps vocab words to integers here
vocab_to_int = {word: i for i, word in enumerate(vocab, 1)} # start from 1

# Convert the reviews to integers, same shape as reviews list, but with integers
review_ints = []
for each in reviews:
    review_ints.append([vocab_to_int[word] for word in each.split()])

# Encoding the labels
labels = labels.split('\n')
labels = np.array([1 if label == 'positive' else 0 for label in labels])
review_lens = Counter([len(x) for x in review_ints])
review_ints = [review for review in review_ints if (len(review) > 0)]

#  Each row should be 200 elements long. For reviews shorter than 200 words,
# left pad with 0s. That is, if the review is ['best', 'movie', 'ever'], 
#[117, 18, 128] as integers, the row will look like [0, 0, 0, ..., 0, 117, 18, 128].
# For reviews longer than 200, use on the first 200 words as the feature vector.
seq_len = 200
features = []
for review in review_ints:
    review_len = len(review)
    len_diff = seq_len - review_len
    if len_diff <= 0:
        features.append(review[:seq_len])
        print(review[:seq_len])
    else:
        padding = [0] * len_diff
        padded_feature = padding + review
        features.append(padded_feature)
print()
features = np.asarray(features)
Output:
[22382, 42, 46418, 15, 706, 17139.....]
[22382, 42, 46418, 15, 706, 17139.....]

# Train, Validation, Test
split_frac = 0.8
split_idx = int(len(features) * split_frac)

train_x, val_x = features[:split_idx], features[split_idx:]
train_y, val_y = labels[:split_idx], labels[:split_idx]

test_idx = int(len(val_x) * 0.5)
val_x, test_x = val_x[:test_idx], val_x[test_idx:]
val_y, test_y = val_y[:test_idx], val_y[test_idx:]

print("\t\t\tFeature Shapes:")
print("Train set: \t\t{}".format(train_x.shape), 
      "\nValidation set: \t{}".format(val_x.shape),
      "\nTest set: \t\t{}".format(test_x.shape))
      
# Simple RNN
# parameters for data load
num_words = 30000
maxlen = 50
test_split = 0.3

(X_train, y_train), (X_test, y_test) = reuters.load_data(num_words = num_words, maxlen = maxlen, test_split = test_split)

# pad the sequences with zeros 
# padding parameter is set to 'post' => 0's are appended to end of sequences
X_train = pad_sequences(X_train, padding = 'post')
X_test = pad_sequences(X_test, padding = 'post')

X_train = np.array(X_train).reshape((X_train.shape[0], X_train.shape[1], 1))
X_test = np.array(X_test).reshape((X_test.shape[0], X_test.shape[1], 1))

y_data = np.concatenate((y_train, y_test))
y_data = to_categorical(y_data)
y_train = y_data[:1395]
y_test = y_data[1395:]

def vanilla_rnn():
    model = Sequential()
    model.add(SimpleRNN(50, input_shape = (200,1), return_sequences = True))
    model.add(SimpleRNN(50,return_sequences = True))
    model.add(SimpleRNN(50))
    model.add(Dense(46))
    model.add(Dense(46))
    model.add(Dense(46))
    model.add(Activation('sigmoid'))
    
    adam = optimizers.Adam(lr = 0.001)
    model.compile(loss = 'sparse_categorical_crossentropy', optimizer = adam, metrics = ['accuracy'])
    
    return model

model = KerasClassifier(build_fn = vanilla_rnn, epochs = 1, batch_size = 50, 
                        verbose = 1)
model.fit(train_x, train_y)

y_pred = model.predict(train_x)
y_test_ = np.argmax(y_test, axis = 1)

print(accuracy_score(y_pred, y_test_))

# Stacked RNN
def stacked_vanilla_rnn():
    model = Sequential()
    model.add(SimpleRNN(50, input_shape = (49,1), return_sequences = True))   # return_sequences parameter has to be set True to stack
    model.add(SimpleRNN(50, return_sequences = False))
    model.add(Dense(46))
    model.add(Activation('softmax'))
    
    adam = optimizers.Adam(lr = 0.001)
    model.compile(loss = 'categorical_crossentropy', optimizer = adam, 
                  metrics = ['accuracy'])
    return model

```
