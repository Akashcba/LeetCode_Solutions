# Problem
## [Add Two Numbers](https://bit.ly/3eOQiya)
Given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contaiin a single digit.
Add the two numbers and return the sum as a Linked List.

```python
# Definiton of singly-linked list:
# class ListNode:
#    def __init__(self,val=0, next=None):
#        self.val=val
#        self.next=next
class Solution:
    def addTwoNumbers(sel, l1:ListNode, l2:ListNode)->ListNode:
        ans = temp = ListNode(0,None)
        carry = 0
        while(l1 or l2 or carry):
            sum = 0
            if l1:
                sum+=l1.val
                l1 =l1.next
            if l2:
                sum+=l2.val
                l2 =l2.next
            if carry:
                sum += carry
                carry = 0
            if sum>9:
                carry = 1
                sum = sum%10
            temp.next=ListNode(sum, None)
            temp =temp.next
        return ans.next
```
### Code in Few Lines
```python
class Solution:
    def addTwoNumbers(self, l1:ListNode, l2:ListNode)-> ListNode:
        carry = 0
        ans = temp = ListNode(0,None)
        while(l1 or l2 or carry):
            carry, sm = divmod(sum(l and l.val or 0 for l in (l1,l2)) + carry, 10)
            temp.next = temp = ListNode(sm)
            l1 = l1 and l1.next
            l2 = l2 and l2.next
        return ans.next
```