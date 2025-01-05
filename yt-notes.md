# [Python for Coding Interviews](https://www.youtube.com/watch?v=0K_eZGS5NsU)

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
print(math.fmod(-10, 3)) //prints -1
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
- Slicing: `arr[start:end]` *end .i.e, last index is non-inclusive*
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
