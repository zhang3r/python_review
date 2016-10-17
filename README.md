Python 3 review
======================

#Table of Content

- [Data Structures](#data-structures)
- [Looping](#looping)
- [Strings](#strings)
- [Algorithms](#algorithms)
- [Graphs](#graphs)
- [Sorting](#sorting)
- [Lambda](#lambda)
- [Del](#del)
- [Ternary](#ternary)
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
can use list as a queue however not efficient while appends and pops from end are fast insertion or pop form beginning is slow

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
A tuple consists of a number of values separated by commas

```python

t = 123,456,'hi'
t[0]
#123

#tuple maybe nested
u = t, (1,2,3,4)
u[0]
(123,456,'hi')

#tuples are immutable
t[0]=1
#TypeError 'tuptle' es not support item assignment

#unpack a tuple
x,y,z=u[0]
```

### Set
A set is an unordered colleciton with no duplicate elements.

basic uses include membership testing, and eliminating duplicates

supports mathematical operations like union, intersection, difference and symmetric difference

```python
#empty creation
basket = set()

#non empty creation
basket = {'apple','orange','mango'}

#membership testing
'orange' in basket
#True

#without the comma the set is all the letters of the string
a = set('abracadabra')
b = set('alacazam')

a
#{'a','r','b','c','d'}

#letters in a but not b
a-b

#letters in either a or b
a|b

#letters in both a and b
a&b

#letters in a or b but not both
a^b

```

### Dictionary
key value pair data storage

keys must be immutable and unique

```python
#empty
d = {}

#all keys
#unsorted
list(d.keys())

#sorted keys
sorted(d.keys())

#key check
key in d

#adding an entry
d['Trump']='Donald'

#deleting an entry
del d['Trump']
```

looping through dictionaries key and value can be retrieved at the same time

```python
d = {'Trump':'Donald', 'Clinton','Hillary'}
for k,v in d.items():
	print(k,v)
```
### Heap

## Looping

looping through a sequece position index and value can be retrieved at the same time using enumerate() function

looping 2 or more sequences the entries can be paired with the zip() function

looping over a sequence in reverse first specify the sequence in a foward direction and call the reversed function

looping over a sequence in sorted order use the sorted() function, which returns a new list leaving the source unaltered

looping over a large sequence it maybe beneficial to loop over an iterator instead using iter()

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

### Tree
TODO
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

##Ternary
ternary operator
```python
c=['b']
a = True if 'b' in c else False
```

## Copy

### Deep Copy
### Shallow Copy

## Built In Functions
###collections
###itertools
###functools


