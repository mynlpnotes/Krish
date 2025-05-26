# Numpy

* NumPy is a fundamental library for scientific computing in Python.&#x20;
* It provides support for arrays and matrices, along with a collection of mathematical functions to operate on these data structures.

```python
##create a 1D array
arr1=np.array([1,2,3,4,5])
arr.shape # (5,)
arr.reshape(1,5)  ##1 row and 5 columns

# 2d array
arr2=np.array([[1,2,3,4,5],[2,3,4,5,6]])
# [[1 2 3 4 5]
# [2 3 4 5 6]]
# (2, 5)

# Using inbuilt function
np.arange(0,10,2).reshape(5,1)
# array([[0],
#       [2],
#       [4],
#       [6],
#       [8]])

np.ones((3,4)) # 3 rows and 4 columns with all 1

np.eye(3) # identity matrix of size 3

# Attributes of numpy
arr.shape  # Output: (2, 3)
arr.ndim   # Output: 2
arr.size   # Output: 6
arr.dtype  # Output: int32 (may vary based on platform

arr1 + arr2 # Elementwise addition
arr1 - arr2 # Elementwise subtraction
arr1 * arr2 # Elementwise multiplication
arr1 / arr2 # Elementwise division

# Universal operations
np.sqrt(arr)
np.exp(arr)
np.sin(arr)
np.log(arr)

# Slicing
# [[ 1  2  3  4]
# [ 5  6  7  8]
# [ 9 10 11 12]]
arr[1:,1:3]
#[[ 6  7]
# [10 11]]
print(arr[0][0])
print(arr[0:2,2:])
#array([[ 7,  8],
#       [11, 12]])

## Modify array elements
arr[0,0]=100

# Statistical concepts
np.mean(data)
np.median(data)
np.std(data)
np.var(data)

# Logical operations
data=np.array([1,2,3,4,5,6,7,8,9,10])
data[(data>=5) & (data<=8)]
# array([5, 6, 7, 8])
```
