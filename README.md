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
- [OOP](#oop)
- [Built In Functions](#built-in-functions)
- [Python Classes](#python-classes)
- [Sort Overriding](#sort-overriding)


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

Average Case
* Access O(1)
* Search O(n)
* Insert O(n)
* Delete O(n)

Worst Case
* Access O(1)
* Search O(n)
* Insert O(n)
* Delete O(n)

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

Average Case
* Access O(1)
* Search O(n)
* Insert O(n)
* Delete O(n)

Worst Case
* Access O(1)
* Search O(n)
* Insert O(n)
* Delete O(n)


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
Average Case
* Access O(n)
* Search O(n)
* Insert O(1)
* Delete O(1)

Worst Case
* Access O(n)
* Search O(n)
* Insert O(1)
* Delete O(1)

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

Average Case
* Access O(n)
* Search O(n)
* Insert O(1)
* Delete O(1)

Worst Case
* Access O(n)
* Search O(n)
* Insert O(1)
* Delete O(1)

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

Average Case
* Access O(1)
* Search O(1)
* Insert O(1)
* Delete O(1)

Worst Case
* Access O(n)
* Search O(n)
* Insert O(n)
* Delete O(n)

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
Average Case
* Access 
* Search O(1)
* Insert O(1)
* Delete O(1)

Worst Case
* Access 
* Search O(n)
* Insert O(n)
* Delete O(n)


### Heap

to create a heap use a list initalized to [] or transform a populated list into a heap by using `heapify()`

```python
import heapq

heap=[]

#adding to heap
heapq.heappush(heap, (1,'one'))
heapq.heappush(heap, (2,'two'))
heapq.heappush(heap, (3,'three'))

#poping from heap
priority, task = heapq.heappop(heap)
#1

#heap replace
#pop the smallest item and push a new item
#more efficient than pop then merge
#appropriate for fixed-sized heaps
heapq.heapreplace(heap, 1)
```

###Priority Queue
Challenges
* sort stablility: how do you get two tasks with equal priorities to be returned in order they were originally added
* tuple comparison breaks for (priority, task) pairs if the priorities are equal and the tasks do not have a default comparison order
* if the priority of a task changes, how do you move it to a new position in the heap?
* or if a pending task needs to be deleted, how do you find it and remove it from the queue?

```python
class PriorityQueue:
	pq =[]
	entry_finder={}
	REMOVED=''
	counter = itertools.count()

	def add_task(task, priority=0):
		if task in entry_finder:
			remove_task(task)
		count = next(counter)
		entry = [priority, count, task]
		entry_finder[task] = entry
		heappush(pq, entry)

	def remove_task(task):
		entry = entry_finder.pop(task)
		entry[-1] = REMOVED

	def pop_task():
		while pq:
			priority, count, task = heapq(pq)
			if task is not REMOVED:
				del entry_finder[task]
				return task
		raise KeyError('pop from an empty priority queue')

```
## Looping

looping through a sequece position index and value can be retrieved at the same time using `enumerate()` function

looping 2 or more sequences the entries can be paired with the `zip()` function

looping over a sequence in reverse first specify the sequence in a foward direction and call the `reversed()` function

looping over a sequence in sorted order use the `sorted()` function, which returns a new list leaving the source unaltered

looping over a large sequence it maybe beneficial to loop over an iterator instead using `iter()`

## Strings
built in string class provides the ability to do complex variable subsitutions and value formatting via the `format()` method. The `Formatter` class in the `string` module allows you to create and customize string formatting behaviors.

```python
#String formatter
a ="Some {0} String {1}".format("short", "!")
"First {0}" # Reference the first positional argument
"First {}" # implicitly reference the frist position
"Name: {name}" # References keyward argument name
"weight in tons {0.weight}" # References the weight attribute of the first argument
"units: {players[0]}" # first element of keyward argument players


# Comma as a thousands separator
'{:,}'.format(12345667)

#percentage
'{:.2%}'.foramt(fraction)

#String to floats
float(string)

#string to int
int(string)

#lowercase the string
string.lower()

#uppercase the string
string.upper()

#split
#String.split(demlim)
a = '1 2 3 4 5'
b = a.split(' ')
b
# ['1', '2', '3', '4', '5']

#joining a string
', '.join(b)
#'1, 2, 3, 4, 5'

#lstrip(s[, chars])
#returns a string with leading characters removed. if chars is omitted whitespace are removed

#rstrip(s[,chars])
#returns a string with trailing characters removed. if chars is not provided whitesapce are removed

#strip(s[, chars])
#returns a copy of the string with leading and trailing characters removed, if chars is not provided, whitespace are removed.


# replacing a string
a = 'hello world'
a.replace('world','')

# casefolded, use for caseless matching
a.casefold()

# endswith - returns true if the string has the suffix
a.endswith('abc')

# find returns the lowerst index in the string where substring is whin the the optional slice, returns -1 if not found
a.find('abc',1,2)

# index - like find but returns ValueError if not found
a.index('abc')

# type check
a.isalpha() # true is all characters in string are alphabetic
a.isdecimal()
a.isdigit()
a.islower()
a.isnumeric()
a.isspace()
```

### Permutation
Permutation without repetition - choosing k from n - n!/(n-k)!

Permutation with repetition -  choosing k - n^k

```python
from itertools import permutations
perms = [''.join(p) for p in permutations('stack')]
perms
#all permutations of the string stack
len(perms)
#total amount of permutations

len(set(perms))
#total unique permutations

#TODO recursive impl

```

### Combination
Combinations without repetition - n!/(k!*(n-k)!)

Combinations with repetition - choosing k - (n+k-1)!/(k!*(n-1)!)

``` python
from itertools import combinations
combo =[''.join(c) for c in combinations('stack',3)]
combo
#combinations of letters of the string stack with length 3
len(combo)
#length of the combinations

#TODO recursive impl

```

### Regex
simple regex
```python
import re

regex = re.compile(pattern)
result = regex.match(string)#whole string only

result = regex.search(string)# anywhere in the string
```

## Algorithms

### Divide and Conquer
multi branched recursion. 

* recursively breaking down a problem into 2 or more subproblems

* in recursive implementation, need to make sure that there is sufficient memory.

* possibly use stack to eliminate recursion.
### Backtracking

### Dynamic Programming
Dynamic Programming saves previously computed answers so that the algorithm no longer have to recompute it again.

DP solutions have a polynomial complextiy. 

Constructing a DP solution
1. find a state for which an optimal solution is found and with the help of which we can find the optimal solution for the next state.

* ordering computations to avoid recalculation

####Top-Down
* memorization - assume have already computed all subproblems

####Bottom-Up
* Tabulation - each subproblem is made up of already computed smaller subproblems therefore larger subproblems is just a function of smaller subproblems.

### Greedy Algorithm
Greedy Algorithm always select the best choice available at the moment.

Greedy Choice Property - from a local optimum we can reach a golobal optimum, without having to reconsider the decision already taken

Optimal Substructure Property - the optimal solution to a problem can be determined for the optimal solution to its subproblems

### Recursion
Recursion consists of a terminating step and a recursive step.

Return statement can be a combination of Recursive calls

or

a variable can be assigned to the results of a recursive step.

note: each recursive step should be closer to the terminating statement than previous recursive steps.

1. it handles a simple "base case" without using recursion
2. avoid cycles
3. each call of the function represents a compolete handling of the given task


## Graphs

### Tree
```python
# Binary Tree impl
class Node:
	def __init__(self, data):
		self.left=None
		self.right=None
		self.data=data

>>> n = Node(1)
>>> p = Node(2)
>>> q = Node(3)
>>> n.left = p
>>> n.right = q
```
Average
* Search O(log n)
* Insert O(log n)
* Delete O(log n)

Worst Case
* Search O(n)
* Insert O(n)
* Delete O(n)


### Tries
A Trie is a tree used to store a dynamic set where the keys are usually strings, each node's position define the key. All children of a node have a common prefix.

Root is always empty string

* Look up is O(m) m is the length of string
* No collisions

### Tree Traversal
#### Pre-Order
Node, Left, Right

#### In-Order
Left, Node, Right

#### Post-Order
Left, Right, Node

### Breath First Search

```python

def bfs(graph, start):
	visted, queue = set(), [start]
	while queue:
		vertex = queue.pop(0)
		if vertex not in visited:
			visited.add(vertex)
			queue.extend(graph.neighbors(vertex) - visited)
	return visited

#paths
def bfs_paths(graph,start,goal):
	queue = [(start,[start])]
	while queue:
		(vertex,path) = queue.pop(0)
		for next in graph.neighbors(vertex) - set(path):
			if next ==goal:
				yield path+[next]
			else:
				queue.append((next,path+[next]))

list(bfs_paths(graph, start, end))

#shortest path
def shortest_path(graph,start,goal):
	try:
		return next(bfs_paths(graph, start, goal))
	except StopIteration:
		return None
shortest_path(graph, start, end)

```


### Depth First Search

```python
def dfs(graph, start):
	visted, stack = set(),[start]
	while stack:
		vertex = stack.pop()
		if vertex not in visited:
			visited.add(vertex)
			stack.extend(graph.neighbors(vertex) - visited)
	return visited

#recursive
def dfs(graph,start, visited=None):
	if visited is None:
		visited=set()
	visited.add(start)
	for next in graph.neighbors(start):
		if next not in visited:
			dfs(graph, next, visited)
	return visited


#paths

def dfs_paths(graph, start, goal):
	stack=[(start,[start])]
	while stack:
		(vertex,path) = stack.pop()
		for next in graph.neighbors(vertex) - set(path):
			if next ==goal:
				yield path+[next]
			else:
				stack.append((next, path+[next]))

list(dfs_paths(graph,start,end))

# recursive path
def dfs_paths(graph, start, goal, path=None):
	if path is None:
		path = [start]
	if start == goal:
		yield path
	for next in graph.neighbors(start) - set(path):
		yield from dfs_paths(graph,next, goal,path+[next])
```
### Djkstra's


### A*

## Sorting

### Quick Sort
Worst Case: O(n^2)
Best Case: O(nlogn)
Average Case: O(nlogn)

worstcase space: O(n)

```python

def quicksort(arr, left, right):
	mid_ptr = (left+right)//2
	mid_value = arr[mid_ptr]
	left_ptr = left
	right_ptr = right
	while left_ptr <= right_ptr:
		while arr[left_ptr]<mid_value:
			left_ptr = left_ptr + 1
		while arr[right_ptr]>mid_value:
			right_ptr = right_ptr - 1
		if arr[left_ptr] > arr[right_ptr]:
			temp = arr[left_ptr]
			arr[left_ptr]= arr[right_ptr]
			arr[right_ptr] = temp
			left_ptr = left_ptr + 1
			right_ptr = right_ptr - 1

	if left_ptr < right:
		quicksort(arr, left, mid_ptr-1)
	if right_ptr > left:
		quicksort(arr, mid_ptr+1, right)
```
### Merge Sort
Worst Case: O(n log n)
Avg Case: O(n log n)
Best Case: O(n log n)

```python

def mergeSort(aList):
	if len(aList) == 1:
		return aList
	mid = len(aList)//2
	left = mergeSort(aList[:mid])
	right = mergeSort(aList[mid:])

	left_ptr, right_ptr, ptr = 0,0,0

	while ptr < len(aList):
		if left_ptr >= len(left):
			aList[ptr] = right[right_ptr]
			right_ptr = right_ptr + 1
		elif right_ptr >= len(right):
			aList[ptr] = left[left_ptr]
			left_ptr = left_ptr + 1
		elif left[left_ptr] < right[right_ptr]:
			aList[ptr] = left[left_ptr]
			left_ptr = left_ptr + 1
		else:
			aList[ptr] = right[right_ptr]
			right_ptr = right_ptr + 1
		ptr = ptr + 1
	return aList

```

### Heap Sort
Worst Case: O(n log n)
Avg Case: O(n log n)
Best Case: O(n log n)
```python
from heapq import heapush
from heapq import heappop

def heapsort(iterable):
	h=[]
	for value in iterable:
		heappush(h, value)
	return [heappop(h) for i in range(len(h))]
```

### Radix Sort
Worst Case O(maxLength n)
```python
def radixsort(aList):
	RADIX =10
	maxLength = False
	tmp, placement = -1, 1
	while not maxLength
		maxLength=True
		#initalize buckets
		buckets = [list() for _ in range(RADIX)]

		#split aList between list
		for i in aList:
			temp = i/placement
			buckets[tmp%RADIX].append(i)
			if maxLength and tmp >0:
				maxLength = False
		#empty list into aList array
		a =0 
		for b in range(RADIX):
			buck=bucket[b]
			for i in buck:
			aList[a]=i
			a+=1
		placement *=RADIX
```

## Lambda
```python
g = lambda x: func(x)
g(2)

g2 = lambda x,y: func(x,y)
g2(2)
```

## del
the del statement can also be used to remove slices from a list
```python
a = [1,2,3,4,5,6]
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

### Shallow Copy
```python
import copy
b = [1,2,3]
a = copy.copy(b)
```

### Deep Copy
```python
import copy
b = [1,2,3]
a = copy.deepcopy(b)
```
## OOP
### Encapsulation
* Binding code and Data togeter into a single unit

### Inheritance
* when one object acquires all the properties and behaviors of parent class

### Polymorphism
* one task is performed by different object instances different ways

### Abstraction
* hiding internal details and showing functionality

## Built In Functions

###collections

#### namedtuple
Named Tuples assign meaning to each position in a tuple and allow for more readable self-documenting code, adds the ability to access fields by name

```python
Point = namedtuple('Point',['x','y'])
p = Point(11, y=22)
x,y =p # unpacking
p.x+p.y
```
#### deque
generalization of stacks and queues

O(1) appends and pops from either direction

append(x)
	- add x to the right of the deque

appendleft(x)
	- add x to the left of the deque

clear()
	- remove all elements from the deque leaving it with length 0

copy()
	- shallow copy

count(x)
	- count the number of deque elements equal to x

extend(iterable)
	- extend the right side of the deque by appending elements

extendleft(iterable)
	- extend the left side of the deque the series of left appends results in reverse order of the iterable elements

index(x[, start[, stop]])
	- returns the position of x in the deque, returns `ValueError` if not found

insert(i,x)
	- insert x into deque at position i

pop()
	- remove and return an elements from the right side of the deque, returns `IndexError` if there is no element

popleft()
	- remove and return an element from the left side of the deque

remove(value)
	- remove the first occurance of value, raise `ValueError` if not found

reverse()
	- inplace reverse the deque

rotate(n)
	- rotate the deque n steps to the right if n is negative, the left.

maxlen
	- max size or `None` if unbounded
#### ChainMap

Provides quickly linking anumber of mappings so they can be treated as a single unit.

```python
c = ChainMap()
d = c.new_child()
e = c.new_child()
e.maps[0]
e.maps[-1]

d['x']=1

```

#### Counter
support convenient and rapid tallies
```python
cnt = Counter()
for word in ['red','blue, 'red','green','blue','blue']:
	cnt[word] +=1
cnt
Counter({'blue':3, 'red':2,'green':1})

+cnt #shows only positive counts
-cnt #shows only negative counts as positive count

#Combining counters
c+d # addition adding 2 counters together
c-d # subtract (only keeps positive count)
c&d # intersect
c|d # union: max(c[x],d[x])
```

* `Counter` is a `dict` subclass for counting hashable objects.
* unordered collection where elements are stored as dictionary keys and their counts are stored as dictionary values

Methods
- `elements()` - returns an iterator over the elements repeating each as many times as its count. ( returned in arbitrary order) (ignore count that is less than 1)

- `most_common([n])` - returns a list of the n most common elements and their counts from the most common to the least

- `update([iterator])

#### orderedDict

Ordered Dictionaries remember the order that the items were inserted.

collections.OrderedDict([items])

popitem(last = True)
	- returns and removes a key value pair, the pairs are returned in a LIFO order if last is True FIFO if last is false
###itertools
###functools
@functools.lru_cache
- Decorator to wrap a function with a memoizing callable

@functools.total_ordering
given a class defining one or more rich comparison ordering methods

* must define one of  `__lt__(), __le__(), __gt__() or __ge__()` in addition to `__eq__()`



##Python Classes

```python
class MyClass:
	def __init__(self):
		pass
	def f(self):
		return 'hello world'

#initialization
x = MyClass()
```

###Public 
public methods are declared as normal.

###Protected 
single underscore for protected

###Private
double underscore for private

###Inheritance
python supports mutliple inheritance. However python only supports method inheritance. python subclasses inherit only methods

```python
class SubClass(MyClass):
	def __init__(self):
		super.__init__()
		self.data=1

#mutliple
class SubClass(MyClass, MyClass1, MyClass2):
	def __init__(self):
		super.__init__()
#python will look at SubClass, MyClass, MyClass1, MyClass2
#python will call superclass methods from left to right

```
###Diamond Problem
Python's diamond problem gets resolved from left to right

###Generators
generators are created by using `yield` instead of `return`

###Abstract Classes
Use NotImplementedError for methods to denote an Abstract Class
```python
class AbstractClass:
	def some_method(self):
		raise NotImplementedError
```

###Python Decorators

Decorators - dynamically alter the functionality of a function, method or class without having to directly use subclasses or change the source code of the function being decorated.

Python Decorators
```python
def my_decorator(some_function):
	def wrapper():
		print("before")
		some_function()
		print("after")
	return wrapper()


from . import my_decorator
@my_decorator
def just_some_function():
	print('hi')

just_some_function()

#before
#hi
#after

```

###Staticmethod
a method that does not use the object it self

using the `@staticmethod` decorator to create static methods

###Classmethod
a method that is not bound to the object but to the class use classmethods as a factory method to generate the class and can also call static methods
using the `@classmethod` decorator to create static methods

```python
def MyClass(object):
	def __init__(self, name='myclass'):
		self.name=name

	@staticmethod
	def static_method():
		print('hello world')

	@classmethod
	def class_factory(cls):
		cls.static_method()
		return cls('myclass')
```

###Mixins
Create small reusable classes to inherit from to gain functionality

###Meta Classes
using meta class to enforce subclass validation

```python
class meta(type):
	def __new__(meta, name, bases, class_dicts):
		#Do some work when creating the new object
		return type.__new__(meta,name,bases,class_dict)

class MyClass(object, metaclass=meta):
	...
	pass
```

###Descriptors
Descriptors modify get set and delete

example: using a Grade class to modify all grades
```python
class Grade(object):
	def __init__(self):
		#use weakKey since this is shared across different objects
		self._values=WeakKeyDictionary()

	def __get__(self, instance, instance_type):
		if instance is None: return self
		return self._values.get(isntance,0)

	def __set__(self, instance, value):
		self._values[instance]=value
```

###Python Object Class

###Python getter and setters
Use the property decorator

```python
class Temp:
	def __init__(self, temperature=0):
		self.temperatrue = temperature

	@property
	def temperature(self):
		#getter
		return self.temperature

	@temperature.setter
	def set_temperature(self, temperature):
		if temperature >1000:
			print('too hot!')
		self.temperature = temperature
```

## Sort Overriding
using key functions to specify a function to be called to make comparisons

value of the key parameter should be a function 

```python
sorted("This is a test".split(), key =str.lower)

# sort complex objects using indicies
sorted([(1,2),(3,4)], key =lambda x: x[2])

# Ascending and Descending
sorted([1,2,3,4,5,2], reverse=True)

#secondary sort
sorted(list1, key= lambda x:(x[1], x[2]))

#using operator
from operator import itemgetter, attrgetter
student_objects =[Student('joh','a','15'), Student('bob','r','10'),Student('deed','g','8')]

student_tuples = [ ('j', 'c',10),('d','e',1)]

sorted(student_tuples, key=itemgetter(1,2))
sorted(student_objects, key=attrgetter('grade','age'))

```