#  Day 01 - LeetCode #344: Reverse String

🔁 **Pattern:** Two Pointers  
📈 **Difficulty:** Easy  
🧠 **Concepts Used:** In-place swapping, loop, pointers  
🕐 **Time Spent:** ~15 mins

---

### 💬 Problem Statement:
> Write a function that reverses a string. The input string is given as an array of characters `s`.  
> Modify the input array in-place with O(1) extra memory.

---

### ✅ Constraints:
- 1 <= s.length <= 10⁵  
- s[i] is a printable ASCII character.

---

### 💡 Approach:
- Use two pointers from both ends.
- Swap until `left < right`.

---

### 🧪 Code:
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        left = 0
        right = len(s) - 1
        while left < right:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1
