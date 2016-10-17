Python 3 review
======================

#Table of Content

- [Data Structures](#data-structures)
- [Strings](#strings)
- [Algorithms](#algorithms)
- [Graphs](#graphs)
- [Sorting](#sorting)
- [Lambda](#lambda)
- [Copy](#copy)
- [Built In Functions](#built-in-functions)


=======================

## Data Structures

### Array

Arrays are sequence types and behave like lists except that the type of objects stored is contstrained

```python
#'b' signed char
#'B' unsigned char
#'i' signed int
#'I' unsigned int
#'l' signed long
#'L' unsigned long
#'f' float
#'d' double

import array
#new array
arr = array.array('l', [1,2,3,4,5])

#type of the array
arr.typecode
# >>> 'l'

#size of array
arr.itemsize
# >>> 4
len(arr)
# >>> 5


#appending
arr.append(6)

#appending different type
arr.append('7')
# >>> TypeERROR: an integer is required (got type str)

#appending a list or any iterable
arr.extend([1,2,3,4])

#counting an occurance
arr.count(1)
# >>> 1
arr.count('1')
# >>> 0

#return the first index of x
arr.index(1)

#insertion
arr.insert(0,10)

#removing the item at i default is -1
arr.pop()
# >>> 4
arr.pop(0)
# >>> 10

#reverse
arr.reverse()

#to list
arr.tolist()

```

### List


```python
#initalization
a=[]
```
### Stack
### Queue
### Tree
### HashSet
### Dictionary
### Heap

## Strings
TODO
### Permutation
### Combination

## Algorithms

### Divide and Conquer
### Dynamic Programming
### Greedy Algorithm
### Recursion

## Graphs

### Breath First Search
### Depth First Search
### Djkstra's
### A*

## Sorting

### Quick Sort
### Merge Sort
### Radix Sort

## Lambda

## Copy

### Deep Copy
### Shallow Copy

## Built In Functions


