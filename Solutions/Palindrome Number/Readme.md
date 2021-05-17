# Problem
## [Palindrome Number](https://bit.ly/3w91j3d)
Given an integer x; Return true if x is a palindrome else return false.

```python
class Solution:
    def isPalindrome(self, x:int)->bool:
        if x<0:
            return 0
        x = str(x)
        if x == x[::-1]:
            return 1
        return 0
```