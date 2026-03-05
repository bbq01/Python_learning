# LeetCode 2 - Add Two Numbers

## Problem Description
Given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example:
- Input: l1 = [2,4,3], l2 = [5,6,4]
- Output: [7,0,8]
- Explanation: 342 + 465 = 807.

## Solution Approach
1. **Initialization**: Create a dummy node to build the resulting linked list and carry to handle sums greater than 9.
2. **Iteration**: Traverse through both lists until both are exhausted. If one list is shorter, continue with the longer list.
3. **Sum Calculation**: For each node, calculate the sum of the current digits and the carry. Update the carry for the next iteration if needed.
4. **Appending to Result**: Create a new node with the sum modulo 10 and move to the next node.
5. **Final Carry**: If there's still a carry after the loop, add a new node with carry as its value.

## Code Implementation
```python
class ListNode:
    def __init__(self, value=0, next=None):
        self.value = value
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode(0)
        current = dummy
        carry = 0

        while l1 or l2 or carry:
            total = carry
            if l1:
                total += l1.value
                l1 = l1.next
            if l2:
                total += l2.value
                l2 = l2.next

            carry = total // 10
            current.next = ListNode(total % 10)
            current = current.next

        return dummy.next
```

## Key Points
- Understanding of linked list traversal is crucial.
- Properly handling the carry is essential for correct results.
- You may need to consider edge cases like different lengths of input lists.

## Complexity Analysis
- **Time Complexity**: O(max(N, M)), where N is the length of list l1 and M is the length of list l2. We need to traverse both lists once.
- **Space Complexity**: O(max(N, M)), for the result linked list storage.

## Common Mistakes
- Forgetting to handle carry after the last addition.
- Mismanaging list nodes when one list is shorter than the other.
- Not returning the correct linked list head (using the dummy node).

## Related Problems
- LeetCode 445: Add Two Numbers II (where the digits are stored in forward order).
- LeetCode 61: Rotate List (linked list manipulation).
- LeetCode 21: Merge Two Sorted Lists (helpful for understanding linked list operations).