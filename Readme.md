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

[Move All Negative and Positive Numbers to One Side Of Array](https://www.geeksforgeeks.org/move-negative-numbers-beginning-positive-end-constant-extra-space/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
## Using Partition algo of Quick Sort
def sort(arr):
  pivot_value = 0
  i = -1; j = 0
  while(j < len(arr)):
    if (arr[j] < 0):
      i += 1
      arr[i] , arr[j] = arr[j], arr[i]
      j+=1
    else :
      j+=1
  return arr

if __name__=="__main__":
  ls = [-1, 2, -3, 4, 5, 6, -7, 8, 9]
  print(sort(ls))
 ```
</p>
</details>

[Union and Intersection of Two Sorted arrays](https://www.geeksforgeeks.org/union-and-intersection-of-two-sorted-arrays-2/)
[Intersection of Two Arrays - LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
###### Sorted Arrays   => Approach is different for unsorted Arrays
def union(arr1, arr2):
  ### Using hash map to get union of two arrays
  ''' This approach can also be used with unsorted arrays '''
  map = dict()
  for i in arr1:
    if i in map.keys():
      map[i] += 1
    else :
      map[i] = 1
  for j in arr2:
    if j in map.keys():
      map[j]+=1
    else :
      map[j]=1
  return list(map.keys())

####### Intersection Implementation
def intersection(arr1, arr2):
  ### Using set data structures
  return list(set(arr1) & set(arr2)) ## Gives us the intersection

### Sets can also be used of Union of the two arrays
#### Just keep on adding to the set and return the set in the end.

if __name__ == "__main__":
  arr1 = [1, 2, 2, 2, 3]
  arr2 = [2, 3, 4, 5]
  print(union(arr1, arr2))
  print(intersection(arr1, arr2))
 ```
</p>
</details>

[Cyclically Rotate An Array By One](https://www.geeksforgeeks.org/c-program-cyclically-rotate-array-one/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
def rotate(arr):
  #### [1,2,3,4,5] = I/p
  #### [5,1,2,3,4] = O/p
  temp = list()
  temp.append(arr[-1])
  temp.extend(arr[0:-1])
  return temp   ### Requires O(N) => Auxillary Space

def rotate2(arr):
  x = arr[-1]
  for i in range(len(arr) - 1, 0 , -1):
    arr[i] = arr[i-1]
  arr[0] = x
  return arr    ### O(1) => Auxillary Space
if __name__ == "__main__":
  ls=[1, 2, 3, 4, 5]
  print(rotate(ls))
 ```
</p>
</details>

[Maximum Sub Array](https://leetcode.com/problems/maximum-subarray/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

Subarray = Contigous segment of an array

```python
#### Kadane's Algorithm Approach
def kd(nums):
  if len(nums)==1:
    return nums[0]
  maxSum = -10000000000 ; sm = 0
  for i in nums:
    sm += i
    maxSum = max(maxSum, sm)
    if sm <0:
      sm=0
  return maxSum   ### O(N) time and O(1) => Space

if __name__ == "__main__":
  ls = [-2,1,-3,4,-1,2,1,-5,4]
  print(kd(ls))
 ```
 ###### Dynamic Programming Approach ===> Prefer KADANE's ALGO Than OTHERS.!!!
```python
def maxSubarray(nums):
  max_so_fafr = nums[0]
  curr_max=nums[0]
  for i in range(1, len(nums)):
    curr_max = max(nums[i], curr_max + nums[i])
    max_so_far = max(curr_max, max_so_far)
  return max_so_far
```
</p>
</details>

[Minimize The Maximum Difference B/W Heights](https://www.geeksforgeeks.org/minimize-the-maximum-difference-between-the-heights/)

[Smallest Range 2 - LeetCode](https://leetcode.com/problems/smallest-range-ii/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

###### BruteForce O(2^N)

```python
### Sort the array
### Find the difference b/w smallest and biggest
### Report the minimum difference
def minDifferenceHeight(arr, k):
  arr = arr.sort() ## Sort
  ### Initial difference possible
  ans = arr[-1] - arr[0]
  big = small = 0
  for i in range(1, len(arr)):
    ## arr[0] + k => Increase height of smallest tower
    small = min(arr[0] + k, arr[i]-k) ### arr[i+1] - kbecause it is not the smallest tower
    ## arr[-1]-k => Decreased height of Largest tower
    big = max(arr[i-1]+k, arr[-1]-k) ### arr[i] + k because it is not the largest tower.
    ans = min(ans, big-small)
  return ans ### O(N) Solution
 ```
</p>
</details>

[Find The Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary
This problem is specified for only 1 duplicate no. in the array of size <b>n+1</b>.

So, there can only we values in the array from 0 to 1.
```python
#### Simple Method => O(N) time and O(N) space.
#### Use hash map and return the number / index with occurence > 1
### or use counter array as in count sort
'''
This time we will be going with O(N) time and O(1) space.
'''
### we will be using the original array itself as our frequency array.
def findDuplicate(nums):
  n = len(nums)
  for i in range(n):
    nums[nums[i]%n] += n
  ### Giving the count of numbers with frequency > 1
  ### This approach is also useful with multiple duplicate sin the array
  ls = list()## Will store the duplicates.
  for i in range(n):
    if nums[i]//n >1:
      ls.append(i) ## i is the index of that repeat no.
  return ls
 ```
 ###### More better approach is to use the Cycle detection algorithm
 ```python
 ### Can only be used when there is just one duplicate...
 def findDuplicate(nums):
   slow ,fast = nums[0], nums[nums[0]]
   while(slow != fast):
     slow = nums[slow]
     fast = nums[nums[fast]]
   slow = 0
   while(slow!=fast):
     slow = nums[slow]
     fast = nums[fast]
   return slow

 ```
</p>
</details>

[Merge Intervals](https://leetcode.com/problems/merge-intervals/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
### Sort the intervals
### O(NLogN) time + O(N)space
from Collections import deque
def merge(nums):
  if len(nums)<2:
    return nums
  nums.sort()
  stack = deque()
  stack.append(nums[0])

  for i in range(1, len(nums)):
    if nums[i][0] <= stack[-1][1]:
      temp = stack.pop()

      if nums[i][1] > temp[1]:
          stack.append([temp[0],nums[i][1]])
      else :
          stack.append(temp)

    else:
      stack.append(nums[i])
  return stack
 ```
 ###### Another approach is to just to iterate over the sorted the array instead of using a Stack.

 ```python
 ### O(NLogN) = Time + O(1) = Space
 def merge(nums):
    if len(nums) < 2:
      return nums
    nums.sort()
    i = 1
    while(i < len(nums)):
      if nums[i][0] <= nums[i-1][1]:
        if nums[i-1][1] < nums[i][1]:
          nums[i-1][1] = nums[i][1]
        nums.remove(nums[i])
      else:
        i+=1
    return nums
 ```
</p>
</details>

[Next Permutation](https://leetcode.com/problems/next-permutation/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

###### Brute Force approach takes O(N!) time + O(N) Space
```python
### This solution Takes O(N) time + O(1) space
def nextPermutation(nums):
  i = len(nums) - 1; idx = -1
  while(i>0):
    if nums[i] < nums[i-1]:
      idx = i
      break
    i -= 1
  if idx < 0:
    nums.reverse()
  j = prev = idx;
  while(j < len(nums)):
    if nums[j] > nums[idx - 1]:
      if nums[i] <= nums[prev]]:
        prev = j
    j+=1
  ### Swap for next lexigographically bigger permuation
  nums[prev], nums[idx-1] = nums[idx-1], nums[prev]
  nums[:] = nums[:idx] + nums[-1:idx -1 : -1]
 ```
</p>
</details>

[Sort An Array](https://leetcode.com/problems/sort-an-array/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

###### Merge Sort Implementation
O(NLogN) = Time (Average ,Best, Worst)
O(N) = Space

```python
#### Merge Sort Implementation

def merge(arr, left, mid, right):
  temp = list()
  i = left; j= mid + 1
  while(i <= mid and j <= right):
    if arr[i] <= arr[j]:
      temp.append(arr[i])
      i+=1
    else:
      temp.append(arr[j])
      j+=1
  if i > mid : ## Unequal sized arrays
    temp.extend(arr[j :right + 1])
  else:
    temp.extend(arr[i: mid + 1])
  
  arr[left : right + 1] = temp[:]

def mergesort(arr, left, right):
  if left < right:
    mid = left + (right - left)//2
    mergesort(arr, left, mid)
    mergesort(arr, mid+1, right)
    merge(arr, left, mid, right)
  return arr

 ```
</p>
</details>

[Count Number Of Inversions in an Array](https://www.geeksforgeeks.org/counting-inversions/)
<details><summary>CODE</summary>
<p>
#### @Author : Akash Choudhary

```python
### Using Merge Sort
def merge(arr, left, mid, right):
  temp = list()
  i = left; j= mid + 1
  inv = 0
  while(i <= mid and j <= right):
    if arr[i] <= arr[j]:
      temp.append(arr[i])
      i+=1
    else:
      temp.append(arr[j])
      inv += mid - i + 1
      j+=1
  if i > mid : ## Unequal sized arrays
    temp.extend(arr[j :right + 1])
  else:
    temp.extend(arr[i: mid + 1])
  
  arr[left : right + 1] = temp[:]
  return inv

def mergesort(arr, left, right):
  inv = 0
  if left < right:
    mid = left + (right - left)//2
    inv += mergesort(arr, left, mid)
    inv += mergesort(arr, mid+1, right)
    inv += merge(arr, left, mid, right)
  return inv

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
