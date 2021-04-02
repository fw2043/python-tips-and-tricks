This is a Work in Progress

## What is this ?

Initially, I created this list to show my friends how cool Python is. Now, this list contains Python Tips and Tricks I learned and collected from years of solving [Leetcode](https://leetcode.com/JummyEgg/) problems. The purpose of this list is to show you best practices in writing Pythonic code. Please enjoy.

This uses `python >= 3.6` unless specified.

## Table of Contents

- [What is this ?](#what-is-this-)
- [Table of Contents](#table-of-contents)
- [Basic Tips and Tricks](#basic-tips-and-tricks)
  - [Swap 2 variables](#swap-2-variables)
  - [Python Unpacking](#python-unpacking)
  - [Enumerate()](#enumerate)
  - [List Comprehension](#list-comprehension)
  - [Dictionary and Set Comprehension](#dictionary-and-set-comprehension)
  - [Multiple Statements on 1 line](#multiple-statements-on-1-line)
- [Extended Tips and Tricks](#extended-tips-and-tricks)
  - [Python Unpacking with `*`](#python-unpacking-with-)
  - [Conditional Comprehensions](#conditional-comprehensions)

## Basic Tips and Tricks

### Swap 2 variables

In some other languages, when we want to swap 2 variables, we tend to use `temp` to store the value. However, in Python, there is a cleaner way to do this:

```python
a = 10
b = 20
c = 30
a, b, c = c, a, b    # <--- all three assignments are done at the same time
print(a, b, c)
# 30 10 20
```

More: [Multiple Statements on 1 line](#multiple-statements-on-1-line)

### Python Unpacking

Unpack values from a tuple or a list:

```python
first, second, last = [10, 20, 30]
print(first, second, last)

# Output
# 10 20 30
```

Nested Unpacking:

```python
matrix = [[1, 2], [10, 20]]
(one, two), (three, four) = matrix
print(one, two, three, four)

# Output:
# 1 2 10 20
```

Nested Unpacking inside loop:

```python
matrix = [[1, 2], [3, 4], [5, 6]]
for val1, val2 in matrix:
    print(val1, val2)

# Output:
# 1 2
# 3 4
# 5 6
```

<!-- Add example how to unpack values from function -->
More: [Python Unpacking with `*`](#python-unpacking-with-)

### Enumerate()

When writing Python, the clean way to iterate over **index and value** at the same time is to use `enumerate()` like this:

```python
for i, val in enumerate(["A", "B", "C"]): # <--- this is python unpacking
    print(i, val)

# Output
# 0 A
# 1 B
# 2 C
```

`enumerate()` accepts an **optional argument** where you can specify **starting index** of `idx`

```python
for i, val in enumerate(["A", 7, {1, 2}], 100):
    print(i, val)

# Output
# 100 A
# 101 7
# 102 {1, 2}
```

### List Comprehension

**Cleaner and faster** way to do `for` loop:

```python
nums = [i for i in range(1, 5)]
print(nums)

# Output
# [1,2,3,4]
```

2 `for` loops:

```python
nums = [i * j for i in range(1, 5) for j in range(10, 12)]
print(nums)

# Output
# [10, 11, 20, 22, 30, 33, 40, 44]
```

2 **NESTED** `for` loops:

```python

matrix = [[i * j for i in range(1, 5)] for j in range(10, 12)]
print(matrix)

# Output
# [[10, 20, 30, 40], [11, 22, 33, 44]]
```

Example use cases:

- [Matrix Initialization](./examples/list_comprehension/matrix_initilization.py)

### Dictionary and Set Comprehension

Dictionary also has comprehension:

```python
my_dict = {val : i for i, val in enumerate([10, 20, 30])}
print(my_dict)

# Output
# {10: 0, 20: 1, 30: 2}
```

Set also has comprehension:

```python
nums = [1,1,1,2,2,3,3,4]
my_set = {num for num in nums}
print(my_set)

# Output
# {1, 2, 3, 4}
```

You might ask why bother with Set Comprehension when we could do this: `print(set(nums))`. The answer is because of [Conditional Comprehensions](#conditional-comprehensions)

### Multiple Statements on 1 line

Although in Python, we don't use `;` often, it can help with writing multiple lines of code on the same line like this:

```python
a = 3; b = 10; c = "--"
for i in range(a): print(i * b); print(c)

# Output:
# 0
# --
# 10
# --
# 20
# --
```

However, as you can imagine, this can be hard to read if you overuse it. So please use it with care. I tend to only use it for variable initilization.

## Extended Tips and Tricks

### Python Unpacking with `*`

While unpacking, you can use `*` to greedy match as much as it can and return a **list**

```python
first, second, *rest = [1, 2, 3, 4, 5, 6]
print(first, second, rest)

# Output
# 1 2 [3, 4, 5, 6]
# Notice that rest is a list

first, *mid, last = [1, 2, 3, 4, 5, 6]
print(first, mid, last)

# Output
# 1 [2, 3, 4, 5] 6
```

Because `*` is greedy (matches as much as it can), you cannot use two `*` in one unpack

```python
first, *mid, *rest = [1, 2, 30, 40, 50, 60]
print(first, mid, rest)

# Output
# SyntaxError: two starred expressions in assignment
```

### Conditional Comprehensions

Conditional Comprehensions allow us to add `if else` statement into list/set/dict comprehensions.

`if` statement in List Comprehension:

``` python
nums = [i for i in range(10) if i % 2]
print(nums)

# Output:
# [1, 3, 5, 7, 9]
```

`if else` statement in List Comprehension. Notice that `if else` is placed in the **front**.

``` python
nums = [i if i % 2 else 0 for i in range(10)]
print(nums)

# Output:
# [0, 1, 0, 3, 0, 5, 0, 7, 0, 9]
```

To Add: 
- *args, **kwargs
- one-line if
- for else
- while else
- unpack and iterate at the same time
- collections
  - defaultdict
  - queue
  - Counter, | &
- itertools
  - chain
  - zip longest
- functools
  - lambda
  - map
  - filter
  - reduce
- class
- Generator
- Iterator
- pprint
- cache()
- decorator
- access variable outside of function
- https://github.com/chiphuyen/python-is-cool
- https://book.pythontips.com/en/latest/enumerate.html
- https://github.com/alexghergh/python-tricks
