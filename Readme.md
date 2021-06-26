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
        return [buffer[target-nums[i]], i]
      else:
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
    curr = ans = ListNode()
    while(l1 or l2 or carry):
      temp=0
      if l1:
        temp+=l1.val
        l1=l1.next
      if l2:
        temp+=l2.val
        l2=l2.next
      if carry:
        temp +=1
        carry = 0
      if temp>9:
        temp=temp%10
        carry = 1
      curr.next = ListNode(temp)
      curr=curr.next
    return ans.next
 ```
</p>
</details>

[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def lengthOfLongestSubstring(self, s:str)->int:
    mx = 0 ## Max length seen so far
    start = 0 ## Starting point of current parsing string
    buffer = dict() ## Stores the index of the elements seen so far
    
    for i in range(len(s)):
      if s[i] in buffer and start <= buffer[s[i]]:   
        ## if s[i] is in buffer that means we have seen it before 
        #so we need to start again and consider the next strings
        start = buffer[s[i]] + 1
      else :
        mx = max(mx, i-start+1)
       
      ## Need to update the index of the elements
      buffer[s[i]] = i
    
    return mx
 ```
</p>
</details>

[Median Of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
### Naive approach based on O(N) provided can be improved using heaps and binary search.
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def findMedianSortedArrays(self, nums1:List[int], nums2:List[int])->float:
    ans = list()
    i = 0; j=0; flag=-1
    curr = 0; median = (len(nums1)+len(nums2))//2
    if(len(nums1) + len(nums2)) &1:
      flag = 0 ## Odd
    else:
      flag=1 ## Even
    
    while(i<len(nums1) and j<len(nums2) and curr<= median):
      if nums1[i] <= nums2[j]:
        ans.append(nums1[i])
        i+=1
      else :
        ans.append(nums2[j])
        j+=1
      curr +=1
    ### Lets check for leftovers from nusm1 and nums2:
    if(curr<=median and i<len(nums1)):
      while(curr<=median):
        ans.append(nums1[i])
        i+=1
        curr+=1
    if(curr<=median and j<len(nums2)):
      while(curr<=median):
        ans.append(nums2[j])
        j+=1
        curr+=1
    
    ## lets print the results now
    if flag: ## Even
    return (ans[-1] + ans[-2])/2
    return ans[-1] ## Odd case
 ```
</p>
</details>

[]()
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python

 ```
</p>
</details>

[]()
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python

 ```
</p>
</details>

## License
[MIT](https://choosealicense.com/licenses/mit/)
