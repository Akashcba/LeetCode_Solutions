# Problem
## [String to Integer](https://bit.ly/3uTTcHq)
Implement the atoi function.

```python
class Solution:
    def myAtoi(self, s:str)->int:
        s = s.lstrip()
        ans = 0; i = 0; flag = 1; digits = "0123456789"
        if len(s)<1:
            return 0
        if s[0] == "-":
            flag = -1
            i = 1
        if s[0] == "+":
            i = 1
        
        for j in range(i, len(s)):
            if s[j] in digits:
                ans = ans*10 + int(s[j])
            else :
                break
        
        if flag == 1:
            if ans > (1<<31)-1:
                return (1<<31) - 1
            return ans
        if flag == -1:
            if ans > (1<<31) - 1:
                return -(1<<31)
            return -ans
```