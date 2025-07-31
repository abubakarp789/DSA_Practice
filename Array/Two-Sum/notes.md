# 📝 Notes: Two Sum (Easy)

## 🔍 Problem Summary

Given an array of integers `nums` and an integer `target`, return **indices of the two numbers** such that they **add up to target**.

- You **cannot** use the same element twice.
- There is **exactly one valid solution**.

---

## 🧠 Approach

We use a **hash table (dictionary)** to store numbers we’ve already seen along with their indices.

For each number in the array:

1. Calculate `diff = target - current number`.
2. If `diff` is already in the dictionary, return the indices of `diff` and the current number.
3. Otherwise, store the current number and its index in the dictionary.

---

## ✅ Python Code (Efficient: O(n) Time)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap = {}  # Stores number -> index

        for i, n in enumerate(nums):
            diff = target - n
            if diff in prevMap:
                return [prevMap[diff], i]
            prevMap[n] = i
```

---

## 🧮 Time & Space Complexity

* **Time Complexity:** O(n) – Single pass through the array
* **Space Complexity:** O(n) – Space for the dictionary

---

## 📦 Example Walkthrough

**Input:**

```python
nums = [2, 7, 11, 15]
target = 9
```

* i = 0 → n = 2 → diff = 7 → Not in map → Add 2:0
* i = 1 → n = 7 → diff = 2 → 2 is in map → ✅ Return [0, 1]

---

## 🏷️ Tags

`Array`, `Hash Table`

---

## 🏢 Company Tags

Google, Amazon, Microsoft, Netflix