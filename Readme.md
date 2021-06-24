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

## License
[MIT](https://choosealicense.com/licenses/mit/)
