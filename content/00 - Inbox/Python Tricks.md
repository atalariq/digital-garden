---
title: Python Tricks
description: Python Tricks
date: 2025-12-15
---

# Python Tricks

> #WIP
> - Mixed language between English and Bahasa Indonesia

Resources:
- [11 Tips And Tricks To Write Better Python Code - Python Engineer](https://www.python-engineer.com/posts/11-tips-to-write-better-python-code/)
- [15 Python Tips To Take Your Code To The Next Level! · GitHub](https://gist.github.com/Julynx/dd500d8ae7e335c3c84684ede2293e1f)
- [30 Cool Python Tricks For Better Code With Examples \| DataCamp](https://www.datacamp.com/tutorial/python-tips-examples)
- [Cheat sheet for Competitive Programming with Python 3 \| by Utsav Chokshi \| Medium](https://medium.com/cheat-sheets/cheat-sheet-for-competitive-programming-with-python-3-0477b685d8cd)
- [Python Optimization Tricks in Competitive Programming - Codeforces](https://codeforces.com/blog/entry/145399)

Intented for:
- competitive programming
- practice problem (LeetCode, Hackerrank, etc.)

## I/O

### `sys.stdin` instead of `input()`

> When there are many input lines, using standard input `sys.stdin` is far better than using `input`.

```python
import sys
input = lambda: sys.stdin.readline().rstrip()  # Remove the newline character at the end of the line
II = lambda: int(input())
LII = lambda: list(map(int, input().split()))
```

### advanced use of `print()`

```python
# Default: print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)

print("Default", sep=' ', end='\n', file=sys.stdout, flush=False)

```

## Conditional

### ternary operator

```python
# Before
if condition:
    name = "John"
else:
    name = "Doe"

# After
name = "John" if condition else "Doe"
```

### better checking with `if ... in ...` syntax

```python
# Before
if variable == a or variable == b:
    res = do_something(variable)

# After
if variable in (a, b):
    res = do_something(variable)
```

```python
# Before
if min <= x <= max:
	...
# After
if x in range(min, max+1):
	...
```


### get first item that match to certain condition with `next()`

```python
# Before
numbers = [1, 3, 4, 5, 7, 9, 2]
result = None
for number in numbers:
    if number > 3:
        result = number
        break     

# After
numbers = [1, 3, 4, 5, 7, 9, 2]
result = next(
		   (number for number in numbers if number > 3), 
           None # Fallback value.
         )
```

## Looping

### simplify `while` loop with Walrus Operator `:=`

> Python 3.8+

```python
# Before
line = input()
while line != 'quit':
    process(line)
    line = input()

# After
while (line := input()) != 'quit':
    process(line)

```


## String

### `.join()` instead of `+=` operator for concatenate string

```python
# Before
ans = ''
for s in strs:
    ans += s
# After
ans = ''.join(strs)
```

## Integer

### use larger integer as infinity

```python
# Before
from math import inf
# Or
inf = float('inf')

# After
inf = 1 << 60
dis = [inf] * n
```

## List, Tuple, and Set

### slicing

Format: `sequence[start:end:step]`
- `start`: Indeks awal (inclusive), default `0`
- `stop`: Indeks akhir (exclusive), default `len(sequence)`
- `step`: Langkah/interval, default `1`

```python

numbers: list[int] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Mengambil elemen dari indeks 2 sampai 5
print(numbers[2:6])  # Output: [2, 3, 4, 5]

# Mengambil dari awal sampai indeks 5
print(numbers[:6])   # Output: [0, 1, 2, 3, 4, 5]

# Mengambil dari indeks 5 sampai akhir
print(numbers[5:])   # Output: [5, 6, 7, 8, 9]

# Menggunakan step
print(numbers[::2])  # Output: [0, 2, 4, 6, 8] (setiap 2 elemen)

# Reverse
numbers = [1, 2, 3, 4, 5]
reversed_nums = numbers[::-1] # [5, 4, 3, 2, 1]
text = "Python" reversed_text = text[::-1] # "nohtyP"

# Negative Index
numbers = [1, 2, 3, 4, 5]
last_two = numbers[-2:]      # [4, 5]
all_except_last = numbers[:-1]  # [1, 2, 3, 4]

# Shallow Copy
original = [1, 2, 3]
copy = original[:]  # Membuat salinan baru
copy[0] = 999
print(original)  # [1, 2, 3] - tidak berubah

# Partial List
numbers = [0, 1, 2, 3, 4, 5]
numbers[1:4] = [10, 20, 30]  # [0, 10, 20, 30, 4, 5]
numbers[::2] = [100, 200, 300]  # Mengganti setiap elemen ke-2

# Palindrom Checker
def is_palindrome(s: str) -> bool:
    return s == s[::-1]
```

### `enumerate` instead of `range()`

```python
# Before
for i in range(len(nums)):
    x = nums[i]
    ...

# After
for i, x in enumerate(nums):
    ...
```

### `list` allocations

```python
# Before
nums = []
for i in range(n):
    nums.append(i)

# After
nums = [0] * n
for i in range(n):
    nums[i] = i
```

### multi-dimensional `list` allocations

> Place `list` with larger size inside. On the one hand, it is more friendly in terms of cache continuity; on the other hand, it reduces the overhead of creating `list`.

```python
n, k = 10**5, 20

# Before
dp = [[0] * k for _ in range(n)]

# After
dp = [[0] * n for _ in range(k)]
```

### compress multi-dimensional `list`

```python
# Before
dp = [[0] * n for _ in range(m)]

# After
dp = [0] * (m*n)
compress = lambda i, j: i*n+j
decompress = lambda k: divmod(k, n)
```

### `array.array` instead of `list`

> **`list` is a built-in, flexible container for heterogeneous data** with dynamic resizing, while an **`array.array` is a specialized, memory-efficient container for homogeneous (same-type) numerical data**.

```python
# Before
nums = [0] * n

# After
from array import array
nums = array('i', [0] * n)
```

### remove duplicate with `set`

```python
# Before
cities = ['London', 'Paris', 'London']
unique_cities = []      
for city in cities: 
    if city not in unique_cities:
        unique_cities.append(city)
print(unique_cities)

# After
cities = ['London', 'Paris', 'London']
unique_cities = list(set(cities)) 
print(unique_cities)
```

### unpack `list` and `tupple`

```python
# list
first, *rest, end = my_list
# tuple
first, second, *rest = my_tuple
```

### transform loops to comprehensions

```python
# Before
items = [item1, item2, item3, item4...]
new_items = []    
for item in items:
    item = do_something(item)  # Extract
    item = do_smth_else(item)  # this
    ...                        # logic.
    new_items.append(item)

# After
items = [item1, item2, item3, item4...]    
def process_item(item):        # 'process_item'
    item = do_something(item)  #  now does the
    item = do_smth_else(item)  #  processing
    ...                        #  for a single
    return item                #  item. 
new_items = [process_item(item) for item in items]
```

### list comprehension with intermediate value (walrus operator)

```python
# Before - compute twice or use nested loop
results = [expensive_function(x) for x in data if expensive_function(x) > 0]

# After - compute once
results = [y for x in data if (y := expensive_function(x)) > 0]
```


### save memory with generator

> Similar to list comprehension we can use **generator comprehension** that has the **same syntax but with parenthesis** instead of square brackets. A generator computes our elements lazily, i.e., it produces only one item at a time and only when asked for it

```python
# list comprehension
my_list = [i for i in range(10000)]
print(sum(my_list)) # 49995000

# generator comprehension
my_gen = (i for i in range(10000))
print(sum(my_gen)) # 49995000
```

> This can make a **huge difference when working with large data**, so it's always good to keep the generator in mind

```python
import sys
my_list = [i for i in range(10000)]
print(sys.getsizeof(my_list), 'bytes') # 87616 bytes

my_gen = (i for i in range(10000))
print(sys.getsizeof(my_gen), 'bytes') # 128 bytes
```

### advanced sorting technique

```python
data = (3, 5, 1, 10, 9)
data_reverse = sorted(data, reverse=True)
# [10, 9, 5, 3, 1]

# Sort by length, then alphabetically
words = ["apple", "pie", "zoo", "a", "an"]
sorted_words = sorted(words, key=lambda x: (len(x), x))
# ['a', 'an', 'pie', 'zoo', 'apple']

# Sort tuples by second element, then first
pairs = [(1, 3), (2, 1), (1, 2)]
sorted_pairs = sorted(pairs, key=lambda x: (x[1], x[0]))
# [(2, 1), (1, 2), (1, 3)]

# Sort by first ascending, second descending
data = [(1, 5), (2, 3), (1, 8), (2, 1)]
sorted_data = sorted(data, key=lambda x: (x[0], -x[1]))
# [(1, 8), (1, 5), (2, 3), (2, 1)]

# Sort Dictionary by Value:
scores = {'Alice': 90, 'Bob': 85, 'Charlie': 95}
### Get sorted keys by value
sorted_names = sorted(scores, key=scores.get, reverse=True)
# ['Charlie', 'Alice', 'Bob']

### Or get sorted items
sorted_items = sorted(scores.items(), key=lambda x: x[1], reverse=True)
# [('Charlie', 95), ('Alice', 90), ('Bob', 85)]

```

#### quicksort in one-line

```python
# Quicksort in one line (for educational purposes only!)
qsort = lambda arr: arr if len(arr) <= 1 else qsort([x for x in arr[1:] if x < arr[0]]) + [arr[0]] + qsort([x for x in arr[1:] if x >= arr[0]])

# Usage
print(qsort([3, 1, 4, 1, 5, 9, 2, 6]))
# [1, 1, 2, 3, 4, 5, 6, 9]

```


## Dictionary/Hashmap

### iterate hashmap/dictionary using `dict.items()`

```python
# Before
for k in mp:
    v = mp[k]
    ...

# After
for k, v in mp.items():
    ...
```

### use `defaultdict()` instead of `Counter()` for simple counting

```python
# Before
cnt = Counter()

# After
cnt = defaultdict(int)
```


### safely get value from dictionary

```python
mp = defaultdict(int)

# Before
x = mp[k]

# After
x = mp.get(k, 0)
```


### merging dictionary

```python
a = {"a": 1, "b": 2}
b = {"c": 3, "d": 4}
c = a | b
print(c)
#> {"a": 1, "b": 2, "c": 3, "d": 4}
```

## Function

### arbitrary argument with `*args` and `**kwargs`


```python
def some_function(*args, **kwargs):
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

some_function(1, 2, 3,  a=4, b=5, c=6)
# Args: (1, 2, 3)
# Kwargs: {'a': 4, 'b': 5, 'c': 6}
```

### use built-in function as much as possible

> Due to the implementation at the C level, built-in functions and library functions are usually more efficient than handwritten ones, **but there could be exceptions**.

example 1:
```python
# Before
pres = [0] * (n+1)
for i, x in enumerate(nums):
    pres[i+1] = pres[i] + x

# After
from itertools import accumulate
pres = list(accumulate(nums, initial=0))
```

example 2:
```python
# Before
numbers = [1, 3, 4, 5, 7, 9, 2]
total = 0   
for number in numbers:
    total += number
avg = total / len(numbers)

# After
numbers = [1, 3, 4, 5, 7, 9, 2]
avg = sum(numbers) / len(numbers)
```

#### exception: `min()` and `max()`

> Manually write `min` and `max` for comparing two numbers to avoid additional overhead such as type checking.

```python
# Before
x, y = min(x, y), max(x, y)

# After
fmin = lambda x, y: x if x < y else y
fmax = lambda x, y: x if x > y else y
x, y = fmin(x, y), fmax(x, y)
```

#### exception: `pow()`

> Manually write `pow` for fast exponentiation to avoid additional overhead such as type checking. In addition, `pow(base, exp, mod)` implements the inverse element based on the extended Euclidean algorithm when `exp` is negative, and its efficiency is also slightly lower than the handwritten fast exponentiation

```python
MOD = 10**9+7

# Before
inv = pow(x, -1, MOD)

# After
def qpow(x, k):
    res = 1
    while k:
        if k & 1:
            res = res * x % MOD
        x = x * x % MOD
        k >>= 1
    return res
inv = qpow(x, MOD-2)
```


### iterable function parameter

> For functions that accept an iterable as parameter, the passed iterable can be a generator may not be necessary to create an object like a `list`.

```python
# Before
s = sum([x**2 for x in range(n)])

# After
s = sum(x**2 for x in range(n))
```

## Advanced Technique

### Bitwise Operation

```python
a: int = 5   # Binary: 0101
b: int = 3   # Binary: 0011

print(a & b)   # 1 (0001) - AND
print(a | b)   # 7 (0111) - OR
print(a ^ b)   # 6 (0110) - XOR
print(~a)      # -6 - NOT (two's complement)
print(a << 1)  # 10 (1010) - Left shift
print(a >> 1)  # 2 (0010) - Right shift
```

* Cek Ganjil/Genap (Lebih Cepat dari Modulo):
```python
def is_even(n: int) -> bool:
    return (n & 1) == 0  # Lebih cepat dari n % 2 == 0

def is_odd(n: int) -> bool:
    return (n & 1) == 1
```

* Multiply/Divide by Powers of 2:
```python
n = 10
double = n << 1    # n * 2 = 20
quad = n << 2      # n * 4 = 40
half = n >> 1      # n // 2 = 5
```

* Swap Tanpa Temporary Variable (XOR Swap):
```python
a, b = 5, 10
a ^= b
b ^= a
a ^= b
# Sekarang a = 10, b = 5
# Catatan: Python's a, b = b, a lebih Pythonic dan sama cepatnya
```

* Menghitung Set Bits (Jumlah 1 dalam Binary):
```python
def count_set_bits(n: int) -> int:
    count = 0
    while n:
        count += n & 1
        n >>= 1
    return count

# Atau gunakan built-in
def count_set_bits_fast(n: int) -> int:
    return bin(n).count('1')
```

* Cek Power of 2:
```python
def is_power_of_two(n: int) -> bool:
    return n > 0 and (n & (n - 1)) == 0
```

* Subset Generation (Bitmask DP):
```python
# Generate all subsets of a set using bitmask
def generate_subsets(arr: list) -> list[list]:
    n = len(arr)
    subsets = []
    for mask in range(1 << n):  # 2^n possibilities
        subset = [arr[i] for i in range(n) if mask & (1 << i)]
        subsets.append(subset)
    return subsets

# Example: [1, 2, 3] -> [[], [1], [2], [1,2], [3], [1,3], [2,3], [1,2,3]]
```

* Toggle Specific Bit:
```python
def toggle_bit(n: int, pos: int) -> int:
    return n ^ (1 << pos)

# Contoh: toggle bit ke-2 dari 5 (0101) -> 1 (0001)
```

* Clear Bit Tertentu:
```python
def clear_bit(n: int, pos: int) -> int:
    return n & ~(1 << pos)
```


## Quick Reference

```python
# Fast I/O
import sys
input = sys.stdin.readline

# Multiple test cases
for _ in range(int(input())):
    # your code here
    pass

# Read list of integers
nums = list(map(int, input().split()))

# Grid input
n, m = map(int, input().split())
grid = [list(map(int, input().split())) for _ in range(n)]

# Counter untuk frequency
from collections import Counter
freq = Counter(nums)
most_common = freq.most_common(1)[0]  # (element, count)

# Default dict untuk grouping
from collections import defaultdict
groups = defaultdict(list)
for item in items:
    groups[key(item)].append(item)

# Priority Queue (Min Heap)
import heapq
heap = []
heapq.heappush(heap, (priority, item))
priority, item = heapq.heappop(heap)

# Max Heap (negate values)
heapq.heappush(max_heap, (-priority, item))

# Binary Search
import bisect
index = bisect.bisect_left(sorted_list, target)

# Math operations
import math
gcd = math.gcd(a, b)
lcm = a * b // math.gcd(a, b)

# Infinity
pos_inf = float('inf')
neg_inf = float('-inf')

# All/Any
if all(x > 0 for x in nums):  # All positive?
if any(x < 0 for x in nums):  # Any negative?

# String to int conversion for bases
num = int('1010', 2)  # Binary to decimal: 10
hex_num = int('FF', 16)  # Hex to decimal: 255
```
