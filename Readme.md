# LeetCode Solutions

This repository contains all my solutions to Leetcode algorithm questions. The problems mostly consist of real interview questions that are asked by many big companies.

Note : All my Solutions are done in Python Programming Language.

Please add a Star if you like it.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## Problems
[TWO SUM](https://leetcode.com/problems/two-sum/)

<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def twoSum(self, nums:List[int], target:int)->List[int]:
    #### Need a look up / buffer to store the index of elements seen so far...
    buffer = dict()
    for i in range(len(nums)):
      if target - nums[i] in buffer.keys():
        return [ buffer[target-nums[i]] , i]
      else :
        buffer[nums[i]] = i
 ```
</p>
</details>

[ADD TWO NUMBERS](https://leetcode.com/problems/add-two-numbers/)

<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
 
class Solution:
  def addTwoNumbers(self, l1:ListNode, l2:ListNode)->ListNode:
    ### Need a carry
    carry = 0
    ans = curr = ListNode()
    while(l1 or l2 or carry):
      temp = 0
      if l1:
        temp += l1.val
        l1=l1.next
      if l2:
        temp += l2.val
        l2=l2.next
      if carry :
        temp+=1
        carry = 0
  
      if temp>9:
        carry=1
        temp=temp%10
      curr.next=ListNode(temp)
      curr=curr.next
    
    return ans.next
 ```
</p>
</details>

## License
[MIT](https://choosealicense.com/licenses/mit/)
