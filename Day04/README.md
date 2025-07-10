# Day 04 – 3Sum

**LeetCode #15**  
**Difficulty:** Medium  
**Pattern:** Two Pointers (Triple Nested)

---

## 🔍 Problem

Find all unique triplets in the array which give the sum of zero.

---

## 💡 Intuition

- Sort the array.
- Fix one number (`nums[i]`), then apply Two Pointers on the rest.
- Skip duplicate values for uniqueness.

---

## ✨ Example

**Input:** [-1, 0, 1, 2, -1, -4]  
**Sorted:** [-4, -1, -1, 0, 1, 2]  
**Output:** [[-1, -1, 2], [-1, 0, 1]]

---

## ✅ Code

```python
nums.sort()

for i in range(len(nums) - 2):
    if i > 0 and nums[i] == nums[i - 1]:
        continue

    left, right = i + 1, len(nums) - 1

    while left < right:
        total = nums[i] + nums[left] + nums[right]

        if total == 0:
            res.append([nums[i], nums[left], nums[right]])
            # skip duplicates
            while left < right and nums[left] == nums[left + 1]:
                left += 1
            while left < right and nums[right] == nums[right - 1]:
                right -= 1
            left += 1
            right -= 1
        elif total < 0:
            left += 1
        else:
            right -= 1
