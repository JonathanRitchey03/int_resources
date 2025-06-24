# 🧠 Coding Interview Reference Sheet

## 📌 3 Pillars of Good Code
1. ✅ Readable
2. ⏱️ Time Complexity
3. 💾 Space Complexity

---

## 🎯 What Interviewers Look For
- 🧠 **Analytical Skills** – Can you break down problems?
- 💻 **Coding Skills** – Is your code clean and structured?
- 📚 **Technical Knowledge** – Do you understand fundamentals?
- 🗣️ **Communication** – Are you a good culture fit?

---

## 🪜 Problem Solving Steps

1. ✍️ Write down key details (e.g. “sorted array”).
2. ❓ Clarify: What are the **inputs/outputs**?
3. 🧭 Identify goals: Time? Space? Performance?
4. 🤐 Don’t over-question.
5. 💡 Start with brute-force (explain, don’t code).
6. ⚠️ Explain why it’s inefficient (e.g. `O(n^2)`).
7. 🔍 Walk through and optimize your logic. Watch for bottlenecks.
8. 🗺️ Plan steps **before coding**.
9. 🧩 Modularize – break into small functions.
10. ✨ Now code – clear, simple, and thought-out.
11. 🚫 Avoid assumptions. Write error checks and input validation.
12. 👀 Use good variable names – **descriptive** > `i`, `j`
13. 🧪 Test edge cases: `null`, `undefined`, large inputs.
14. 🛠️ Reflect and suggest improvements or alternate approaches.
15. 📈 Be ready for scale/stream follow-up questions (divide-and-conquer strategy).

---

## ✅ Good Code Checklist

- [x] It works.
- [x] Uses right data structures.
- [x] DRY (Don’t Repeat Yourself).
- [x] Modular and testable.
- [x] Time: Better than O(N²).
- [x] Space-efficient (watch recursion/large copies).

---

## ⚙️ Optimization Heuristics

- 🗃️ **Hash Maps** often improve time complexity.
- 🔀 **Sorted input?** Try **Binary Search** (`O(log N)`).
- 📊 **Sort input** if helpful.
- 🧠 **Precompute or cache** data.
- 🔁 Use **space-time tradeoffs** when appropriate.
- 🧭 **Follow interviewer hints** – they count.
- 💬 Communicate your reasoning **throughout**.

---

> “Don’t just solve. Show your process.”

---

# 📦 Iterative Binary Search
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid  # Found
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1  # Not foun
```

# 🌳 DFS Tree Traversal 

```python
    def dfs(node, result):
        if not node:
            return
        
        // pre-order: Root ➡️ Left ➡️ Right
        // result.append(node.val)  # 👈 Visit root
        // dfs(node.left)           # 👈 Visit left subtree
        // dfs(node.right)          # 👈 Visit right
         
        // in-order: Left ➡️ Root ➡️ Right
        // dfs(node.left)           # 👈 Visit left subtree
        // result.append(node.val)  # 👈 Visit root
        // dfs(node.right)          # 👈 Visit right
        
        // post-order: Root ➡️ Left ➡️ Right
        // dfs(node.left)           # 👈 Visit left subtree
        // dfs(node.right)          # 👈 Visit right
        // result.append(node.val)  # 👈 Visit root
        
subtree

    // invoke depth-first-search
    result = []
    dfs(root, result)
```

# 🎯 Level-Order Traversal (Breadth-First Search)

```python
from collections import deque

def level_order_traversal(root):
    if not root:
        return []

    result = []
    queue = deque([root])

    while queue:
        node = queue.popleft()
        result.append(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)

    return result
```

# 🧙‍♂️ Python Sorting

## 1️⃣ 🔧 `sorted()` – Returns a new sorted list

```python
nums = [4, 2, 7, 1]
sorted_nums = sorted(nums)  # [1, 2, 4, 7]
```

- ✅ Non-destructive (original list unchanged)
- 🧠 Use `key=` for custom sort
- 🔁 Use `reverse=True` for descending order

```python
words = ['banana', 'apple', 'cherry']
sorted(words, key=len)  # ['apple', 'banana', 'cherry']
```

---

## 2️⃣ 🔢 `.sort()` – Sorts the list in-place

```python
nums = [5, 3, 8, 2]
nums.sort()  # modifies nums to [2, 3, 5, 8]
```

- ✅ Destructive (changes original list)
- ❌ Returns `None`
- 🧠 Also supports `key=` and `reverse=`

```python
nums.sort(reverse=True)  # [8, 5, 3, 2]
```

---

## 3️⃣ 🔂 `list.sort()` with a custom `lambda` key

```python
people = [('Alice', 25), ('Bob', 20), ('Eve', 30)]
people.sort(key=lambda person: person[1])  # sort by age
# [('Bob', 20), ('Alice', 25), ('Eve', 30)]
```

- 💡 Powerful for sorting objects or tuples
- 🧩 `lambda` lets you customize the sort field

# 🧠 Python Higher-Order Functions

Higher-order functions take other functions as arguments or return them. Here's a quick guide:

---

## 🔁 `map()` – Transform elements

```python
nums = [1, 2, 3]
squared = list(map(lambda x: x**2, nums))  # [1, 4, 9]
```

- Applies a function to **each item** in an iterable
- Returns a **map object** (use `list()` to view)

---

## 🧹 `filter()` – Keep only matching items

```python
nums = [1, 2, 3, 4]
evens = list(filter(lambda x: x % 2 == 0, nums))  # [2, 4]
```

- Keeps items where the function returns `True`

---

## 🔄 `reduce()` – Combine into one value

```python
from functools import reduce
nums = [1, 2, 3, 4]
total = reduce(lambda x, y: x + y, nums)  # 10
```

- Applies a function cumulatively to reduce iterable to a single value
- Requires `from functools import reduce`

---

## 🎯 `sorted()` with `key=`

```python
words = ['banana', 'apple', 'cherry']
sorted(words, key=len)  # ['apple', 'banana', 'cherry']
```

- `key` takes a function to customize sorting

---

## 🧩 `any()` / `all()`

```python
nums = [1, 2, 3]
any(x > 2 for x in nums)   # True
all(x > 0 for x in nums)   # True
```

- `any()` returns `True` if **any** item is `True`
- `all()` returns `True` if **all** items are `True`

---

## Summary Table

| Function    | Purpose                        |
|-------------|--------------------------------|
| `map()`     | 🎨 Transform items             |
| `filter()`  | 🧹 Keep matching items         |
| `reduce()`  | 🧮 Collapse to single value     |
| `sorted()`  | 🔠 Sort with custom rule       |
| `any()`     | 🔍 At least one True?          |
| `all()`     | ✅ Are all True?               |

> 💡 Use lambda functions for quick inline logic.

# 🧠 Dynamic Programming Template (Bottom-Up Tabulation)

```python
def dp_template(n):
    # Step 1: Define DP table (1D or 2D based on problem)
    dp = [0] * (n + 1)  # or dp = [[0] * cols for _ in range(rows)]

    # Step 2: Initialize base cases
    dp[0] = 1  # Example base case (adjust as needed)

    # Step 3: Iterate through state space
    for i in range(1, n + 1):
        # Step 4: Define recurrence relation
        dp[i] = dp[i - 1] + dp[i - 2]  # Example: Fibonacci recurrence

    # Step 5: Return final result
    return dp[n]
```

# 🧩 Merge Sort – O(n log n)

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    # Divide
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    # Conquer: Merge two sorted halves
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0

    # Merge sorted subarrays
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Append any leftovers
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```