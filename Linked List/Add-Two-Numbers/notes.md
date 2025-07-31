# 📝 Notes: Add Two Numbers (Medium)

## 🔍 Problem Summary

You are given two **non-empty linked lists**, where each node contains a **single digit** of a number.
The digits are stored in **reverse order**, and each of their nodes represents a digit in the number.

Your task is to **add the two numbers** and return the result as a new linked list (also in reverse order).

- No leading zeros (except the number 0 itself)
- Each list can have different lengths

---

## 🧠 Approach

We simulate **column-wise addition** (like how we add numbers on paper), taking care of:

- The current digits from both lists
- The **carry** from the previous addition

We:

1. Traverse both lists simultaneously
2. Add corresponding digits and the carry
3. Create a new node with the result digit
4. Move to the next digits in both lists
5. Continue until both lists and the carry are processed

We use a **dummy node** to simplify list construction.

---

## ✅ Python Code (Efficient: O(max(M, N)) Time)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        cur = dummy
        carry = 0 

        while l1 or l2 or carry:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0

            val = v1 + v2 + carry
            carry = val // 10
            val = val % 10

            cur.next = ListNode(val)
            cur = cur.next

            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return dummy.next
```

---

## 🧮 Time & Space Complexity

- **Time Complexity:** O(max(M, N))Traverse both lists once
- **Space Complexity:** O(max(M, N))
  New linked list size is at most max length of inputs + 1 (if carry remains)

---

## 📦 Example Walkthrough

### Example 1:

**Input:**
`l1 = [2,4,3]`, `l2 = [5,6,4]`
**Output:**
`[7,0,8]`
**Explanation:**
342 + 465 = 807 → Reversed: [7,0,8]

---

### Example 2:

**Input:**
`l1 = [0]`, `l2 = [0]`
**Output:**
`[0]`

---

### Example 3:

**Input:**
`l1 = [9,9,9,9,9,9,9]`, `l2 = [9,9,9,9]`
**Output:**
`[8,9,9,9,0,0,0,1]`

---

## 🏷️ Tags

`Linked List`, `Math`, `Recursion`

---

## 🏢 Company Tags

Apple, Google