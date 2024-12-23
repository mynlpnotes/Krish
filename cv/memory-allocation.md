# Memory Allocation

* a = 2 ⇒ Here a does not hold 2, it holds the address of the memory
* When we want to store 2, python will communicate with OS for memory allocation
* So 2 will be stored in memory and address will be returned
* If we want to store a list a = \[1,2] then address of 1 and 2 will be returned

Sequential memory:

* RAM will have storage in rows and columns
* If there is a matrix which needs to be stored then any language like C++ will store the elements in any manner in the memory as per availability
* In sequential it covers 1st rows and then columns
* In view whatever memory is used to change the shape should be sequential
* We will pass the data to function continguous() so that it will reallocate the memory and make it sequential
