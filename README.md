# DAY 2 — Python Problem Solving & Core Data Structures

**Name:** POLAGANI HARINADH BABU  
**Date:** 27/10/2026  
**Day:** 2

---

## 1. Duplicate-Removal Problem

### Approach
I use a set named `seen` to track elements that have already appeared and a list named `result` to store unique elements in their original order. If an element is not in the set, I add it to both the set and the result list.

### Code

```python
def unique_in_order(items):
    seen = set()
    result = []

    for item in items:
        if item not in seen:
            seen.add(item)
            result.append(item)

    return result


print(unique_in_order([]))                   # []
print(unique_in_order([5]))                  # [5]
print(unique_in_order([2, 2, 2]))            # [2]
print(unique_in_order([3, 1, 3, 2, 1]))      # [3, 1, 2]
print(unique_in_order([1, 2, 3]))            # [1, 2, 3]
```

### Test Inputs and Outputs

| Test Input | Expected Output |
|---|---|
| `[]` | `[]` |
| `[5]` | `[5]` |
| `[2, 2, 2]` | `[2]` |
| `[3, 1, 3, 2, 1]` | `[3, 1, 2]` |
| `[1, 2, 3]` | `[1, 2, 3]` |

### Time and Space Complexity
- Time Complexity: O(n) expected.
- Auxiliary Space Complexity: O(n) in the worst case.

The elements must be hashable because a set is used.

---

## 2. Sliding-Window Problem

### Approach
I use the sliding-window technique to find the maximum sum of any contiguous window of size `k`. First, I calculate the sum of the first window. Then, I subtract the outgoing element and add the incoming element for each next window. I validate `k` before calculating the sum.

### Code

```python
def max_sum_window(numbers, k):
    if k <= 0 or k > len(numbers):
        return None

    window_sum = sum(numbers[:k])
    best = window_sum

    for right in range(k, len(numbers)):
        window_sum += numbers[right] - numbers[right - k]
        best = max(best, window_sum)

    return best


print(max_sum_window([2, 1, 5, 1, 3, 2], 3))  # 9
print(max_sum_window([5], 1))                 # 5
print(max_sum_window([1, 2, 3], 3))            # 6
print(max_sum_window([1, 2, 3], 0))            # None
print(max_sum_window([1, 2, 3], 4))            # None
print(max_sum_window([], 1))                   # None
```

### Edge Cases
- `k` is 1.
- `k` equals the length of the input.
- `k` is 0 or negative.
- `k` is greater than the input length.
- The input list is empty.
- The input contains negative numbers.

For invalid values of `k`, the function returns `None`.

### Time and Space Complexity
- Time Complexity: O(n).
- Auxiliary Space Complexity: O(1), excluding the input.

---

## 3. Debugging Challenge

### Issue
In the original code, `else` is inside the loop. Therefore, `"Not found"` is printed for every number that does not match the target. This produces repeated failure messages.

### Corrected Code

```python
numbers = [4, 8, 12]
target = 7

for number in numbers:
    if number == target:
        print("Found")
        break
else:
    print("Not found")
```

### Output

```text
Not found
```

### Explanation
The `for/else` structure executes the `else` block only when the loop finishes without encountering a `break`. If the target is found, the loop stops and prints `"Found"`. Otherwise, it prints `"Not found"` exactly once after checking all the numbers.

---

## 4. Data-Structure Comparison

| Feature | List | Set | Dictionary |
|---|---|---|---|
| Order | Preserves sequence order | Do not rely on it to preserve the original input order | Preserves insertion order of keys |
| Duplicates | Allows duplicate elements | Stores unique elements | Keys must be unique; values may repeat |
| Membership | O(n) search in a typical unsorted list | O(1) average | O(1) average for key lookup |
| Common use | Storing ordered items | Checking duplicates and membership | Storing key-value pairs and counting frequencies |

### Realistic Backend Examples

**List:** A backend API can use a list to store ordered items returned in a response.

**Set:** A registration service can use a set to detect duplicate registration IDs efficiently.

**Dictionary:** A backend application can use a dictionary to count product occurrences or store item names and their quantities.

---

## 5. What I Learned

- I learned how to remove duplicates while preserving the original order.
- I understood how sets improve membership checks compared with lists.
- I learned how dictionaries can count the frequency of elements using `dict.get()`.
- I understood how the two-pointer technique can reduce repeated comparisons.
- I learned how the sliding-window technique calculates the maximum sum of a fixed-size contiguous window efficiently.
- I understood the difference between `list.sort()` and `sorted()`.
- I learned how to use a `for/else` loop to display a failure message only after the complete search.
- I learned to test edge cases and state time and space complexity after writing code.

---

## 6. What I Found Difficult

- Understanding how the `seen` set and `result` list work together to remove duplicates while preserving order.
- Understanding how to update the window sum without recalculating the complete sum for every window.
- Understanding why the `else` block in the original debugging code printed `"Not found"` multiple times.
- Identifying edge cases such as empty input, duplicate values, and invalid window sizes.
- Understanding how to explain time and auxiliary space complexity.

### What I Would Improve After Feedback

I would practise more coding problems using lists, sets, dictionaries, two pointers, and sliding windows. I would also improve my ability to dry-run code, test boundary cases, and explain my approach and complexity clearly during interviews.
