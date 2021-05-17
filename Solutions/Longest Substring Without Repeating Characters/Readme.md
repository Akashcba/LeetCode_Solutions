# Problem
## [Longest Substring Without Repeating Characters](https://bit.ly/3wcUA8e)
Given a string s, find the length of the longest substring without reeating characters.
## Approach
1. Start from the first index of the string.
2. Store the index of the characters seen in a dictionary.
3. If the repeating character is present in  the buffer then go to the index of the last repeating character seen.
4. Return the maximum length of the substring.
```python
class Solution:
    def lengthOfLongestSubstring(self, s :str)->int:
        mx, start, buffer =0,0, { }
        for i in range(len(s)):
            if s[i] in buffer and start <=buffer[s[i]]:
                start = buffer[s[i]] + 1
            mx = max(mx, i-start +1)
            buffer[s[i]] = i
        return mx
```