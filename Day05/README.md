# Day 05: Container With Most Water

🔢 LeetCode Problem [#11](https://leetcode.com/problems/container-with-most-water/)  
🧠 Pattern: Two Pointers  
📈 Difficulty: Medium

---

## 📘 Problem

Given an integer array `height` of length `n`, there are `n` vertical lines drawn such that the two endpoints of the i-th line are at `(i, 0)` and `(i, height[i])`.

Find **two lines** that, together with the x-axis, form a container that holds the **most water**.

Return the **maximum amount of water** a container can store.

---

## 🧪 Examples
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The container formed between index 1 and 8 holds the most water.

---

## 🔍 Approach

- Use **Two Pointers**: one at the start, one at the end.
- Calculate area = width × height
- Move the **shorter line inward**, since height limits capacity.
- Track the **maximum area** throughout.

---

## 🧠 Intuition

We want to:
- Maximize width → start from farthest ends
- Maximize height → keep moving the shorter wall to find taller options

---

## ✅ Code (Python)

```python
from typing import List

class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0
        right = len(height) - 1
        max_area = 0

        while left < right:
            width = right - left
            h = min(height[left], height[right])
            area = width * h
            max_area = max(max_area, area)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_area

