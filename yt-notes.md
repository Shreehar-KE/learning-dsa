# [Python for Coding Interviews](https://www.youtube.com/watch?v=0K_eZGS5NsU) - [NeetCode](https://www.youtube.com/@NeetCode)

## variables
- **Dynamically** typed language
	- Type is determined at runtime
- Multiple Assignments `a, b = 0, 'abc'`
- Increment `n = n + 1` or `n += 1` **but not** `n++`
- `None` is null in python
	- absence of value 

## if statements
- No parentheses are required for conditions 
- No curly braces are required
	- **Indentation** is used instead
-  `:` after a conditional
-  `elif` instead of `else if`
- Parentheses are required for multi-line conditions or  *if you want to force an order of operations*
- `and` instead of `&&`
- `or` instead of `||`

## loops
- similar to if statements, `while` loops requires colon, indentation, no parentheses, no curly braces
- `for` loop uses `range()` with a counter variable like `i` 
	- `range()` can have a **start, stop & step** as arguments
	- only stop is mandatory, default values of start & step are 0 & 1
	- stop value is excluded, so its **0 to (stop - 1)**

## math
- **decimal division** by default, instead of **integer division** by other languages
	- `print(5 / 2)` -> `2.5`
- use double slash for integer division
	- `print(5 // 2)` -> `2` 
	- but it rounds down instead of rounding towards 0, which can be problem when dealing with negative numbers
	- `print(-3 // 2)` -> `-2`
	- workaround: `print(int(-3 / 2))` -> `-1`
- similarly for `%` operator to get remainder value
	- `print(-10 % 3)` ->  `2` instead of `-1` like most languages
```python
import math
print(math.fmod(-10, 3)) # -1
```
- math helper functions
	- `math.floor(3/2)`
	- `math.ceil(3/2)`
	- `math.sqrt(2)`
	- `math.pow(2,3)`
- `float("inf")` for a max integer
- `float("-inf")` for a min integer
- Python numbers are infinite so they never overflow
	- `math.pow(2,200) < float("inf")`

## arrays
- called as **lists** and uses `[]`
- lists are dynamic by default, so they can be used as a stack
```python
arr = [1, 2, 3]
print(arr) # [1, 2, 3]
arr.append(4)
arr.append(5)
print(arr) # [1, 2, 3, 4, 5]
arr.pop()
print(arr) # [1, 2, 3, 4]
```
- but since they are technically an array, values can be inserted by position 
	- `arr.insert(pos, val)`
	- **O^n** time operation
- Indexing & reassigning
	- `print(arr[pos])`
	- `arr[pos] = val`
	- constant time operation
- Initializing an array using: `arr = [1] * 5 # [1, 1, 1, 1, 1]`
- Length of the array: `print(len(arr))`
- `arr[-1]` is not **out of bounds**, instead it's the last value
	- similarly `arr[-2]` returns the 2nd last value  
- Slicing: `arr[start:end]` *end i.e. last index is non-inclusive*
- Unpacking: `a, b, c = [1, 2, 3]` 
- Looping through arrays
	- Using index
```python
nums = [1, 2, 3]
for i in range(len(nums)):
	print(nums[i])
"""
1
2
3
"""
```
	- Without index
```python
nums = [1, 2, 3]
for n in nums:
	print(n)
"""
1
2
3
"""
```
	- Another method using index & value
```python
nums = [1, 2, 3]
for i, n in enumerate(nums):
	print(i, n)
"""
0 1
1 2
2 3
"""
```
	- looping though multiple arrays using unpacking
```python
nums1 = [1, 3, 5]
nums2 = [2, 4, 6]
for n1, n2 in zip(nums1, nums2):
	print(n1, n2)
"""
1 2
3 4
5 6
"""
```
- Reversing an array: `arr.reverse()`

## sorting
```python
arr = [2, 4, 7, 3, 5]

arr.sort()
print(arr) # [2, 3, 4, 5, 7]

arr.sort(reverse=True)
print(arr) # [7, 5, 4, 3, 2]

arr = ["bob", "alice", "jane", "doe"]
arr.sort()
print(arr) # ['alice', 'bob', 'doe', 'jane']

#custom sort - by length of string
arr.sort(key=lambda x: len(x))
print(arr) # ['bob', 'doe', 'jane', 'alice']
```

## list comprehension
```python
arr = [i for i in range(5)]
print(arr) # [0, 1, 2, 3, 4]

arr = [i+i for i in range(5)]
print(arr) # [0, 2, 4, 6, 8]
```

## 2D arrays
```python
arr = [[0] * 4 for i in range(4)]
print(arr) # [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]

arr = [[0] * 4] * 4 # not same as previous method
print(arr) # [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]] 
# each of the 4 rows are the same(reference values), they are not 4 unique rows.
```

## strings
- Similar to arrays, represented by `s = 'abc'` or `s = "abc"`
- Slicing: `print(s[0:2]) # ab`
- Immutable i.e. `s[0] = "A" # this is not possible`
- We can update the whole string
	- `s += "def" # actually creates a new string`
	- **O^n** time operation
- Conversions
	- `print(int("123") + int("123")) # 246`
	- `print(str(123) + str(123)) # 123123`
- `print(ord('a')) # 97 - ASCII value`
- Combining a list of string with an empty string delimitor
	- `strings = ["ab", "cd", "ef"]`
	- `print("".join(strings)) # abcded` 

## queues
- Double ended queues by default
```python
from collections import deque

queue = deque()
queue.append(1)
queue.append(2)
print(queue) # deque([1, 2])

queue.popleft() # constant time operation
print(queue) # deque([2])

queue.appendleft(1) # constant time operation
print(queue) # deque([1, 2])

queue.pop() # constant time operation
print(queue) # deque([1])
```

## hash sets
- used to search in constant time
- there can't be any duplicates in a hash set
```python
mySet = set()
myset.add(1) # constant time operation
mySet.add(2) # constant time operation
print(mySet) # {1, 2}
print(len(mySet)) # 2

# search using in operator
print(1 in mySet) # True
print(2 in mySet) # True
print(3 in mySet) # False 

mySet.remove(2) # constant time operation
print(2 in mySet) # False

# to initialize a hash set using list
print(set([1, 2, 3]))

# Set comprehension
mySet = { i for i in range(5) }
print(mySet)
```

## hash maps
- aka dictionaries in Python
- there can't be any duplicate keys in a hash map
```python
myMap = {}
myMap["alice"] = 88
myMap["bob"] = 77
print(myMap) # {'alice': 88, 'bob': 77}
print(len(myMap)) # 2

myMap["alice"] = 80
print(myMap["alice"]) # True

print("alice" in myMap) # True
myMap.pop("alice")
print("alice" in myMap) # False

myMap = { "alice": 90, "bob": 70 }
print(myMap) # { 'alice': 90, 'bob': 70 }

# Dict Comprehension
myMap = { i: 2*i for i in range(3) }
print(myMap) # { 0: 0, 1: 2, 2: 4 }

# Looping through maps
myMap = { "alice": 90, "bob": 70 } 
for key in myMap:
	print(key, myMap[key])
"""
alice 90
bob 70
"""

for val in myMap.values():
	print(val)
"""
90
70
"""

# using unpacking
for key, val in myMap.items():
	print(key, val)
"""
alice 90
bob 70
"""
```

## tuples
- tuples are like arrays but immutable
- uses `()`
- uses as key for hash map or in hash sets
- lists(being mutable) can't be used as keys
```python
tup = (1, 2, 3)
print(tup) # (1, 2, 3)
print(tup[0]) # 1
print(tup[-1]) # 3

tup[0] = 0 # won't work

myMap = { (1, 2): 3 }
print(myMap[(1, 2)]) # 3

mySet = set()
mySet.add((1, 2))
print((1, 2) in mySet) # True
```

## heaps
- implemented using arrays
- only minHeap is available in python
- multiply values by -1 to use as maxHeap
```python
import heapq

minHeap = []
heapq.heappush(minHeap, 3)
heapq.heappush(minHeap, 2)
heapq.heappush(minHeap, 4)

print(minHeap[0]) # 2

while len(minHeap):
	print(heapq.heappop(minHeap))
"""
2
3
4
"""

maxHeap = []
heapq.heappush(maxHeap, -3)
heapq.heappush(maxHeap, -2)
heapq.heappush(maxHeap, -4)

print(-1 * maxHeap[0]) # 4

while len(maxHeap):
	print(-1 * heapq.heappop(maxHeap))
"""
4
3
2
"""

arr = [2, 1, 8, 4, 5]
heap.heapify(arr) # constant time operation
while arr:
	print(heapq.heappop(arr))
"""
1
2
4
5
8
"""
```

## functions
- `def` keyword
- function name in camel case
- parameters in function declaration
- colon and indented function body
- function call with arguments

## nested functions
- useful in recursive problems, graph problems
```python
def outer(a, b):
	c = "c"
	
	def inner():
		return a + b + c
	return inner()
print(outer("a", "b")) # abc
```
- can modify objects, but not reassign values, unless using `nonlocal` keyword
```python
def double(arr, val):
	def helper():
		# modifying array works
		for i, n in enumerate(arr):
			arr[i] *= 2
		
		# will only modify val in the helper scope
		# val *= 2

		# this will modify val outside helper scope
		nonlocal val
		val *= 2
	helper()
	print(arr, val)

nums = [1, 2]
val = 3
double(nums, val) # [2, 4] 6
```
## classes
```python
class MyClass:
	# Constructor
	# self is equivalent to this keyword in java
	def __init__(self, nums):
		# Create member variables
		self.nums = nums
		self.size = len(nums)
	
	# self keyword required as param
	def getlength(self):
		return self.size
	
	def getDoubleLength(self):
		return 2 * self.getLength()
```