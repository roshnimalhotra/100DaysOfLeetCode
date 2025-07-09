# Day 03 - Two Sum II (Input Array is Sorted)

**LeetCode #167**  
**Difficulty:** Medium  
**Pattern:** Two Pointers

---

## 🧩 Problem

Given a 1-indexed **sorted** array of integers `numbers`, find two numbers such that they add up to the `target`.

- Return the indices (1-indexed) of those two numbers.
- Use only constant extra space.
- Assume there is **exactly one solution**.

---

## ✨ Example

**Input:**  
numbers = [2, 7, 11, 15], target = 9  
**Output:** [1, 2]  
**Explanation:** 2 + 7 = 9 → return [1, 2]

---

## 🧠 Intuition (Two Pointers)

- Start with `left = 0`, `right = n - 1`.
- Move the pointers inward:
  - If the sum is too small → move `left` forward.
  - If the sum is too big → move `right` backward.
  - If the sum is perfect → return `[left + 1, right + 1]`.

This works **because the array is sorted**.

---

## ✅ Code

```python
left = 0
right = len(numbers) - 1

while left < right:
    total = numbers[left] + numbers[right]
    
    if total == target:
        return [left + 1, right + 1]
    elif total < target:
        left += 1
    else:
        right -= 1
