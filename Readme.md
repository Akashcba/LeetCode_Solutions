# DSA Solutions

This repository contains all my solutions to DSA algorithm questions. The problems mostly consist of real interview questions that are asked by many big companies.

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
###### Naive approach based on O(N) provided can be improved using heaps and binary search.
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

[Zig Zag Conversion](https://leetcode.com/problems/zigzag-conversion/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def convert(self, s:str, numRows:int)->str:
    if numRows==1 or numRows >= len(s): ## Edge cases
      return s
    row =0; direction = -1; result = ['']*numRows ## List with empty strings for each row
    for ch in s:
      result[row] += ch ## Add respective character to their rows
      if row==0 or row==numRows-1 : direction *= -1 ## For going forward and backward along the string
      row += direction
    
    return ''.join(result) ## Return the joined string
 ```
</p>
</details>

[Reverse An Integer](https://leetcode.com/problems/reverse-integer/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

Naive Approach Shall not be used at all

```python
class Solution:
  def reverse(self, x:int)->int:
    flag = 1
    if x<0:
      flag = -1
      x = x*flag
    x = str(x)
    x = int(x[::-1])
    if (x > (1<<31) - 1): ## 1<<31 gives us 2**31 but in a more optimised manner
      return 0 ## Integer overflow
    return x *flag
 ```
</p>
</details>

[Palindrome Number](https://leetcode.com/problems/palindrome-number/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
### Once again a Very Naive and Not to be used approach
class Solution:
  def isPalindrome(self, x:int)->bool:
    if x<0:
      return False
    x = str(x)
    if x == x[::-1]:
      return True
    return False
 ```
</p>
</details>

[Roman To Integer](https://leetcode.com/problems/roman-to-integer/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        value = {
            'M': 1000,
            'D':500,
            'C':100,
            'L':50,
            'X':10,
            'V':5,
            'I':1
        }
        ans = 0
        ### If value of current character is less than Next char then subtract it else add its value
        for i in range(len(s) - 1):
            if value[s[i]] < value[s[i+1]]:
                ans -= value[s[i]]
            else:
                ans += value[s[i]]
        ans += value[s[-1]]
        return ans
 ```
</p>
</details>

[String To Integer Atoi](https://leetcode.com/problems/string-to-integer-atoi/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def myAtoi(self, s:str)->int:
    ## Remove any whitespaces on left
    s = s.lstrip()
    ## Check for + and -
    flag = 1
    try: ## to avoid conflict with '' empty string
      if s[0] == '-':
        flag = -1
        s = s[1:]
      elif s[0] == '+':
        s = s[1:]
    except :
      pass
    digits = '0123456789' ## All possible digits
    ans=0
    for i in s:
      if i in digits: ## It is a number
        ans = ans*10 + int(i)
      else:
        break
    if ans > (1<<31) - 1:
      ### Integer Overflow
      if flag== 1:
        return (1<<31)-1
      else :
        return (1<<31)*-1
    return ans*flag
 ```
</p>
</details>


[Reverse A String](https://leetcode.com/problems/reverse-string/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
class Solution:
  def reverseString(self, s:List[str])->None:
    i = 0; j = len(s) - 1
    while(i<j):
      s[i] , s[j] = s[j], s[i]
      i+=1; j-=1
 ```
</p>
</details>

[MAX and MIN Element in array](https://www.geeksforgeeks.org/maximum-and-minimum-in-an-array/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
### Noobie approach O(n)
ls = [1,2,3,4,6,99,-2002, 29992]
mx = mn = ls[0]
for i in ls:
  if i > mx:
    mx = i
  elif i < mn:    ## 2(n-2) + 1 => comparisons
    mn = i
return mn, mx
 ```

########### Using Two comparisons at the same time...
```python
ls = [1,2,3,4,6,99,-2002, 29992]
if len(ls)&1:
  ## ODD Length Min array size possible = 1
  mx = mn = ls[0]
  i = 1 ### 3*(n-1)/ 2 - 1 => comparisons
else: ## Even array min size possible is 2
  if ls[0] > ls[1]:
    mx = ls[0]; mn = ls[1]
  else :
    mx = ls[1]; mn=ls[0]
  i = 2 ## 3*(n-1)/2 => Comparisons
while( i < len(ls)):
  if ls[i] > ls[i+1]:
    if ls[i] > mx:
      mx = i
    if ls[i+1] < mn:
      mn = ls[i+1]
  else :
    if ls[i+1] > mx:
      mx = ls[i+1]
    if ls[i] < mn:
      mn = ls[i]
  i += 2
print(mn, mx)
```
###### The Above approach is more better as it takes less compasrisons.
</p>
</details>

[Sort an array of 0s, 1s and 2s](https://www.geeksforgeeks.org/sort-an-array-of-0s-1s-and-2s/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
### Naive approach
def sort(arr):
  c0 = 0; c1=0; c2=0;
  for i in arr:
    if i==0:
      c0+=1
    elif i==1:
      c1+=1
    else:
      c2+=1
  ls=list()
  while(c0):
    ls.append(0)
    c0-=1
  while(c1):
    ls.append(1)
    c1-=1
  while(c2):
    ls.append(2)
    c2-=1
  return ls

if __name__=="__main__":
  ls = [1,0,0,0,1,2,1,2,2,1,1,0]
  print(sort(ls))
 ```
 ###### Better approach is to use additional pointers that can define the space within the given array

 ```python
def sort(arr):   ## Better approach
  high = len(arr) - 1
  lo = 0
  mid = 0
  while(mid <= high):
    if arr[mid] == 0:
      arr[lo], arr[mid] = arr[mid], arr[lo]
      lo +=1
      mid += 1
    elif arr[mid] == 1:
      mid+=1
    else :
      arr[high], arr[mid] = arr[mid], arr[high]
      high-=1
      mid +=1
  return arr
if __name__=="__main__":
  ls = [1,0,0,0,1,2,1,2,2,1,1,0]
  print(sort(ls))
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
