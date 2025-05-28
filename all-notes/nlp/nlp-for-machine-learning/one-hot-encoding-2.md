# One Hot Encoding - 2

* Sentences:
  * People watch cricket - D1
  * Cricket watch cricket - D2
  * People give comments - D3
  * Cricket give comments - D4
* OHE will be as below
* Vocabulary ⇒ People, watch, cricket, give, comments
* Vocabulary Size ⇒ 5
* D1 ⇒ \[ \[ 1 0 0 0 0] \[ 0 1 0 0 0 ] \[ 0 0 1 0 0 ] ] ⇒ Dimension: 3X4
* D2 ⇒ \[ \[ 0 0 1 0 0] \[ 0 1 0 0 0] \[ 0 0 1 0 0  ]]

**Pros:**

* Easy to implement

**Cons:**

* Sparse matrix (Too many 0s in the matrix)
* OOV problem
* No fixed dimension

