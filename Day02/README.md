# Day 02 – Valid Palindrome (#125)

🧠 **Pattern:** Two Pointers  
🎯 **Level:** Easy  
📚 **Topics:** Strings, Pointers, Alphanumeric Filtering

---

## 💬 Problem Statement

A phrase is a palindrome if, after converting all uppercase letters into lowercase and removing all non-alphanumeric characters, it reads the same forward and backward.

Return `True` if the string is a palindrome. Otherwise, return `False`.

---

## 📥 Examples

**Input:** `"A man, a plan, a canal: Panama"`  
**Output:** `True`  
🧠 After cleanup → `"amanaplanacanalpanama"`

---

**Input:** `"race a car"`  
**Output:** `False`  
🧠 After cleanup → `"raceacar"`

---

**Input:** `" "`  
**Output:** `True`  
🧠 Empty strings are valid palindromes.

---

## 📌 Constraints

- `1 <= s.length <= 2 * 10^5`
- `s[i]` is a printable ASCII character

---

## 🧪 Solution: `valid_palindrome.py`

### Approach: Two Pointers

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        left = 0
        right = len(s) - 1

        while left < right:
            while left < right and not s[left].isalnum():
                left += 1

            while left < right and not s[right].isalnum():
                right -= 1

            if s[left].lower() != s[right].lower():
                return False

            left += 1
            right -= 1

        return True
