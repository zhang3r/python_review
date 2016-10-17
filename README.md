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
#reverse the array in place the original array is replaced with the reversed one.
arr.reverse()

#to list
arr.tolist()

```

### List


```python
#initalization
a=[]

#append
#add an item to the end of the lsit
a.append(1)

#extend
#extend the lsit by appending all the items in the given list
a.extend([2,4])

#insert
a.insert(2,3)

#remove
#errors if there is no such item
a.remove(4)

#pop
a.pop(0)
#1
a.pop()
#3

#clear
a.clear()

#index
returns the index in the list of the first item of value, error if there's no such item
a.index(1)
# >>> ValueError: 1 is not in list

#count
a.count(1)
# >>> 0

#reverse
#reverse the list in place, original is replaced
a=[1,2,3]
a.reverse()
a
#>>> [3,2,1]

#copy
#shallow copy equivalent to a[:]
b = a.copy()
b==a
# >>> True
b is a
# >>> False

```
### Stack

python uses lists for stack impl

```python
stack = [3,4,5]

#adding stack
stack.append(6)
stack.append(7)

#poping from stack
stack.pop()
#7

#stack size
len(stack)

#stack empty
not stack
#false
```

### Queue
can use list as a queue
however not efficient while appends and pops from end are fast insertion or pop form beginning is slow

use deque instead

```python
from collections import deque

#initalization
queue = deque([])

#appending
queue.append(1)
queue.append(2)

#dequeue
queue.popleft()
#1

#reverse
#inplace returns None
queue.reverse()
```
### Tuples

### Tree

### Set

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
## del
the del statement can also be used to remove slices from a list
```python
a=[1,2,3,4,5,6]
del a[0]
a
#2,3,4,5,6

del a[2:4]
a
#2,3

del a[:]
a
#[]
```

## Copy

### Deep Copy
### Shallow Copy

## Built In Functions
###collections
###itertools
###functools


