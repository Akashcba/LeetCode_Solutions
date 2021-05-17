# Problem
## [TWO SUMS](https://bit.ly/3fohKSm)
Given an array of Integers and a target. We need to return the indices of the two numbers such that they add up to the target.
## Approach
1. Use a Dictionary / Hashmap where you can store the indices of numbers seen so far.
2. If target - current number is in the dictionary, return the indices.
3. Else add the index of the current number of the array.
```python
class Solution:
    def twoSum(self, nums: List[int], target: int)-> List[int]:
        ## Hashmap / Dictionary
        buffer = { }
        for i in range(len(nums)):
            if (target - nums[i]) in buffer:
                return [buffer[taregt - nums[i]], i]
            buffer[nums[i]] = i
        return 'Not Found'
```