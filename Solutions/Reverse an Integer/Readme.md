# Problem
## [Reverse an Integer](https://bit.ly/3hvLeAs)
Given a signed 32-bit integer x, retturn the reverse of x.
Make sure that x is in the 32-bit range [-2^31, 2^31 - 1] .
## Approach
1. Check if x is negative or not.
2. Store the sign of x in flag
3. Convert x into a string and reverse it.
4. Check if x falls in the range.
5. Return x * sign
```python
class Solution:
    def reverse(self, x:int)->int:
        flag = 1
        if x<0:
            flag = -1
            x = -x
        x = int(str(x)[::-1])
        if (abs(x) > ((1<<31) - 1)):
            return 0
        return x*flag
```